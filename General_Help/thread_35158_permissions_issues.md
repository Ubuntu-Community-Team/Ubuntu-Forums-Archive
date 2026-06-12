---
title: "permissions issues"
date: 2005-05-17
forum: General Help
---

### Post by Tails747 on 2005-05-17
I am trying to install certain programs "limewire and winamp, for example" for my new install of ubuntu. I'm pretty sure I need to extract these into the root of the file system, but I get an error returned telling me I do not have permission to do this. How can I give myself permission to add files there?

---

### Post by bruizer on 2005-05-17
WinAMP??? Why go to the trouble of WinAMP when XMMS is free and in the base repos??

---

### Post by Tails747 on 2005-05-17
uhh.. because I like Winamp?

still.. I'd like to know how to get permission to add/remove/modify stuff in the root...

---

### Post by bruizer on 2005-05-17
Basic user accounts don't by default have the permissions to do anything to the root, as these files/directories are seen as owned by ROOT.

Go to a terminal and use sudo to do what you need to do. (ie - sudo <commands>, or just go to terminal and type su, which it then prompts for a password for the root account)

---

### Post by bruizer on 2005-05-17
BTW - XMMS is the free version that some good people decided to make in the likes of WinAMP... 

[http://www.xmms.org/about.php](http://www.xmms.org/about.php)

---

### Post by tread on 2005-05-18
How do you plan to install winamp? Isn;t that a windows program .. or did they port it?

---

### Post by bruizer on 2005-05-18
I've heard of someone actually getting this ported to Linux as well as one that created an rpm for it. I have not heard any success stories on this though...

---

### Post by SNo0py on 2005-05-18
[QUOTE=bruizer]I've heard of someone actually getting this ported to Linux as well as one that created an rpm for it. I have not heard any success stories on this though...[/QUOTE]
Maybe via wine? Anyways, xmms is much better....

---

### Post by lorap on 2005-05-18
hi buddy!
just write this:

sudo sh

after "sh" just write the installation script name.
that's all.
have a nice day.
pavel

---

### Post by bruizer on 2005-05-18
I have not heard anyone getting this ported through WINS all that easy. I have heard that it still comes back very buggy and unstable.

---

### Post by vegetto on 2005-05-18
winamp for lin that's a new one. There is no offical version of winamp for linux. try xmms or beep-media-player, if you prefer gtk2. I feel amarok is the best but it is kde app and is useful only if you have a huge collection. for playing individual songs bmp will do just fine.

---

### Post by op3studios on 2005-06-02
There is an .rpm of Winamp for Linux. Released by winamp!   I'm fighting with it now. 
\I got the .rpm translated with alien, see the files havn't quite figured out the rest of it lame as I am.
jz

I may be lame but I'm nice:


[http://www.dawnload.net/alternative_platforms/linux_software/winamp_for_linux.cfm](http://www.dawnload.net/alternative_platforms/linux_software/winamp_for_linux.cfm)

---

