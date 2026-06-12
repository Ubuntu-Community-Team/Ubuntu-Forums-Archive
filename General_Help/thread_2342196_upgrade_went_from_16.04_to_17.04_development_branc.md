---
title: "upgrade went from 16.04 to 17.04 development branch :("
date: 2016-11-04
forum: General Help
---

### Post by alain.roger on 2016-11-04
Hi,

i wanted to upgrade my distro from 16.04 to 16.10, but for unknown reason, ubuntu upgrade to 17.04 version as you can see below:

[FONT=monospace]```
[COLOR=#000000]$ lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:        17.04
Codename:       zesty
```

how to i downgrade to 16.10 without crashing everything ?

thx.

[/FONT]

---

### Post by bearlake on 2016-11-04
Hi, you can't go backwards.

Do you have a full backup before you upgraded? ( Easiest way )

Even having a backup of just your /home directory would be a big help.

---

### Post by RobGoss on 2016-11-04
How did you do your upgrade did you do it from the command line?

---

### Post by alain.roger on 2016-11-05
> **RobGoss said:**
> How did you do your upgrade did you do it from the command line?

in fact i did a mistake typing in command line: sudo do-release-upgrade -d
i should not write -d :(

and now i have this ubuntu "Zesty Zapus (development branch) version installed :(

by the way it works great but there is 1 annoying bug with WIFI that every morning for unknow reason it stop to work and i have to disconnect and connect again to have wifi working.
the other bug is more a compatibility issue with XnViewMP... some libs need to be manually installed to run XnViewMP :(

thx

---

### Post by RobGoss on 2016-11-05
I've never seen this before very strange to me don't know why it's saying **17.04** is this a new installation? you might want to fix this issue first before you attempt to fix other issues. You have to be very carful using the command line it can and will breake a system

Have you thought about just doing a fresh installation if this system is new might be worth a try I'm not sure if you're using a **single **or **dual **boot

I don't know much about **XnViewMP **someone else might be able to help with this issue

---

### Post by alain.roger on 2016-11-05
this laptop had before kubuntu 15.04, next 15.10, 16.04 and i just wanted to upgrade it to 16.10.
I know i could reinstall a fresh install but i would need to reinstall all applications and settings too, which i do not want.

That's why almost 2 years ago i migrated from windows 7 to Kubuntu :) Ubuntu was stable and had no issue during upgrading process.

I would not be happy to do a fresh install of ubuntu...moreover i'm limited regarding free space for backuping my home directory as no tools (even rsync) does not backup everything...i tried with rsync to backup home do NAS but there are always some file with issues.

I'm using single boot system...i'm against the idea to have 2 OS on the same machine.

---

### Post by howefield on 2016-11-05
Seems that you have 2 choices, either run with 17.04 which will have tons of updates and take the high risk of breakage that comes with running the development release or a clean install of your previous OS version. Neither sound attractive but it is where you are :(

---

### Post by RobGoss on 2016-11-05
As far as keeping all your application Ubuntu makes it simple to just reinstall things, when ever I do a re-installation of any Linux OS I just make a list of what's installed then as soon as I complete my new installation I go down the list and install the application I need to complete my system. I don't think I'm really attached to any applications that needs to be installed that's what makes Linux so GREAT they have a simple installation process  

I did come across this application you might be interested in it helps keep some of the settings within your system [http://www.teejeetech.in/2016/04/aptik-v1641.html?m=1](http://www.teejeetech.in/2016/04/aptik-v1641.html?m=1) I have never use it yet but from what I read most people say it a good application

I think you should consider **Howefeild** suggestion running a developer's version will have it's issues and unless you're willing to work them out a fresh installation is the only option

---

### Post by alain.roger on 2016-11-06
I would be happy to test Aptik but when i add the repository it automatically add the Zesty compatibility release whereas Aptik has not. 
I had to force/edit the package details in software & update to make update works.

I just would like to know when v17.04 (zesty) will be released...so in APril 2017, will my complete laptop OS will be updated to this release and stable version or will it continue to install development branch of next 17.10 and so on ?
how to stop it and be back to stable version (17.07, next 17.10, 18.04 etc...) without have the development branch release :(

---

### Post by howefield on 2016-11-06
> **alain.roger said:**
> I just would like to know when v17.04 (zesty) will be released...so in APril 2017,

That's right, it's quite a short development cycle and is released in April 2017..  I have to say that running the development release has been pretty solid for the past few years, with remarkably few issues (on my machines at least) but the increased risk of breakage versus the LTS release is the price you pay for using it, also is good to report bugs and help the process. 

>  will my complete laptop OS will be updated to this release and stable version or will it continue to install development branch of next 17.10 and so on ?

If you keep updating as advised by the system you will end up on the finished release of 17.04.

> how to stop it and be back to stable version (17.07, next 17.10, 18.04 etc...) without have the development branch release :(

Don't destroy it the way you did to 16.04 by using the do-release-upgrade command with the -d switch, simple enough really.

Allow the system to advise of updates/upgrades or periodically use

```
sudo apt update
```
```
sudo apt upgrade
```

That's all you need to do. I'm sure that you already know that you have left behind the 16.04 LTS 5 year support cycle and are now on a 9 month support cycle with the interim releases which means you will have an upgrade to perform every 6-9 months till the next LTS is released and you get to choose again what to use. :)

---

