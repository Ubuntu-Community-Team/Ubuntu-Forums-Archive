---
title: "Unable to save files in home area"
date: 2014-02-26
forum: General Help
---

### Post by hkgangwar on 2014-02-26
Hello,
From last few days, I am not able to save files even in my home area. I can create and save files through "vi" but not through Gedit/libreoffice (all dropdown menus are not activated). I checked permission of my home area, I am owner and have read/write/exe permission. However I can save files if I open libreoffice as sudo. I am using ubuntu 13.10 64 bit.
Please help me.
Thanks

---

### Post by bc.haynes on 2014-02-26
You need to use **gksudo** with gedit.

---

### Post by hkgangwar on 2014-02-26
Thanks,
But why I need root permission to edit document in my home area. I am not trying to edit system file, just normal day to day use files.

---

### Post by andrew.46 on 2014-02-26
Sounds very odd, can you give the results of the command in red:

```

andrew@corinth:~$ **[COLOR="#FF0000"]ls -l $HOME[/COLOR]**
total 56
drwxr-xr-x 2 andrew andrew 4096 Feb 27 05:27 Desktop
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Documents
drwxr-xr-x 2 andrew andrew 4096 Feb 10 12:41 Downloads
drwxr-xr-x 2 andrew andrew 4096 Jan 10 15:10 dwhelper
-rw-r--r-- 1 andrew andrew 8980 Jan 10 12:33 examples.desktop
drwxr-xr-x 3 andrew andrew 4096 Jan 13 17:46 l-smash_build
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Music
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Pictures
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Public
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Templates
drwxr-xr-x 2 andrew andrew 4096 Jan 10 12:54 Videos
drwxr-xr-x 8 andrew andrew 4096 Feb 27 05:30 vlc_build
andrew@corinth:~$ 

```

The results should be similar to mine (the username will be different of course).

---

### Post by hkgangwar on 2014-02-26
Thanks. 
Here is the out come of ls -l $HOME
drwxr-xr-x 11 hemantk hemantk 36864 Feb 26 10:40 BNC
drwx------  4 hemantk hemantk 12288 Feb 14 13:50 codes
drwxr-xr-x  2 hemantk hemantk  4096 Feb 26 16:30 Desktop
drwxr-xr-x 23 hemantk hemantk  4096 Feb 24 12:29 Documents
drwxr-xr-x 23 hemantk hemantk 12288 Feb 26 15:47 Downloads
drwx------ 10 hemantk hemantk  4096 Feb 26 16:08 Dropbox
drwx------  9 hemantk hemantk  4096 Feb 14 15:59 gv5
drwxr-xr-x  2 hemantk hemantk  4096 Dec 24 16:17 iisc
drwxr-xr-x  3 hemantk hemantk  4096 Nov 12 10:59 intel
drwxr-xr-x  2 root    root     4096 Nov 11 17:50 isus
drwxr-xr-x  2 hemantk hemantk  4096 Nov 15 16:39 lammps
drwxr-xr-x  9 hemantk hemantk  4096 Feb 21 16:31 mele_soln
drwxrwxr-x  3 hemantk hemantk  4096 Dec  3 11:13 mlg
drwxr-xr-x  2 hemantk hemantk  4096 Jan 13 16:35 penn
drwxr-xr-x  2 hemantk hemantk  4096 Jan 17 14:22 Pictures
-rw-rw-r--  1 hemantk hemantk   619 Jan 12 17:57 ref.m
drwx------  9 hemantk hemantk  4096 Feb 11 15:18 scripts
drwxr-xr-x 11 hemantk hemantk  4096 Feb 21 16:22 softwares
-rw-rw-r--  1 hemantk hemantk  1464 Feb 19 20:14 strain_new.f90
drwxr-xr-x  9 hemantk hemantk 40960 Feb 25 16:51 tau_simu
drwxrwxr-x  3 hemantk hemantk  4096 Nov 12 12:04 Ubuntu One
drwxr-xr-x  4 hemantk hemantk  4096 Jan 17 13:37 VirtualBox VMs

---

### Post by deadflowr on 2014-02-26
> all dropdown menus are not activated

Do you not have global menus?

All menus are placed along the top left of the top panel.
They hide until you press alt-key, or push the cursor across the panel.

I'm hoping this is known to you,  but maybe it isn't.

---

### Post by hkgangwar on 2014-02-27
@deadflowr, I have global menu but they are not activated (faded ). Please see the attachment.

---

### Post by hkgangwar on 2014-02-27
It seems like, I have somehow messed up the executable. As I can still change file-name, move them etc. but not edit with programs. Can anyone tell me what is the current permission for the /usr/bin/ directory. I have " lrwxrwxrwx 1 root root"
Hope it will help someone to resolve my problem.

---

### Post by deadflowr on 2014-02-27
> **hkgangwar said:**
> @deadflowr, I have global menu but they are not activated (faded ). Please see the attachment.

?

If global menus are active, but unreadable, you can still use the HUD function to call the appropriate menu item.
In this case, press alt, then type "save as" and the save as function will show up.

---

