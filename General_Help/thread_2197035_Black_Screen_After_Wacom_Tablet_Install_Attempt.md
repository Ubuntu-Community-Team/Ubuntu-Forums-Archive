---
title: "Black Screen After Wacom Tablet Install Attempt"
date: 2014-01-01
forum: General Help
---

### Post by jasonadamlong on 2014-01-01
Hi all, 

(First, I am using an HP G50 laptop, with Ubuntu 12.04.3 installed last week. I am currently booting from a LiveCD, as my previous boot is inoperable.)

After following this guide in an attempt to use my Wacom CTH480 tablet, I've been left with a black screen on all bootup attempts. 

[http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

I followed the guide, beginning with part** I: Install Input-Wacom's Wacom.ko**. I followed the code to line "**cd input-wacom-0.19.1**" (though I was using "cd input-wacom-0.22.1"). The code stopped working here, though I can't now paste the message I would receive. I must also mention that I failed to change the code in this line: "(For Ubuntu **use libx11-dev** instead of libX11-dev in the following command)."

At some point I restarted my computer to find a black screen. I ran boot repair in an attempt to fix the problem; here is the result of the repair: 

[http://paste.ubuntu.com/6676108](http://paste.ubuntu.com/6676108)

I'm still left with a blank screen. On a few of the previous bootup attempts I received this message: "**boot up error could not write byte: broken pipe**". I am not receiving this message any longer. 

_**EDIT**_: I'm assuming that the problem has to do with the kernel, since that's the part of the system I was toying with in** Part I: Install Input-Wacom's Wacom.ko**. When I boot without a LiveCD, I get the black screen; when I boot from previous kernels I get the "**boot up error could not write byte: broken pipe**". I am attempting to solve the problem through searching the forum for old posts; I don't mean to make a duplicate thread. I've taken note of this warning in the Linux Mint thread: 

***Warning 2**  - Ubuntu Precise 12.04.2 was updated to include the Quantal kernel and X  Server (which means you no longer need to run the frankenserver patch).   Precise 12.04.3 has the Raring kernel and X Server (kernel 3.8 & X  Server 1.13).  If while compiling input-wacom when you run **sudo apt-get install build-essential etc.** the output asks if you want to remove a list of drivers and libraries ending with the suffixes -lts-quantal or -lts-raring, **STOP!  That will disable your system.***

....but I never received a message to remove the drivers and libraries. 

Any help in the right direction is very, very appreciated. 

Thank you,

Jason

---

### Post by jasonadamlong on 2014-01-02
Here's a question: is it possible to locate a file and put it on a flash drive while in recovery mode? The only thing I need from my previous installation of Ubuntu is my Keepassx file. Then I can just reinstall Ubuntu. 

Thanks again,

Jason

---

### Post by jasonadamlong on 2014-01-02
Hi everybody,

The problem has not been solved, but I was able to extract the keepassx file with an external mount. All I have to do now is reinstall Ubuntu.

I appreciate anybody who read my post and considered the problem. 

Thanks once again, 

Jason

---

