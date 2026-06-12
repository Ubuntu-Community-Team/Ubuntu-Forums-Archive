---
title: "GRUB visual artifacts after upgrading to 22.04.3 LTS"
date: 2024-01-07
forum: General Help
---

### Post by SamInside on 2024-01-07
I was using *20.04 LTS*, so I recently finally re-installed *Xubuntu*, and now I'm on a normal installation of *Xubuntu 22.04.3 LTS*.

When booting, I get *GRUB* glitches as seen in the video: [https://vimeo.com/900571782](https://vimeo.com/900571782)

**Specs:**
Coffee Lake i5-8400
Asus Prime B360-Plus ATX
Radeon RX 570 ITX 4G
Monitor Dell S3422DWG

```
$ sudo apt list --installed | grep linux-image
linux-image-6.2.0-26-generic/jammy-updates,jammy-security,now 6.2.0-26.26~22.04.1 amd64 [installed,automatic]
linux-image-6.2.0-39-generic/jammy-updates,jammy-security,now 6.2.0-39.40~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 6.2.0.39.40~22.04.16 amd64 [installed,automatic]
```

---

### Post by SamInside on 2024-01-11
Bump, I guess.
I'll be interested just in knowing if others have a similar problem.

---

### Post by Rubi1200 on 2024-01-11
Personally, not seen something like that before.

But...

1. what is your current screen resolution?

2. post the output of ```
cat /etc/default/grub.d
```

---

### Post by SamInside on 2024-01-11
> **Rubi1200 said:**
> 1. what is your current screen resolution?
3440x1440, as per default for my monitor.
As said, with 20.* LTS it worked fine, though.

> **Rubi1200 said:**
> 2. post the output of `cat /etc/default/grub.d`
It's a directory. Inside there's *`**init-select.cfg**`*, all commented, so no content.
If you meant *`/etc/default/grub**`*, it's mostly untouched; omitting commented lines, it's:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nosgx"
GRUB_CMDLINE_LINUX=""

```

---

### Post by tea for one on 2024-01-11
You could try one of the matching resolutions offered by grub.
Boot your PC and allow the grub menu to appear.
Press [COLOR="#0000FF"]c[/COLOR] for grub prompt
```
grub>videoinfo
```
Make a note of the resolutions displayed.
Then, edit grub
```
sudo nano /etc/default/grub
```
```
GRUB_GFXMODE=1280x1024  [COLOR="#0000FF"]just an example[/COLOR]
```
```
sudo update-grub
```
You never know, you may be blissfully happy with a legible grub menu
Or it could drive you into depths of despondency 

Worth a shot, methinks ;)

---

### Post by SamInside on 2024-01-12
> **tea for one said:**
> [HTML]GRUB_GFXMODE=1280x1024[/HTML]
This completely fixed the issue, thank you very much.

Should I report a bug somewhere?

Should e.g. this be included by default in the Ubuntu/Xubuntu recent installations, and maybe that was included in 20.*? Or is it a GRUB new bug that was not present in older versions, etc.? This probably requires some investigation by someone more knowledgeable than me.

---

### Post by tea for one on 2024-01-12
Pleased to have helped.
To help other forum users/searchers, it's a nice gesture to mark the thread as solved:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by SamInside on 2024-01-13
> **tea for one said:**
> To help other forum users/searchers, it's a nice gesture to mark the thread as solved
Of course, but as you can see, I still had questions (about issuing or not a bug report, and where).
And, more info: I've been able to make a screenshot-from-video about some error that appears for just a split second, might be related:



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293303&stc=1[/IMG]

---

### Post by MAFoElffen on 2024-01-13
> **SamInside said:**
> This completely fixed the issue, thank you very much.

Should I report a bug somewhere?

Should e.g. this be included by default in the Ubuntu/Xubuntu recent installations, and maybe that was included in 20.*? Or is it a GRUB new bug that was not present in older versions, etc.? This probably requires some investigation by someone more knowledgeable than me.

Not a bug. This has been well documented since Kernel, Grub2, and Linux Graphics Layer changes back about Ubuntu 11.04 (2011)... Please read Post #1 of my Graphics Resolution Sticky in my signature line... That is how it (still) works, and the fixes for many things graphics related for the Linux Graphics Layer. (not just Ubuntu and it's flavors.)

---

### Post by SamInside on 2024-01-14
> **MAFoElffen said:**
> ...
Ok, thank you.
What about my last screenshot, should I just ignore those errors?

---

