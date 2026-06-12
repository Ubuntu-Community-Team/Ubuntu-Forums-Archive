---
title: "What is this subfolder in .thumbnails?"
date: 2013-07-09
forum: General Help
---

### Post by vasa1 on 2013-07-09
Context: I'm on Lubuntu 13.04 which I modified somewhat by using Thunar as file manager and the Xfce desktop as described [here]("http://askubuntu.com/a/73101/25656"). I mention this because I don't know if what I'm seeing is restricted to Lubuntu 13.04 or whether it's because of the changes to file manager/desktop or something else that I did unknowingly.

When I run **ls -lR ~/.thumbnails** (after deleting the non-folder contents), this is what I see:

```
[11:02 AM] ~ $ ls -lR .thumbnails
.thumbnails:
total 332
drwx------ 3 vasa1 vasa1  20480 Jul  9 11:02 large
drwx------ 3 vasa1 vasa1 315392 Jul  9 11:01 normal

.thumbnails/large:
total 4
drwx------ 2 vasa1 vasa1 4096 May 13 22:30 00000000000000000000000000000000.png

.thumbnails/large/00000000000000000000000000000000.png:
total 0

.thumbnails/normal:
total 4
drwx------ 2 vasa1 vasa1 4096 May 13 22:30 00000000000000000000000000000000.png

.thumbnails/normal/00000000000000000000000000000000.png:
total 0
[11:02 AM] ~ $ 

```
My question is this: if the "00000000000000000000000000000000.png" folders aren't a consequence of my messing up, what is their role? Whenever I look, they're always empty.

---

### Post by Bashing-om on 2013-07-09
vasa1;
Appears something is hosed up for sure.. do not know how else to help except show my output. 13.04/xfce4:
> 
 total 688
-rw-rw-r-- 1 sysop sysop  4909 May 27 16:00 01693dbdcea6a8fc4dc2b4db9283b87a.png
-rw------- 1 sysop sysop  8274 May 22 11:38 02dbe085191716d9106a17cee2993064.png
-rw-rw-r-- 1 sysop sysop  8088 May 27 15:58 02f03513839ac37ce95086b838b50fef.png
-rw------- 1 sysop sysop  9775 May 29 02:50 04fdb171973a486b26248217b6231b48.png
-rw------- 1 sysop sysop  5997 May 22 11:38 0731c503b2dd81c5a29f8c79ae9f8e7a.png
-rw-rw-r-- 1 sysop sysop  9256 May 27 16:00 0959f3468fbeb94aeba415f6f5a05426.png
-rw-rw-r-- 1 sysop sysop  8145 May 27 16:00 1043638ffef196f71d35cd473d457da3.png
-rw------- 1 sysop sysop  8043 May 29 02:50 106673f7596e3246ccc349b06c56533c.png
-rw------- 1 sysop sysop 14041 May 29 02:50 13ab2303c5ad25991137bff0563318cb.png
-rw-rw-r-- 1 sysop sysop 10090 May 27 15:58 1d7c4ca48eabce8baecdd6b90f9b9aac.png
-rw-rw-r-- 1 sysop sysop  7412 May 27 15:58 2731f289d8eb8d343c78907f1b731989.png
-rw-rw-r-- 1 sysop sysop  3360 May 27 16:00 2c0d6d283bae1758559d3f39f5363fcc.png
-rw-rw-r-- 1 sysop sysop  9343 May 27 16:00 2d73939148891500a28bd1afd8ab6d8c.png
-rw------- 1 sysop sysop 10644 May 29 02:50 32812d3a2bcfa6152088d232b4cd5924.png
-rw-rw-r-- 1 sysop sysop  6088 May 27 15:58 3498377f690675e3eaf841d3639d92a9.png
-rw------- 1 sysop sysop  8960 May 29 02:50 38ae21af79efe90bae7933ed1fc45817.png
-rw-rw-r-- 1 sysop sysop  6764 May 27 16:00 39b849aac07328815f42438ab19e08f2.png
-rw-rw-r-- 1 sysop sysop  3202 May 29 02:50 3a67a523207609ab9422f4ab8be7ac77.png
-rw-rw-r-- 1 sysop sysop 11490 May 27 16:00 4683f1b7ec2e56d40aac72e0cc218a2d.png
-rw------- 1 sysop sysop  5528 May 22 11:38 471949b027d455837a14da9f521c4345.png
-rw-rw-r-- 1 sysop sysop 11487 May 27 15:58 47d1c37c5aaa1d5dca6bc60a32a4f45e.png
-rw-rw-r-- 1 sysop sysop  6382 May 27 15:58 4be1e5b750d2f7011011844b4363dc53.png
-rw-rw-r-- 1 sysop sysop 14490 May 27 16:00 5aa1ede1a07ed891f715617763673b36.png

--and more similar


I note the permissions differ (??).
[INDENT][INDENT]hope this helps somewhat[/INDENT][/INDENT]

---

### Post by vasa1 on 2013-07-09
Thanks for replying but don't you have any subfolders? I have "normal" and "large".

---

### Post by Bashing-om on 2013-07-09
vasa1;
Nope .. not in my fairly new install... only a few mods made.
> 
sysop@1304mini:~$  ls -lR ~/.thumbnails
/home/sysop/.thumbnails:
total 4
drwx------ 2 sysop sysop 4096 May 30 19:37 normal

/home/sysop/.thumbnails/normal:
total 688
-rw-rw-r-- 1 sysop sysop  4909 May 27 16:00 01693dbdcea6a8fc4dc2b4db9283b87a.png
-rw------- 1 sysop sysop  8274 May 22 11:38 02dbe085191716d9106a17cee2993064.png
-rw-rw-r-- 1 sysop sysop  8088 May 27 15:58 02f03513839ac37ce95086b838b50fef.png

for reference:
> 
sysop@1304mini:~$  ls -la ~/.thumbnails
total 12
drwxrwxr-x  3 sysop sysop 4096 May 22 11:38 .
drwxr-xr-x 21 sysop sysop 4096 Jul  9 10:11 ..
drwx------  2 sysop sysop 4096 May 30 19:37 normal
sysop@1304mini:~$ 


[INDENT][INDENT]not much help, but[/INDENT][/INDENT]

---

### Post by vasa1 on 2013-07-10
I just deleted the contents of .thumbnails completely. Now, I don't have the "large subfolder"; the normal subfolder was recreated after a while and it doesn't doesn't have that funky 0*.png subfolder. I'm suspecting that what I saw was a hangover from my previous file manager, PCManFM.

---

