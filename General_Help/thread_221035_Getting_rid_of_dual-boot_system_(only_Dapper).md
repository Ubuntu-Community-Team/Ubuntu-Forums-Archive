---
title: "Getting rid of dual-boot system (only Dapper)"
date: 2006-07-22
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-07-22
As recently as a few days ago I was running a dual-boot of XP and Dapper.  Currently I am running just Dapper now and couldn't be happier with my decision.  XP was on the first partition (sda1) of my hard disk though so I converted that to ext3 and use it as a data drive now.

I would like to do a fresh install of Dapper to use my hard disk roughly in the following manner (I have a 100GB disk of which 93GB or so is actually useable):

          sda1 - 15GB - /root
          sda2 - 25GB - /home
          sda3 - 50GB - /data
          sda4 - 3GB - swap

I've read in multiple places that it's smart to have a dedicated /home partition. It allows you to keep all your settings intact and avoid the potential problems of upgrading over a previous install.  However I can't help thinking that even with a dedicated /home partition that you have to reinstall the actual applications after a clean install/upgrade (still seems like quite a PITA to me).

Anyway, I'm asking for the real benefits of having a dedicated /home partition with respect to upgrades/installs and some guidence on how to best set up my partitions (in case there's something I overlooked).  Thanks!

BTW, my computer info:
Toshiba laptop 105A-2716
100GB hard disk
1.73GHz Intel Centrino Proc
1GB RAM
128MB shared video memory

---

### Post by msak007 on 2006-07-22
The home partition contains all of your documents, as well as any user-specific settings (gnome, kde, application configurations, game high scrores, etc.). Having a separate partition makes for easier setup after a reformat or upgrade, because all of your settings are intact. You were right in that you still need to set up all the applications you had before, but when you launch them they'll read the settings from your home directory. 

One of the best examples I can think of to demonstrate this is Firefox / Thunderbird (if you use them). Your home directory contains your profiles for those apps, including any extensions, themes, accounts (in the case of Thunderbird), etc.  If you don't back those settings up, you have to reinstall every single extension and theme you had prior to your format, and re-add all your accounts in Thunderbird (not to mention you'll lose all your emails if you had any downloaded). Now that's a PITA. 

If you want to create a separate home partition, it's a good idea. If you don't, then make sure you at least back up your home directory to another partition or removable storage before you format or upgrade. That way it can be restored after the install and restore all of your user prefs quickly and easily.

As far as your proposed partition layout, what's the /data partition for?

---

### Post by 5-HT on 2006-07-22
> **ThrobbingBrain66 said:**
> However I can't help thinking that even with a dedicated /home partition that you have to reinstall the actual applications after a clean install/upgrade (still seems like quite a PITA to me). 

You could always have a separate partition for /usr.
However, I haven't tried it in practice and I'm not sure what would happen with package management (though I've read some guides that recommend it).

---

### Post by Herman on 2006-07-22
**[B]Personally**[/B], I would not bother going to all the trouble of re-installing with a seperate /home partition for all the tea in China. The single partition '/' (root) plus swap area install is best for most people and that is the default operation of the installer.

       In my opinion, the idea of having a seperate /home partition is rather out of date, and is no longer the best way to preserve data or system settings and added software now that we have more modern software available.
 A better idea is to keep your single '/' partition install now that you have your system all set up. 
Back up and remove all your data to some other media (a USB drive is ideal). We should all be making regular back ups to other media in any case, so that should be no extra work at all.

Then use a [GParted LiveCD]("http://gparted.sourceforge.net/") to resize your current operating system as small as you can. It should be able to be resized to as small as 2 to 2.5 GB after the data is backed up seperately and deleted. 
Use the GParted LiveCD to copy and paste your entire operating system to the end of your hard disk. plus all added software, updates, tweaks, bookmarks and settings. 
Tehn resize your operating system that you are using and restore the data again from the USB drive or other media.
You can fully restore your system (software and settings) from such a back up partition in around ten minutes, plus however long it takes to restore your data. 

When it is time to move to Edgy Eft, you can try upgrading. Sometimes that works and sometimes it doesn't work so well.  I would much prefer a nice clean, fresh install myself. I wll be just installing Edgy beside Dapper, mounting Dapper and transferring my files. Or adding the files to Edgy from my USB drive.
That's my two cents worth, I would hate to see anyone just believing what is popular and what they read without considering more modern alternatives first.
Regards, Herman :D

---

### Post by ThrobbingBrain66 on 2006-07-22
> **msak007 said:**
> The home partition contains all of your documents, as well as any user-specific settings (gnome, kde, application configurations, game high scrores, etc.). Having a separate partition makes for easier setup after a reformat or upgrade, because all of your settings are intact. You were right in that you still need to set up all the applications you had before, but when you launch them they'll read the settings from your home directory. 

One of the best examples I can think of to demonstrate this is Firefox / Thunderbird (if you use them). Your home directory contains your profiles for those apps, including any extensions, themes, accounts (in the case of Thunderbird), etc.  If you don't back those settings up, you have to reinstall every single extension and theme you had prior to your format, and re-add all your accounts in Thunderbird (not to mention you'll lose all your emails if you had any downloaded). Now that's a PITA. 

If you want to create a separate home partition, it's a good idea. If you don't, then make sure you at least back up your home directory to another partition or removable storage before you format or upgrade. That way it can be restored after the install and restore all of your user prefs quickly and easily.

As far as your proposed partition layout, what's the /data partition for?

The data partition that I'm proposing is for various things...music, video, any kind of documents whether they be for school or work and whatever else I can think of.

btw, thanks for all opinions!

---

