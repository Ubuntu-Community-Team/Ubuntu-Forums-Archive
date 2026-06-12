---
title: "Can't access documents through places"
date: 2008-05-22
forum: General Help
---

### Post by Despot Despondency on 2008-05-22
Hey. 

My ubuntu system has been working fine for the last couple of months and then today I've started to have some problems. 

I was browsing through some files, then I selected one of my music folder I got an error saying that not all of the contents could be displayed. 

After that I couldn't use any of the shortcuts in the places menu. If I try to access the Home Folder, for example, it will seemingly do nothing and then a couple of minutes later a small blank window will appear. 

I restarted the computer and everything was fine again for awhile and then the same error returned. 

Any ideas what it could be? I'm using gutsy btw.

---

### Post by danwood76 on 2008-05-22
Sounds like your home folder is dissapearing somehow. (or maybe gnome is forgetting it somehow)
Is it on a seperate partition to your main linux partition?

---

### Post by Despot Despondency on 2008-05-22
I have it on a separate partition. I forgot to mention in the last post that the quit option in the system menu also stopped working. I don't know if they are related but they happen around the same time.

---

### Post by danwood76 on 2008-05-22
It might be that the partition is unmounting for some reason, this may cause issues with the log off screen as I think some of its options are stored on the home dir.

When it does it can you navigate to your home directory through the terminal and list the files there?

```

cd ~/
ls

```
The above commands should list the files in your home directory.

---

### Post by Despot Despondency on 2008-05-22
Hey, thanks for your response. I will try that if the error occurs again. Wouldn't know how to recreate it because I wasn't doing anything in particular at the time. 

If it doesn't list the files does that mean that I have to remount the partition? I know how to mount partitions and so on, so that would be fine, but is there a way of preventing it in the future?

---

### Post by Damiox on 2008-05-30
im having the same problem....was moving things from another hard drive...then whent back to check them and it gave me that error....im using nautilus in root to access them but i cant regular......this is not good,im a musician and i do not need to lose those files.....i tried adjusting the permisions on my home dir  but that hasnt changed anything....nothing will open from the menu.....the hard drive i was pulling from was a win xp ridden with virus's and spyware...the original user was using Kazza..i wonder if any win virus could even effect a linux box...maybe this is the effect...???

its all on the same partion....a 40 gb...with 1 gb ram, 1 gb swap ,2gb 32 bit processor...ubuntu 7 ...

---

### Post by danwood76 on 2008-05-30
@Despot

To remount your home you simply do:
```

sudo mount /home

```
Though I'm unsure as to why the home partition is being unmounted.
In another thread someone was having issues where some remote desktop software (not ubuntus Remote Desktop sw) was blocking access to his home dir.

@Damiox

When you say you've adjusted the permissions what have you exactly done?

In the terminal can you post the output of:
```

sudo ls -al ~/

```
This will list all the permissions and owners/groups of the files in your home folder so we can verify if its a permissions issue.

---

