---
title: "Hidden Files?"
date: 2021-12-11
forum: General Help
---

### Post by sniper8752 on 2021-12-11
I am using syncthing to backup my photos.  I recently noticed that some files were not showing up.  Long story short, after spending much time on this, I found out that some images are showing up as "hidden".  Here is one of them:
```
[FONT=monospace][COLOR=#000000]-rwxrwxrwx 1 syncthing syncthing  1.3M Dec 11 14:32 [/COLOR][COLOR=#ff5454]**IMG_20211211_093233.jpg**[/COLOR]
[COLOR=#000000] [/COLOR][/FONT]
```
When I think of "hidden", I think of a file having a "." in front of it.  But that doesn't seem to be the case here.  What property is causing me to have to do "Show Hidden" in the file explorer?

---

### Post by HermanAB on 2021-12-11
It is not hidden.  It is marked as executable.

---

### Post by sniper8752 on 2021-12-11
In Dolphin, I select Show Hidden, and there are more files in this name format.  When I don't show hidden, there are less.

---

### Post by The Cog on 2021-12-11
What filesystem are the files on? 
Can you show the output of ls -l and include a file that is "hidden" and one that is not "hidden" (for comparison)?

---

### Post by sniper8752 on 2021-12-12
sda/sda1 is [FONT=monospace][COLOR=#000000]crypto_LUKS, and the directory is ext4. 

The following is a file NOT hidden:
[/COLOR][/FONT][FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]-rwxrw-rw- 1 [FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]user[/COLOR][/FONT][/FONT][/FONT] [FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]user[/COLOR][/FONT][/FONT][/FONT] 4866187 Apr 10  2021 VID_20201101_185421.mp4[/COLOR]
[/FONT][/FONT]
The following IS hidden: [FONT=monospace]
[FONT=monospace][COLOR=#000000]-rwxrw-rw- 1 user [/COLOR][/FONT][/FONT][/FONT][FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]user[/COLOR][/FONT][/FONT][/FONT] 823515 Nov 19 14:58 IMG_20211119_145824.jpg[/COLOR]
[/FONT][/FONT][/FONT][FONT=monospace][/FONT]

---

### Post by yetimon_64 on 2021-12-12
> **sniper8752 said:**
> ...When I think of "hidden", I think of a file having a "." in front of it....
The ls output you show has no indication of the JPG file being hidden, but there is another way files can be hidden in Linux without the "." in front of the file name. Look for a txt file called ".hidden" in the folder that the JPG file is held in. If there is a ".hidden" file in the folder open it with a text editor; the filename (including the file extension) should be listed there. Remove/delete the file name entry from the text file or simply delete the .hidden file altogether to show all files.

I've never heard or seen any program using the ".hidden" text file method of hiding files before though, seems a bit unusual.
Good luck, yeti.

---

### Post by sniper8752 on 2021-12-12
There is no .hidden text file.

---

### Post by yetimon_64 on 2021-12-12
> **sniper8752 said:**
> There is no .hidden text file.
Ok. I don't know of any other means of hiding files besides the ".filename" or the ".hidden" text file. Wait for further help/suggestions from others here. Cheers.

---

### Post by HermanAB on 2021-12-13
There are other ways to fool you:
ACLs
SELinux
AppArmor

---

### Post by sniper8752 on 2021-12-13
sestatus doesn't do anything, and apparmor has been disabled.  They are still hidden.

---

### Post by TheFu on 2021-12-13
> **sniper8752 said:**
> sestatus doesn't do anything, and apparmor has been disabled.  They are still hidden.

Check the ACLs on all the files.
I've never heard of any software using it.  I don't use sync-whatever, so I don't know what it does.

I did check the **attr**, **lsattr** and **chattr** manpages. Didn't see anything there, but it would be worth having a look to double check.
I didn't check the **setfacl** and **getfacl** manpages. An exercise for the reader. I don't think they hide anything. Just the .file method is the only one that I know outside normal permissions which would happen at a directory level.

---

