---
title: "SUDO hangs in 10.04--any solutions?"
date: 2013-02-20
forum: General Help
---

### Post by rondamato on 2013-02-20
Hello friends,

My company has 10.04/Gnome deployed across several thousand desktops,  and I only see this problem come up every now and then, but I'm really  having an issue with it. It doesn't help that I am a relative newcomer  to Ubuntu--most of my experience is long ago, and with Free-BSD to boot!

Anyhow, my issue lies in the SUDO command. I am working on a virtual  machine that I have no physical access to, though I do have root privs.  The machine is severely hanging on sudo. Like, I'm talking 10 to 20 minutes. Today I have another ticket--now TWO machines are doing it. 

For example, if I issue the command 'sudo echo hi' in a term window I am  greeted with several minutes (3 to 5) of a blinking cursor, sometimes  much longer, before a request to authenticate pops up. Once it does it's  not an issue; immediately upon entering the PW the term will echo.

I checked to make sure that /etc/hostname file contained the same  computer name as the /etc/hosts files...they match. In /etc/hosts my  first two lines are:

127.0.0.1 VMname.domain VMname localhost
127.0.1.1 ubuntu32-template.domain ubuntu-32-template

I built a VDI and the /etc/hosts file is precisely the same, though I have no issues with SUDO hanging on my machine who's process list and /etc/hostname--/etc/hosts are in exactly the same syntax as the affected computers.

Also note that the affected machines are running NOTHING. All processes are killed--all there is up is a Gnome desktop and maybe a few term windows.

I've Googled this for a good part of the afternoon and found that this  is a "bug"--has anyone yet proposed a fix for this? Since this is in a  development environment I'd like to keep the kernel where it is  (2.6.32-38-generic) unless it can be upgraded without potentially  damaging anything...I just have very little idea as to what's going on  here until I have more time. This is NOT a 'requirement' though--if  upgrading the kernel would help and not do any harm let me know and I'll  do so immediately.

Any help that anyone can offer would be greatly appreciated! Sorry for  the lack of information; I know that its all not much help. If you have  anything specific to ask I'll be happy to look/answer though! :D

---

### Post by JayKay3OOO on 2013-02-20
Here is how to upgrade the kernel although you might want to test it on a dev machine (if you have one). Seems to be a pretty good guide if you scroll to the ubuntu bit.

[http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/)

From what I can gather nothing should break, but If I was the admin I'd be doing a test run before going live.

---

