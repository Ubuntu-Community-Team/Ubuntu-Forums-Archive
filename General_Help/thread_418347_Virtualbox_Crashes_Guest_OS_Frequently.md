---
title: "Virtualbox Crashes Guest OS Frequently"
date: 2007-04-22
forum: General Help
---

### Post by GSF1200S on 2007-04-22
Well, I decided to go ahead and just try a virtual emulation software.

I heard VirtualBox was lighter and included a virtual machine "maker," So I gave it a shot.

Now, I have one issue thats annoying, and one that makes it almost unusable

1) For some reason, whenever I click inside of my emulated box, I have no way to click out of it. I have my terminal mapped to the win key in Gnome, so pressing that will bring up a terminal and release me from the virtual machine. Ive read about some kind of "host" key, but I dont know what that is. I cant click the mouse icon at the bottom of the screen...

2) The virtual machine aborts for seemingly no reason frequently. Ill be doing something in Windows and all of a sudden, the box just goes away. It says "aborted" in the virtual box manager, and I have to restart the virtual machine. If I dont do anything, it will run forever. It will close sometimes every 45 seconds... Doesnt make sense to me...

---

### Post by raja on 2007-04-22
What guest OS are you using? And have you installed the guest additions ?

---

### Post by 4ebees on 2007-04-22
Hi there,

To answer your first question:

press the RIGHT Ctrl key. This will release your mouse from the virtual machine's capture.

I'm afraid I have no answer for your second question.

Regards,
4ebees

> **GSF1200S said:**
> Well, I decided to go ahead and just try a virtual emulation software.

I heard VirtualBox was lighter and included a virtual machine "maker," So I gave it a shot.

Now, I have one issue thats annoying, and one that makes it almost unusable

1) For some reason, whenever I click inside of my emulated box, I have no way to click out of it. I have my terminal mapped to the win key in Gnome, so pressing that will bring up a terminal and release me from the virtual machine. Ive read about some kind of "host" key, but I dont know what that is. I cant click the mouse icon at the bottom of the screen...

2) The virtual machine aborts for seemingly no reason frequently. Ill be doing something in Windows and all of a sudden, the box just goes away. It says "aborted" in the virtual box manager, and I have to restart the virtual machine. If I dont do anything, it will run forever. It will close sometimes every 45 seconds... Doesnt make sense to me...

---

### Post by GSF1200S on 2007-04-22
> **raja said:**
> What guest OS are you using? And have you installed the guest additions ?

I have windows XP as the guest OS. No I have not installed the guest additions.. I currently have a problem with my DVD RAM drive not being able to burn anything, so do you know of a location where I can download the .ISO file? I know I can mount an .ISO file with virtualbox..

---

### Post by GSF1200S on 2007-04-22
> **4ebees said:**
> Hi there,

To answer your first question:

press the RIGHT Ctrl key. This will release your mouse from the virtual machine's capture.

I'm afraid I have no answer for your second question.

Regards,
4ebees

Thanks for that.. right control key works as you said :)

---

### Post by 4ebees on 2007-04-26
No probs.

To install the 'guest additions', when you have an OS running (as a guest inside of VirtualBox) you go to the toolbar at the top of the windows in VB and click on 'devices' then slelect 'install guest additions'.

Hope this helps.

Regards,

4ebees

---

### Post by spankymasterc on 2007-04-26
dude install vmware worksatition 6.0 its AWSOME its also has a light player and its nice 2...

Add me on messenger and ill get you up an running if you like ive had no problems what so ever....

---

### Post by doublemeat on 2008-02-20
VMWare Workstation costs money, and is not "light" by most rational measures.  You might be thinking of the free VMWare Player?  VMWare Server [yes a third incarnation] is "free" (as in beer not speech) and very robust in terms of feature set, although you need the Windows version to do certain things like shrink/grow volumes.  But in both Linux and Windows forms, it installs a bewildering array of stuff that never seems to uninstall cleanly.  Plus you have to compile it, there isn't a Gutsy package.  I ran VMWare Server for quite a while on Feisty and it worked great (with a few annoyances).  But Gutsy broke it, and installing the new version of VMWare Server worked, but much, much more slowly.  It also broke hardware assist.  And that is a common problem with Gutsy/VMWare Server.

VirtualBox is quirky and it's UI to the guest works very inconsistently, but when you use it against Ubuntu's built-in RDP client (instead of it's built-in viewer), it works with Windows guests like a dream in terms of full keyboard functionality and switching between OSes.  (If fastest video response is a must...e.g. for video...then you'll need to stick with the built-in viewer.)  It's also slightly more "open" than VMWare, but you'll want the proprietary version for best functionality.

VirtualBox is also objectively and subjectively much, much faster than VMWare Server ever was (according to several synthetic Sysandra benchmarks I ran in multiple host/VM/guest configurations - plus subjective everyday use).  It has been absolutely rock-solid running Win2k on Gutsy on my macbook, but Win2k on VirtualBox/Gutsy on an older P4 has been experiencing some random guest lockups, like the OP asked about.  At the moment though I'm confident I'll work it out, because I haven't dove in yet to fix it and I have a few shots in the dark in mind to try.

Win2k on VirtualBox on Gutsy on a P4 2.6ghz [no hardware assist, single core] is AMAZINGLY fast and useable!  I was blown away--whereas no other VM solution I tried on this config was even REMOTELY tolerable (all with proper guest extensions installed).  Not VMWare Server (on Gutsy OR XP as host), not MVWare Player, and most definitely not Microsoft Virtual PC 2007 (on XP host) which was just plain stupidly unusably slow.


> **spankymasterc said:**
> dude install vmware worksatition 6.0 its AWSOME its also has a light player and its nice 2...

Add me on messenger and ill get you up an running if you like ive had no problems what so ever....

---

