---
title: "IG.com's Level2 access program is a  Dos / Windows program"
date: 2022-02-28
forum: General Help
---

### Post by Robbyx on 2022-02-28
IG.com the stockbroker offers an app, called L2,  that only runs under Windows, as per their tech support. 

I would prefer not to install a virtual machine  as I do not have a copy of windows and do not want it.

The app is installed via two programs 

1. A setup called prerequisites.
2. The L2 click once installer.

[https://www.ig.com/uk/help-and-support/platforms/l2-dealer/how-do-i-download-l2-dealer](https://www.ig.com/uk/help-and-support/platforms/l2-dealer/how-do-i-download-l2-dealer)

The purpose of the installer is to access a live feed and the LSE stock exchange's dealer book that shows offers  and bids.

Has anyone installed it on Ubuntu?

Here is the  question that a user raised in the IG support conference:

> Can I use L2 dealer on Mac?

You can’t use L2 dealer on a Mac. The platform was designed for PC, and built on a PC-specific framework called .NET, which is not supported by Apple. 


I note that there is a version of .NET for Ubuntu

How should I proceed?

What should I do to start the process? Which emulator should I use? Wine? CrossOver Linuxx


See this link for a list of claimed as best emulators.
[https://www.ubuntupit.com/best-windows-emulators-for-linux-enthusiasts/](https://www.ubuntupit.com/best-windows-emulators-for-linux-enthusiasts/)


R

---

### Post by QIII on 2022-02-28
You might want to take a look at [this]("https://docs.microsoft.com/en-us/dotnet/core/install/linux").  Installing that should provide the .NET libraries you need.  I've never fiddled with it, so I don't know what secrets you might have to invoke to get it to run.

There is even a .NET development environment for Linux called [MonoDevelop]("https://www.monodevelop.com/").  As far as I know it is limited to C#.  Apparently one can write cross-platform applications with it.

Caveat:  I don't know if Microsoft has given in to the fact that Linux is here, or if this is part of a sinister plan to get their hooked claws in enough to lay claim to Linux.

---

### Post by #&amp;thj^% on 2022-02-28
> **Robbyx said:**
> I
What should I do to start the process? Which emulator should I use? Wine? CrossOver Linuxx


See this link for a list of claimed as best emulators.
[https://www.ubuntupit.com/best-windows-emulators-for-linux-enthusiasts/](https://www.ubuntupit.com/best-windows-emulators-for-linux-enthusiasts/)


R

Just to quote: (If it will work this would be my first chioce :))
> 4. QEMU

QEMU is a robust virtual machine emulator and hardware visualizer that can run Windows programs directly inside a Linux system. It can act in different ways, and you&#8217;ll be primarily using it as a full system emulator for running a Windows system inside Linux. You can then install applications developed for Windows in your Linux system. It is maintained very well and takes care of bugs and errors faster than most Windows emulators for Linux.
But bare in mind I'm with Qlll on "so I don't know what secrets you might have to invoke to get it to run."
IF? I have spare time today I might give it a whirl.

---

### Post by Robbyx on 2022-02-28
Thank you for your responses. 

Ifallen I hope you do have the time to give feedback about your experience with  trying to run the app from within QEMU

R

---

### Post by #&amp;thj^% on 2022-02-28
> **Robbyx said:**
> Thank you for your responses. 

Ifallen I hope you do have the time to give feedback about your experience with  trying to run the app from within QEMU

R
Looks like it will be tomorrow, will I have to sign-up for this?(I need to know first)
EDIT: If you decide to go before me, you will need this  FreeDOS on QEMU :  [https://www.cloudsavvyit.com/6719/how-to-use-qemu-to-boot-another-os/](https://www.cloudsavvyit.com/6719/how-to-use-qemu-to-boot-another-os/)

---

### Post by Robbyx on 2022-02-28
I was able to download the apps without registering. However to access the streaming data is going to involve registering. I was hoping that the installation of the app via the two stage procedure in my first post above will give us a good chance to know if the program can be installed that way. I presume after installation clicking on some form of access to the data and getting a request for user name and password would indicate it has been successfully installed because I assume the response will be coming from the server not the local program.

---

### Post by #&amp;thj^% on 2022-03-01
> **Robbyx said:**
> I was able to download the apps without registering. However to access the streaming data is going to involve registering. I was hoping that the installation of the app via the two stage procedure in my first post above will give us a good chance to know if the program can be installed that way. I presume after installation clicking on some form of access to the data and getting a request for user name and password would indicate it has been successfully installed because I assume the response will be coming from the server not the local program.

Forgive me Robbyx but I've registered and still have not heard back from them.
As a result I've given up.:(

---

### Post by Robbyx on 2022-03-02
Thank you for trying so hard. 

I have been thinking over the easiest way forward for me. I was given an oldish  laptop with windows on it. I am going to use it to run  the IG  Level 2 access app.

---

