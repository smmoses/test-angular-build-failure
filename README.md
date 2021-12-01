# test-angular-build-failure
A new angular project that is failing builds when running in Azure DevOps on-prem pipelines. This project contains the simplest implementation of an Angular project. It is essentially just an `ng new`.

# Issue
I have several angular applications running Angular 12 that fail in our build pipeline by just hanging on the `npm run build` command.
When it gets to this command, the build gets stuck and eventually times out.
This build is being run in Azure DevOps 2020 on-prem, and it is on the latest release.

I have included the build definition file (azure-pipeline.yml).

# What I have tried to fix it
- Using command line and powershell to run the `npm run build` command instead of the npm task
- Adding environment variable for NODE_OPTIONS --max_old_space_size=8000 as described here: https://stackoverflow.com/questions/69678725/npm-build-is-hanging-in-azure-dev-ops
- Created a brand new on prem build server with clean install of windows server, Visual Studio and build tools
- Attempted calling `ng build` directly from powershell
- Adding --verbose to `ng build`. No additional logs are created because it freezes up prior to that point.
- Running pipeline in diagnostic mode. None of those logs were helpful to me.

The only thing I have tried that worked is running the build pipeline in Azure DevOps cloud version. I was unable to get the build pipeline to hang there.