---
title: "Updating from Wubi 7.04"
date: 2008-03-28
forum: General Help
---

### Post by n3hu on 2008-03-28
I am running wubi 7.04 and have a bunch of added applications...
ham radio stuff, signal analysis software, wine, etc.

  Is there a way to upgrade to 8.04 and preserve all of the added applications or do I have to start over? 

  I spent a BUNCH of time installing all of these applications and getting them running. If I have to re-install all of them, is the 8.04 update worth it?

tia
rob

---

### Post by Joeb454 on 2008-03-28
It depends, I'm not sure what it's like upgrading through Wubi...last time I heard it was quite a pain to do it.

You could always stick with 7.04 if it works for you :)

---

### Post by gavinjb on 2008-03-28
with Ubuntu you usually have an upgrade option in the package manager (make sure you have all patches applied before running it), but as you are running 7.04 I would have thought you would already have an option to upgrade to 7.10.

I know you can run the updater with an option to force an upgrade, but cant remember the option, but if you hunt around the forum you should find it somewhere.

---

### Post by ago on 2008-03-28
> **n3hu said:**
> 
  Is there a way to upgrade to 8.04 and preserve all of the added applications or do I have to start over? 


Start over!

But there are 2 interesting tricks:

* If you save your system.virtual.disk and home.virtual.disk files before uninstalling 7.04, you can mount them and access any file in there from within 8.04.

* You can save a list of all the packages you installed in 7.04(dpkg &#8722;&#8722;get&#8722;selections > list_of_installed_files) and then replay that on 8.04 (cat list_of_installed_files > dpkg --set-selections && sudo apt-get dselect-upgrade)

From 8.04 dist-upgrades will be fully supported.

---

### Post by n3hu on 2008-03-28
Thanks for the info... I can actually save the entire 7.04 load onto
a USB drive. I guess that if it comes down to it, I can just go back altogether....

  How stable is the 8.04 distro? Would I be better off waiting for a while until more of the kinks are out of 8.xx?

rob

---

### Post by ago on 2008-03-28
> **n3hu said:**
> Thanks for the info... I can actually save the entire 7.04 load onto
a USB drive. I guess that if it comes down to it, I can just go back altogether....

  How stable is the 8.04 distro? Would I be better off waiting for a while until more of the kinks are out of 8.xx?

rob
I'd say it is fairly stable, BUT one of the issue is that you will experiance a LOT of package upgrades before the final. So if you have a slow connection might be a bit annoying.

---

### Post by mikedep333 on 2008-03-28
> **ago said:**
> 

* You can save a list of all the packages you installed in 7.04(dpkg &#8722;&#8722;get&#8722;selections > list_of_installed_files) and then replay that on 8.04 (cat list_of_installed_files > dpkg --set-selections && sudo apt-get dselect-upgrade)

Wow, thanks alot. That is very useful advice people like me. I am frequently reinstall ubuntu 8.04 on my laptop in hopes that reinstalling it will fix some bugs. (With  7.10 I experienced this one bug consistently from when I installed it in beta, but reinstalling the final release fixed it.)

> **ago said:**
> I'd say it is fairly stable, BUT one of the issue is that you will experiance a LOT of package upgrades before the final. So if you have a slow connection might be a bit annoying.
From my personal experiences and other people's, I would say that 8.04 beta stability varies alot from hardware to hardware. I definitely agree that you should not install 8.04 until RC or final if you are on a slow connection.

---

