---
title: "Default panel freezes when video is played in full screen"
date: 2020-09-17
forum: General Help
---

### Post by themeditationcenter on 2020-09-17
This is a weird but when I play my video in full screen the default panel just freezes. I see the digital clock frozen.
But everything else is just fine.And when I get the video off full screen, the panel is back to normal. Can anyone help me resolve this issue.

My hardware info can be found [here]("https://paste.ubuntu.com/p/NJDVhy7fxx/")

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal

```
```
$ plasmashell --version
plasmashell 5.18.5
```

My dmesg info can be found [here]("https://paste.ubuntu.com/p/vdRFvtgjVx/").

I am not sure how to get the display logs, in case if you need it.

Any help on this will be a greatly appreciated.

---

### Post by springshades on 2020-09-18
I don't have any really great ideas to be honest. There may be some KDE wizards around who would be much better help. The first idea that popped into my head though is that KDE has a nasty history of relatively minor widgets being able to misbehave and take out massive portions of the desktop environment. It's probably not supposed to happen, but I'd bet it's still possible that one of them could lock up and freeze part of the system.

The first thing I'd do is look through and see if you can temporarily disable or remove as many widgets as possible to see if it helps. In particular, since it is related to video, I might look for any sort of widget related to audio streams.

---

### Post by SeijiSensei on 2020-09-18
When I watch a video full-screen, the image covers the panel?

I'm using Kubuntu 20.04.1 as well. I have an NVIDIA card with the proprietary driver though, so I'm not using the CPU to decode video. What do you get for a video adapter with "lspci"?

```
VGA compatible controller: NVIDIA Corporation GP108 [GeForce GT 1030] (rev a1)
```

Open a terminal and run "top".  Note the load averages.  Then watch something full-screen for a few minutes. What are the load averages now? If they've increased substantially, then you're using the CPU to decode the video which could cause performance issues elsewhere.  

What player software are you using? My preference is the combination of mpv for the player engine and SMPlayer for the GUI interface.
```
sudo apt install mpv smplayer
```
Now open a video with SMPlayer and do the same comparisons as before. Any better?

---

### Post by ajgreeny on 2020-09-18
You say "full screen" but do you really mean "maximised window" which would mean the panel is still visible?

As SeijiSensei says, if running full screen you can not view anything other than the video, unless you Alt-tab to another running application when the panel also appears on my Xubuntu-20.04 system.

---

### Post by themeditationcenter on 2020-09-21
> **ajgreeny said:**
> You say "full screen" but do you really mean "maximised window" which would mean the panel is still visible?


As SeijiSensei says, if running full screen you can not view anything other than the video, unless you Alt-tab to another running application when the panel also appears on my Xubuntu-20.04 system.

Not maximized window but "full screen", I have dual monitor and I can see the default panel frozen in the second monitor too.
And also I alt +tab in the current monitor to check if the panel was frozen, which indeed it was.

My lspci command results in the below output:
```

07:00.0 VGA compatible controller: NVIDIA Corporation Device 1f14 (rev a1)
``` 

> **SeijiSensei said:**
> 
What player software are you using? My preference is the combination of  mpv for the player engine and SMPlayer for the GUI interface.


I tried smplayer, vlc, mpv, but same issue.

Like [ 						 							 						 					]("https://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")**[COLOR=#000000] [/COLOR]**[COLOR=#000000]suggested, I'll monitor the system usage and report soon.

Thank you again very much for trying to help me out.[/COLOR]

---

### Post by SeijiSensei on 2020-09-22
Did you go to System Settings > Device Manager and let Ubuntu install the proprietary driver for your NVIDIA card? If not, try that.

---

### Post by themeditationcenter on 2020-09-22
Thank you. I just did a apt update / upgrade and it pushed some nvida updates to my machine and that did the trick.
Someone was looking at the thread then. Thank you all. Marking this thread as closed.

---

