---
title: "Powershell isntalled, rund script from a docker container"
date: 2019-07-20
forum: General Help
---

### Post by flemmingss on 2019-07-20
Hi.

So powershell is installed and works from CLI.
I have a server where I rund hass.io, that is a docker pack of Home-Assistant, or something like that. for more info see [https://www.home-assistant.io/hassio/](https://www.home-assistant.io/hassio/)
I am running Ubuntu Server 16, and newest hass.io.
I try to run this from Home-Assistant (ant then technically inside docker), with this string:
[COLOR=#0000ff]*'pwsh -file /usr/share/hassio/homeassistant/powershell_script/output_date.ps1'*[/COLOR]

And this is my powershell_script\output_date.ps1 script file:```
Get-Date | Out-File "/usr/share/hassio/homeassistant/powershell_script/test.txt"
```

It works if I run in in cli, but not if the automation is triggering it.

Is there a way of doing this? (PS: Ubuntu and docker noob)
Ref my original thread: [https://community.home-assistant.io/t/running-custom-command-in-ubuntu-cli-from-automation/126011](https://community.home-assistant.io/t/running-custom-command-in-ubuntu-cli-from-automation/126011)

---

### Post by TheFu on 2019-07-20
If it uses cron, a common mistake is assuming all the same environment variables are available in a cron environment as what is enabled in an interactive shell. That just isn't true.  It is a very, very, common problem for people not familiar with Unix environment variables.  Windows has them too, but they don't tend to be used much outside software development.   To see if this is the issue, print all the environment variables when you run it from the shell and do the same when you run it through the scheduler.  What's different?

I don't know how to do that for powershell, but in all Unix systems, the **env** command will dump all environment variables.

I know nothing about docker, but if it works from a shell, I doubt the problem is inside docker.

---

### Post by dragonfly41 on 2019-07-20
I see that you have been posting this question in home-assistant forum ..
docker is just a container or vm.
I know nothing about hass .. but it occurs to me that this might be a permissions problem

Instead of placing script in /usr/ can you run from home folder?

[P.S.] However after [reading again]("https://community.home-assistant.io/t/command-line-automation-without-command-line-switches/3730/7") I see that you use sudo so perhaps this idea does not fly.

---

