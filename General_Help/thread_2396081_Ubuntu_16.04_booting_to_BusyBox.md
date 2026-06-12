---
title: "Ubuntu 16.04 booting to BusyBox"
date: 2018-07-10
forum: General Help
---

### Post by SourceSlayer on 2018-07-10
Mods, apologies, I'm not sure where the proper forum to post this is, so please go ahead and move it whereever.

Hello, I have a laptop, Toshiba Satellite that I did a full install on from Ubuntu 16.04 on disk. Prior to using Ubuntu it ran Windows 10 and after an update wouldn't get passed the Toshiba spash screen so I installed Ubuntu on it. 

The issue is that now it shows GRUB which it didn't before and instead of a normal start up, gives me a BusyBox shell
[IMG]https://postimg.cc/y57oxmlj5/20180710_223132.jpg[/IMG]


[https://s19.postimg.cc/jdke71dzn/15312786249668941560475930893125.jpg](https://s19.postimg.cc/jdke71dzn/15312786249668941560475930893125.jpg)

---

### Post by wildmanne39 on 2018-07-10
Hello, your post is fine where it is.

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by SourceSlayer on 2018-07-10
Okay, thanks.

---

### Post by cariboo on 2018-07-11
Your screenshot tells you what needs to be done:

> The root file system on /dev/mapper/ubuntu--vg-root requires a manual fsck

You need to start in recovery mode, then select root from the menu and type at the prompt:

```
fsck /dev/mapper/ubuntu--vg-root
```

---

