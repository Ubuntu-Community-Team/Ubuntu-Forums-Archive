---
title: "Decline updates"
date: 2017-05-22
forum: General Help
---

### Post by jwn-2 on 2017-05-22
Ubuntu 14.04 LTS

Every time I reboot I get a notification that there are updates available and do I want to install it. How can I get rid of this without installing the updates? I have set all checks for updates to “Never” in Software & Updates, and I have set Package upgrade behaviour to “Always prefer the installed version” in Synaptic, but the notification keeps coming up. I do not want to install the updates for two reasons: 1) I cannot afford a ridiculous 400Mb download, and 2) I prefer to stick with what I am used to rather than having to relearn how to use the software every time  some developer gets a bee in his bonnet and changes everything.

---

### Post by mastablasta on 2017-05-22
> **jwn-2 said:**
>  1) I cannot afford a ridiculous 400Mb download, and 

makes sense, but if PC is connected online you are open to hacking.

> 
2) I prefer to stick with what I am used to rather than having to relearn how to use the software every time  some developer gets a bee in his bonnet and changes everything.

update is not the same as upgrade. update includes security patches and bug fixes, it doesn't change or upgrades the application to newer version. again, not doing the updates leaves you open to hacking. head over to security section if you still believe it can not happen on the unpatched PC.

selecting to never look for updates should have solved it. however it could be this is something that stayed form before. if you updates and then selected never it should work. it should also work in synapctic if you lock down the packages to certain version. alternatively, you can untick the repositories. because obviously you do not intend to install anyhting. if you did you would need to update first anyway.

when you say you can't afford large updates, are you using mobile internet or what? even those have unlimited plans available. usually. 
in any case i would leave at least security patches on. i think this would still pull in kernels which are the ones that are large. 

anyway choice is udpate and be safe or not update and risk getting hacked. i can tell you i have at least 8 break in attempts per day.

---

### Post by ian-weisser on 2017-05-22
Well, the whole point of an LTS release is precisely that the the software WON'T change.
Updates due to bee-in-bonnet are specifically proscribed from LTS updates.
If you are getting bee-in-bonnet changes, then you have a very different problem that limiting updates seems unlikeley to cure.

If the system is trying to download 400Mb, then you may have a very different --and more serious-- problem than a mere notification. We gently suggest you investigate further.

Here is one answer: Comment out the update sources in /etc/apt/sources.list* . 
Leave the -security source enabled, obviously. Else you unwisely leave your system vulnerable to known, published exploits.

---

### Post by Impavidus on 2017-05-22
1: 400MB downloads are not the norm, but if you never install upgrades, the available upgrades keep accumulating so at some point you'll have 400 MB waiting. It seems you haven't upgraded your software in ages. Something like 100MB/month is more like it, but it depends on what software you've installed and how many kernel updates we get, as those are rather big and unpredictable. If you skip the non-security updates it will be less. If you wish, you can download the updates on a different computer and move them over on a usb drive, if you have access to a different computer with a better network connection. But it's a bit of a hassle.

2: Apart from Firefox and a few other things you only get updates for bugfixes and things like that. And I recommend you keep at least your web browser up-to-date. Your version of libreoffice will not be replaced by the latest release. Most updates are nearly invisible to the average user. The type of upgrade you want to avoid is a release upgrade, from 14.04 to 16.04. That's when the entire user interface can change.

---

### Post by vasa1 on 2017-05-22
@jwn-2, please provide more actual detail :)

BTW, are you aware that you have some responses to your other thread on [bs1770gain]("https://ubuntuforums.org/showthread.php?t=2360056")?

---

### Post by jwn-2 on 2017-05-22
@vasa1, I don't know what more detail I can give you. I was getting tired of the notification that comes up on every reboot, so I unsuccesfully tried to get rid of it. It however seems now from other answers above I should have set those settings right from the beginning. I just wish that there was a way that I can tell the system to ignore all those previous updates.

And yes I have seen the response to the other thread and I am using easymp3gain now.

---

### Post by speartip on 2017-05-22
Could I ask, why you don't want the updates?
An updated system is a secure system.

---

### Post by ajgreeny on 2017-05-22
If you are not prepared to update at least the security packages when they are notified to you, I wonder if Ubuntu (or any other Linux distro) is the correct OS for you.

As a way to clarify exactly what is waiting for you to update at the moment, run 
```
sudo apt-get update
sudo apt-get -s upgrade
```
and post back here the output from the second of those commands; it will not actually download any packages when run with the -s option, so don't worry about that, but it will show us a list of packages and we can then tell you better the risk you are going to run if you don't upgrade the packages.

The suggestion in post #3 is perhaps worth trying, to see the download size of security packages alone without all the others, but none of this is something to be taken lightly; **security is very important**; just ask those running unpatched Windows who were caught by the Wannacrypt ramsomware.

---

