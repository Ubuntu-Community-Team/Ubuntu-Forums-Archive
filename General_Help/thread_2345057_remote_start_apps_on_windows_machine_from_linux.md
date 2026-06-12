---
title: "remote start apps on windows machine from linux?"
date: 2016-11-30
forum: General Help
---

### Post by springs1 on 2016-11-30
hi guys, 

just wondering if there is anything available to remotely start an application on a windows machine. looking for something like psexec that will actually start the application on the device and not within the terminal. 

I've had a look at winexe but this runs within the terminal from what i can see / tested.

just trying to automate some stuff and this is one step im trying to work around. i've got an app for my phone [https://play.google.com/store/apps/details?id=com.owtroid.remotelauncherfree](https://play.google.com/store/apps/details?id=com.owtroid.remotelauncherfree) that does it from phone to linux / windows but would like to go from linux to windows.

Any ideas?

---

### Post by HermanAB on 2016-11-30
Well, you could install openssh on cygwin,  then run program and push it to the background as usual with &.

---

### Post by TheFu on 2016-11-30
Ansible is reported to [work with Windows]("https://docs.ansible.com/ansible/intro_windows.html") now.  That's a devops tool.  There's also lots and lots of Windows hacking powershell tools ... guess those could be used for "good" as well?  I always found the PowerShell security model to be too cumbersome - especially for Home versions of the OS. In a corporate env, maybe it would work?

---

