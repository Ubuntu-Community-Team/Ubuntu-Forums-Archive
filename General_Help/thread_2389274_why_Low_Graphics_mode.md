---
title: "why Low Graphics mode?"
date: 2018-04-14
forum: General Help
---

### Post by daveginboav on 2018-04-14
_**EVENTS**_
Two events occurred Fri Apr 13th which may have led to my problem.
[LIST=1]
[*]Performed my usual daily update, nothing particular unusual except I did spot some Plymouth stuff going on, but that has happened a couple of times recently.  Had no reason to shutdown or restart system. 
[*]Through the post, I received a faulty replacement keyboard which I intended to use some of the keys to replace some worn ones on my keyboard.  Did not work; the clips were not compatible.  I knew the faulty keyboard had been reported as a problem with the power button, so I tried swapping over the keyboards just to see if indeed it was a faulty power button.  It was!  So reverted back to my good keyboard with the few worn keys.  Anyone who has swapped out a keyboard  in a Lenovo T410 will know there is a fiddly ribbon cable and connector. 
[/LIST]

[U][B]PROBLEM
[/B][/U]Upon performing a reboot after reassembly I recieved a graphic box with the words "system Running in Low graphics mode" and there were some other words about other input devices no right also.  Strangely, it affected my wifi connection also so was unable to research the issue.

_**DONE SO FAR**_

[LIST=1]
[*]Thinking I may have reinstalled the keyboard wrongly, something was snagging or the connector was wrong, I went back and did it again - twice.  The same problem occurred on rebooting. 
[*]Researched around on spare machine including ubuntuforums only to discover it could be a number of problems. 
[*]Tried rebooting in recovery mode; didn't really know what I was doing so just came back out. 
[*]Booted using the previous kernal and voila! all seems fine.  Not a problem whatsoever. 
[*]Rebooted a number of times now using previuos kernel and works every time. 
[/LIST]

_**CONCLUSION**_

[LIST=1]
[*]Am I right to conclude that I do not have a hardware problem as a result of my keyboard swapping? 
[/LIST]
_**QUESTION**_
[LIST=1]
[*]What, if anything, should I do get back to a safe booting regime without any intervention during boot? 
[/LIST]

_**MY SYSTEM**_
```
uname -a ThinkPad-T410 4.13.0-37-generic #42~16.04.1-Ubuntu SMP Wed Mar 7 16:03:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux  is the previous i.e. good kernel
uname -a ThinkPad-T410 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux is the newest kernel available
Part of lspci says 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

Here are some extracts from  Xorg log file when I try to boot with  4.13.0-38-generic kernel.
```
X.Org X Server 1.19.5
Release Date: 2017-10-12
[    33.313] X Protocol Version 11, Revision 0
[    33.313] Build Operating System: Linux 4.4.0-101-generic x86_64 Ubuntu
[    33.313] Current Operating System: Linux dave-ThinkPad-T410 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64
[    33.313] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-38-generic root=UUID=58d362c2-ed1e-479b-84f5-e5d8a782b08f ro quiet splash vt.handoff=7
...
 33.410] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
...
 34.288] (EE) Screen 0 deleted because of no matching config section.
...
    34.288] (EE) Screen 0 deleted because of no matching config section.
[    34.288] (II) UnloadModule: "modesetting"                                
[    34.288] (EE) 
Fatal server error:
[    34.288] (EE) Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
[    34.288] (EE) 
[    34.288] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    34.288] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    34.288] (EE) 
[    34.295] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by monkeybrain20122 on 2018-04-14
Does [this]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1758009") describe your problem?

---

### Post by daveginboav on 2018-04-14
> **monkeybrain20122 said:**
> Does [this]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1758009") describe your problem?

Sorry, no it does not describe my problem. When I look through the discussion on that bug, I checked and the compiz settings and files do not appear to be present in my system.

---

### Post by daveginboav on 2018-04-14
_**UPDATE**_
Doing further research, it would appear there are similar issues being experienced on kernel 4.13.0-38 and graphics.
This sound very similar [https://forums.linuxmint.com/viewtopic.php?t=267066](https://forums.linuxmint.com/viewtopic.php?t=267066)
As does this [https://community.amd.com/thread/227620](https://community.amd.com/thread/227620)

No real solutions though so far - maybe I just keep booting into the old kernel 4.13.0-37.  At least I am fairly certsin it wa s not me tinkering with keyboard! :)

---

### Post by Yellow Pasque on 2018-04-14
```
33.410] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
```
^This seems like the key to me. When I google, I see a lot of results with hybrid graphics. Is your T410 one of those machines with hybrid graphics or is it pure Intel?
```
lspci -nn | grep '\[03'
```

> This sound very similar [https://forums.linuxmint.com/viewtopic.php?t=267066](https://forums.linuxmint.com/viewtopic.php?t=267066)
As does this [https://community.amd.com/thread/227620](https://community.amd.com/thread/227620)

The first one seems vague. The second one is complaining about proprietary AMDGPU-Pro driver crashing, so seems unrelated.

---

### Post by daveginboav on 2018-04-14
> **Temüjin said:**
> ```
33.410] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
```
^This seems like the key to me. When I google, I see a lot of results with hybrid graphics. Is your T410 one of those machines with hybrid graphics or is it pure Intel?
```
lspci -nn | grep '\[03'
```



The first one seems vague. The second one is complaining about proprietary AMDGPU-Pro driver crashing, so seems unrelated.

output from lspci -nn | grep '\[03'
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
so I would say it is pure Intel.

The key point in my original post appears to have been missed - this problem appears to be an issue regarding the difference between the new kernel 4.13.0-38-generic and the one before it; 4.13.0-37-generic and that is why I mentioned the similarity between the links mentioned and my problem plus the problems are related to graphic cards generally.

---

### Post by Yellow Pasque on 2018-04-14
If it was me, I would try the 4.13.0-39 kernel from the proposed repo. I don't see anything in the changelog that would make me hopeful, but it's worth a try.

---

