---
title: "broke my dpkg on wsl"
date: 2024-05-23
forum: General Help
---

### Post by ulao3 on 2024-05-23
I was playing around with linux on wsl and tried to install kde for fun but it when bad wrong. Seems dpkg now wants to install whoopsie and I can not remove purge or install it. No matter what I do it fails. Is there a way to remove a package from the list to be configured?

---

### Post by yancek on 2024-05-23
Which version of windows are you using?  I've not used WSL but my understanding is that the systems usually don't have a GUI unless you are running windows 11.  That may have changed and ia graphical interfact may now be available with windows 10.

You would probably need to be more specific to get help such as posting specifically what you did an how you did it and any error/warning messages you saw.

---

### Post by ulao3 on 2024-05-23
yeah its 11, I can not install anything because the package managers  says you have packages that need configuring. Then I do that -a to  configure then, and it fails. Every time I want to install something it says this so its just repeats. I can run it and capture  the text but it takes about 4 hours to fail. I just want to tell it to  forget about whoopsie and stop trying to configure it. Was hoping this  was a general Linux question but I guess its more involved?

Here I try to install something. 

E: Invalid operation jstest
ulao@gamer:/mnt/c/Windows/System32$ sudo apt-get install jstest
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

If I run it, it shows this

 sudo dpkg --configure -a
Setting up whoopsie (0.2.77) ...
Failed to preset unit: Transport endpoint is not connected
/usr/bin/deb-systemd-helper: error: systemctl preset failed on whoopsie.path: No such file or directory
Failed to reload daemon: Transport endpoint is not connected

..and sits here for hours. If I kill it, or of it errors out, I'm in a loop.

---

### Post by ActionParsnip on 2024-05-24
OK, did you look online for what
```

/usr/bin/deb-systemd-helper: error: systemctl preset failed on whoopsie.path: No such file or directory

```
means?

---

### Post by ulao3 on 2024-05-24
it led me to a hold function. That seems to do what I was looking for.

but trying to install another packages I'm back to the whoopsie errors. 
> 
Setting up libglibmm-2.4-1v5:amd64 (2.66.2-2) ...
Setting up libevemu3:amd64 (2.7.0-3) ...
Setting up whoopsie (0.2.77) ...
Failed to preset unit: Transport endpoint is not connected
/usr/bin/deb-systemd-helper: error: systemctl preset failed on whoopsie.path: No such file or directory
Failed to reload daemon: Transport endpoint is not connected
Failed to start whoopsie.service: Transport endpoint is not connected
See system logs and 'systemctl status whoopsie.service' for details.
invoke-rc.d: initscript whoopsie, action "start" failed.
Failed to get properties: Transport endpoint is not connected
dpkg: error processing package whoopsie (--configure):
 installed whoopsie package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of kde-config-whoopsie:
 kde-config-whoopsie depends on whoopsie; however:
  Package whoopsie is not configured yet.

dpkg: error processing package kde-config-whoopsie (--configure):
 dependency problems - leaving unconfigured
Setting up libcairomm-1.0-1v5:amd64 (1.12.2-4build3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Set

---

### Post by yancek on 2024-05-24
Take a look at the page from the link below.  The software you are referring to can be easily disabled if it creating problems.

[https://bookofzeus.com/harden-ubuntu/disable-services/disable-whoopsie/](https://bookofzeus.com/harden-ubuntu/disable-services/disable-whoopsie/)

>  Was hoping this  was a general Linux

It's not because you are running it in windows which is not at all the same as running a straight Linux.  My understanding of WSL is that there are limitations on using a GUI in it.  I would suggest that you at least read through the information on WSL at the microsoft site regarding the limitations.

[https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

---

### Post by ulao3 on 2024-05-24
Yeah, I was only playing with it to learn a bit.  It certainly is not critical to make run, 

As  to the advice of the first link, that file does not exist. Now I'm no  excerpt on linux but if DPKG can not finish setting up whoopsie, why would it be assume  configured? At any rate, I didnt make the file since it did not exist.   as to the purge I also tried this before but the DPKG is still broken, it  simply does not work any more. I'm just trying to understand how to fix  a broken package manager. I had this all the time back in the day with  libranet, not seen it since. 

Here is the output.
> 
ulao@gamer:~$ sudo apt-get purge whoopsie
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  kde-config-whoopsie* whoopsie*
0 upgraded, 0 newly installed, 2 to remove and 98 not upgraded.
2 not fully installed or removed.
After this operation, 159 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 140607 files and directories currently installed.)
Removing kde-config-whoopsie (15.10ubuntu2) ...
Removing whoopsie (0.2.77) ...
Failed to stop whoopsie.service: Transport endpoint is not connected
See system logs and 'systemctl status whoopsie.service' for details.
invoke-rc.d: initscript whoopsie, action "stop" failed.
dpkg: error processing package whoopsie (--remove):
 installed whoopsie package pre-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Failed to preset unit: Transport endpoint is not connected
/usr/bin/deb-systemd-helper: error: systemctl preset failed on whoopsie.path: No such file or directory
Failed to reload daemon: Transport endpoint is not connected
Failed to start whoopsie.service: Transport endpoint is not connected
See system logs and 'systemctl status whoopsie.service' for details.
invoke-rc.d: initscript whoopsie, action "start" failed.
Failed to get properties: Transport endpoint is not connected
dpkg: error while cleaning up:
 installed whoopsie package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 whoopsie
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
ulao@gamer:~$


---

### Post by ulao3 on 2024-05-25
not sure how this did it but solved with

cd /etc/acpi/ && mv events events-OLD && mkdir events

[https://github.com/microsoft/WSL/issues/9029](https://github.com/microsoft/WSL/issues/9029)

---

