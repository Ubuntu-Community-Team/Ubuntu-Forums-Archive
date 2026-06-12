---
title: "[SOLVED] Removing trash thumb drive"
date: 2008-04-20
forum: General Help
---

### Post by Bubba64 on 2008-04-20
I have a sony thumb drive USM 2gj with a microvault compression feature for windows use.
When I bought it I deleted all the microvault stuff, The built in trash though is now made itself into a root file read only so anything in the trash I can't remove. I have read through some of the other posts on this sort of problem, and I have tried to change the file name to no avail I don't know how to sudo rm this specific drive that would probably do the trick any help would be appreciated.

---

### Post by Bubba64 on 2008-04-20
> **Bubba64 said:**
> I have a sony thumb drive USM 2gj with a microvault compression feature for windows use.
When I bought it I deleted all the microvault stuff, The built in trash though is now made itself into a root file read only so anything in the trash I can't remove. I have read through some of the other posts on this sort of problem, and I have tried to change the file name to no avail I don't know how to sudo rm this specific drive that would probably do the trick any help would be appreciated.

Found the answer in repartitioning with gparted and just highlighting and then shift-delete does the trick on any files I want removed after the repartition.
This link was the key Fat 16 is what I used on my linux computer to get it working.
[http://ubuntuforums.org/showthread.php?t=528615&highlight=delete+thumb+drive](http://ubuntuforums.org/showthread.php?t=528615&highlight=delete+thumb+drive)
This link had the instruction on bringing up the hidden files with crtl-h and deleting with shift-delete
[http://ubuntuforums.org/showthread.php?t=471285](http://ubuntuforums.org/showthread.php?t=471285)

I may have not had to repartition this thumbdrive to get it to work but I also did a sudo rm to the thang in order to clean out that MS stuff. When I first tried to shift-delete I hadn't left clicked on the file to remove so it didn't work but after the sudo and repartition and highlighting with a left click passing over files everything was deleted..

---

