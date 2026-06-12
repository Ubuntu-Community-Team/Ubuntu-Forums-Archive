---
title: "Transfering files from ntfs to a linux partion using 2 computers?"
date: 2006-09-28
forum: General Help
---

### Post by deathrunner on 2006-09-28
I am new to linux but not a newbie plus I know windows realy good. I did a good search and could not find my answer. I have 2 computer that I am going to do a fresh install to because I have just got a new hard drive for my main computer and the old ones are going to my secondary computer.

I would like to know how I could transfer the files I would like to save over to my main computer, main computer will have the newest Ubuntu on it the other will have what ever is need to transfer the files over then probably win xp on it after words. Currently the old hard drive are ntfs. I like to know how to do it over my Lan the easiest way if possible.

Oh and what would be the best or easiest partions to use on linux to deal with the tranfers of my files?

P.S. I am trying to go totaly linux but because of the huge amout of file I have I just have not had the storage space untill now to do it.

---

### Post by louis_nichols on 2006-09-28
You can do plain old file sharing the windows way by using samba. It works great!

Just install samba, then go to System>Administration>Shared folders and share the files and folders you want. Then they'll just show up in windows under network neighbourhood.

Samba requires some configuring to do (security settings, access rights etc.). You can find info about that [here]("https://help.ubuntu.com/community/SettingUpSamba"). Good luck!

---

