---
title: "Cannot download metalink, therefore the ISO cannot be downloaded either"
date: 2015-06-09
forum: General Help
---

### Post by Steven_White on 2015-06-09
Hey guys, I'm a new Ubuntu user (technically not even new, I can't even get it installed!) and I'm having problems with installing Ubuntu 14.04. It keeps saying that it cannot download the Metalink, therefore the ISO can't be downloaded either. Here's what it's saying:
[ATTACH=CONFIG]262500[/ATTACH] 
I have no idea what I did wrong, so if you can, **_*PLEASE HELP.*_**

Thanks,
Steven White

---

### Post by howefield on 2015-06-09
What are you doing to get the error, and did you look at the logs ?

---

### Post by yancek on 2015-06-09
The image of the download you posted has "wubi" in it and the wubi installer, although still available, is not supported and is not expected to work on a machine with windows 8 so if you have windows 8, don't bother.  The wubi software was meant as a means to test Ubuntu, not as a permanent installation and would simply be installed inside windows as a program.  If you want to actually install Ubuntu on its own partition, the link below is the download site.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by hakuna_matata on 2015-06-11
> **Steven_White said:**
> It keeps saying that it cannot download the Metalink, therefore the ISO can't be downloaded either.
Wubi for 14.04 uses outdated download links. But it is not really a problem because there is no need to use Wubi for downloading Ubuntu iso files. It is easy to download it manually. 

If you already downloaded the correct version of iso file, you can disconnect internet connection before you'll run wubi.exe. This should avoid the error message you described in your post. 

There is also no need to run Wubi for installing Ubuntu and in almost all cases it is better to avoid Wubi.

 But if avoiding Wubi means for you that you avoid Ubuntu and use an outdated Windows XP for internet, it should be a better solution if you use one of the Wubi versions which I patched. e.g.: wubi14042.exe for 14.04.2 from a [dropbox folder]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na")

---

