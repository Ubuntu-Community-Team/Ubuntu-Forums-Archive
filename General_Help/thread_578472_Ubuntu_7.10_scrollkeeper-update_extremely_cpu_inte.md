---
title: "Ubuntu 7.10: scrollkeeper-update extremely cpu intensive"
date: 2007-10-17
forum: General Help
---

### Post by Menzonius on 2007-10-17
Hi,

Yesterday I installed Ubuntu 7.10 on a Toshiba Tecra 8000 (a laptop with PII 400Mhz cpu, 40GB hdd and 256MB RAM). 

I used the "alternate" install CD image, and selected LVM with hard drive encryption. Almost everything is working just fine.

However, when I run Ubuntu I noticed a process called "scrollkeeper-up" (=> scrollkeeper-update) often running and consuming a lot of CPU resources. This is undesirable for two reasons: 
1) The noisy CPU fan begins to operate 
2) The system becomes less responsive

The process appears to be related to something called "scrollkeeper", which is apparently a documentation cataloging program. However, I do not require access to gnome/ubuntu documentation through yelp, and by extension also do not require scrollkeeper on my system.

So I want to uninstall Scrollkeeper if possible. But when I try to do that using the Synaptic package manager, it indicates that this operation will require removing software that I do _*not*_ want removed under any circumstance (e.g. "ubuntu-desktop").

I have currently fixed the problem by following the instructions I found [_here_]("https://bugs.launchpad.net/ubuntu/+source/scrollkeeper/+bug/44535/comments/4").

But if anyone knows of a cleaner way of disabling/removing scrollkeeper, then I'd appreciate any help regarding how this is achieved.

Thanks in advance!

---

### Post by smartbei on 2007-10-19
I am having the same problem. Just so you know, removing the ubuntu-desktop metapackage has no detrimental effect on the system. It just depends on all the packages that the cd installed, so if you remove one of them, it is removed as well.

---

### Post by Menzonius on 2007-10-19
Hi,

Thanks for your reply! But unfortunately there are also about 30 other programs besides "ubuntu-desktop" that Synaptic wants to remove, including "gedit", "nautilus" and "synaptic", and I'm not sure if these are also metapackages. Is it nonetheless still safe to remove scrollkeeper?

Thanks in advance!

---

### Post by freddy33 on 2007-11-15
I have the same problem. It looks like scrollkeeper-up is not written correctly for Dual core SMP and/or 64 bits machines.
If your patient it should finish indexing the files and go back to normal.

---

### Post by paul cooke on 2008-01-09
it's infuriating that it's running at all during an update... why can't it wait until afterwards?????

My laptop is completely unresponsive at the moment, in the middle of post installation updates and scrollkeeper update is slowing the entire update process right down... it's making the entire software update process look downright amateurish...

I'm currently having to manually kill it everytime it spawns... the update is proceeding far faster...

---

### Post by paul cooke on 2008-01-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/scrollkeeper/+bug/44535](https://bugs.launchpad.net/ubuntu/+source/scrollkeeper/+bug/44535) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				it's infuriating that it's running at all during an update... why can't it wait until afterwards?????

My laptop is completely unresponsive at the moment, in the middle of post installation updates and scrollkeeper update is slowing the entire update process right down... it's making the entire software update process look downright amateurish...

I'm currently having to manually kill it everytime it spawns... the update is proceeding far faster...

---

### Post by crf on 2008-01-29
This program bugs me. It regularly thrashes my computer for several minutes at a time.

I read that you can replace it with rarian. Remove scrollkeeper, install rarian ?
[https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=Rarian&content=](https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=Rarian&content=)

---

### Post by Menzonius on 2008-02-04
Thanks for the tip! I installed rarian and it automatically removed scrollkeeper. The only small problem I now have is that it also removed gnochm which I use to read .chm files.
Fortunately, all that is required is to download the sources and recompile gnochm without scrollkeeper support. So my problem is essentially solved, thanks!

---

### Post by sureinlux on 2008-04-14
Thanks a lot crf. That helped me a lot too. Additionally gramps is also uninstalled along with gnochm.

---

