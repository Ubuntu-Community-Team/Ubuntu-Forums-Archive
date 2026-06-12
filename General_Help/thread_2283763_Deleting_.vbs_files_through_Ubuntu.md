---
title: "Deleting .vbs files through Ubuntu?"
date: 2015-06-24
forum: General Help
---

### Post by renscy on 2015-06-24
Hi! I'm new here and I registered just to ask for suggestions in solving this problem.

I have my external HDD and laptop along with a couple of drives infected with a .vbs file. I guess it does nothing but to show an .lnk file, unlike others mentioned elsewhere in the net. However I seek another method in erasing this, hopefully through Ubuntu, since as much as possible I don't want to resort to formatting them. I know it's not that simple as permanently deleting them through Ubuntu. Tried it. Still keeps coming back when I boot up Windows 7. I'm also a fairly new Ubuntu user, so I guess I needed a more detailed approach. Thanks!

---

### Post by dino99 on 2015-06-24
[http://www.openthefile.net/extension/vbs](http://www.openthefile.net/extension/vbs)

as that concern your windows installation, ubuntu have not to push the mess inside it

---

### Post by TheFu on 2015-06-24
Ubuntu can certainly delete the files, but most of those things hide deeper inside the "other" OS. Some put their code in the registry.  So I think the best course of action is to use a Windows AV tool to remove it - boot off another OS - not the infected instance - to remove.   Might be easier to remove the infected disk and connect it to another Windows-running system for AV to remove.

If it cannot be removed that way - reformat. Having an OS that can be trusted as uninfected is the first thing I want. If you have versioned backups, you can just restore to a point prior to the infection. Backups (especially versioned) aren't hard under ubuntu/Linux, so I would assume the same to be true for Windows.

---

### Post by jamesisin on 2015-06-24
You can try loading something like ClamWin on your Ubuntu system and scan the Windows system partitions.  What is happening is the file is being re-created by the actual infection and you need to locate and remove that file as well.

If anti-virus software doesn't seem to be doing the trick, you can try using ComboFix (on Windows):

[ComboFix]("http://jamesisin.com/a_high-tech_blech/index.php/2008/12/combofix-and-the-magic-bullet/")

---

### Post by renscy on 2015-06-24
Yep. That's my problem. For some reason the AV's I downloaded (switched from AVG to Malwarebytes) still don't see it as an infected file.. and even though it's detected (in other computers with different kinds AV's each) it just keeps coming back. By the way, will try your suggestions.. Thanks!

---

### Post by renscy on 2015-06-25
Did the ComboFix. It deleted the autorun.inf in both of my drives, and I took care of the .vbs file using command prompt. Problem is, when I restarted (as recommended,) the trio (.lnk, .vbs and .inf files) is back again, tried deleting again the .vbs and even the .inf files through command prompt but it just says that it doesn't exist. However, I've noticed that when I delete these files in my flash drives through Ubuntu it doesn't come back, unless I plug it to an infected Windows 7, though I can't say for sure when I plug it in an uninfected one. Is there any way of confirming that the virus is gone in my flash drives without reformatting them? My plan is to just delete the virus from the flash drives and the internal drive through Ubuntu, and reinstall Windows, since it's messed up anyways..

---

