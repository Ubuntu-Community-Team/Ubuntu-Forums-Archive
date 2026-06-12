---
title: "Configuration files in /home/user"
date: 2007-05-07
forum: General Help
---

### Post by ggaaron on 2007-05-07
Many programs after installation make a /home/user/.program directory to store configuration files there. Is there a way to delete all folders that are no longer needed after package's removal? Because growing amount of trash in home folder is really annoying=(

Aaron

---

### Post by FluffyElmo on 2007-05-07
I think if you select a package for "Complete Removal" in Synaptic it removes the configuration files as well. For programs you've already un-installed you can just delete the directory, Ctrl-H in nautilus will show and let you delete hidden directories.

---

### Post by ggaaron on 2007-05-07
Unfortunately complete removal, or dpkg --purge does keep the directories. I know, that I can delete this folders manually, but I fear removing some configuration files that are actually needed...

---

### Post by fakie_flip on 2007-05-07
sudo apt-get --purge remove packagename

Doing a fresh install of Ubuntu once in a while helps keep your system clean of trash. I always install a fresh copy of Ubuntu when a newer release comes out instead of upgrading. There's a lot of bugs with upgrading anyways.

---

### Post by ggaaron on 2007-05-07
I use fresh installs too.

No luck with apt-get --purge remove, what am I doing wrong? The folder still exists, while it shouldn't?

---

### Post by fakie_flip on 2007-05-07
I sometimes delete them manually after I remove a porgram. If they weren't there before the program was installed, then they don't need to be there after the program is gone.

---

### Post by fakie_flip on 2007-05-07
For example after doing 

sudo apt-get --purge remove wine

I do

rm -rvf ~/.wine

---

### Post by fakie_flip on 2007-05-07
I guess the files are there incase you ever install the program again. Then you still have your settings. If you really need to clean up all those dot files, but don't know which ones you should remove, you could create a new user. Then move all of your files that you want to keep over to that users home directory. Then remove the old user, and his home directory will be gone. When you create the new user, only the dot files that you really need will be there. If you accidently delete the wrong dot file like .bash_profile, .bashrc, then you could be in trouble.

---

### Post by ggaaron on 2007-05-07
So I assume that there is no tool for doing this? It's quite sad, that every linux gets crowded after some time, and nothing can be done about this.

---

### Post by intruder13 on 2007-05-07
> **ggaaron said:**
> So I assume that there is no tool for doing this? It's quite sad, that every linux gets crowded after some time, and nothing can be done about this.
Maybe you could try renaming the files to a ".backup" and if nothing happens after a while, delete them?

---

### Post by mannheim on 2007-05-07
For clarifiction, things like "Complete Removal" in synaptic and the "--purge" option in apt-get only remove the **system-wide** configuration files and customizations - things that are stored, for example, in /etc/.

It's usually pretty easy to recognize which programs a "dot" file belongs to when you see ".picasa" or ".gimp-2.2". And generally, if I don't know what it is, I don't delete it!

---

### Post by ggaaron on 2007-05-07
Then using apt-get without --purge leaves some files behind? As you said in /etc where I won't probably search for unused configuration files?

---

### Post by fragos on 2007-05-07
If you do delete a configuration file you didn't want to, many packages will create a new one when they run.  You will of course loose any customization you'd done.  When a package stops running properly dleteing the old configuration file can be a way to correct the problem.

---

### Post by mannheim on 2007-05-08
> **ggaaron said:**
> Then using apt-get without --purge leaves some files behind? As you said in /etc where I won't probably search for unused configuration files?

Yes. The package system distinguishes between (at least?) two types of files that a package may install: first, the regular files that a package installs; and second, the files that are "configuration" files. The idea is that the configuration files are files that the owner of the machine might want to customize (these would be system-wide customizations). For example, anyone who installs the apache web server is obviously going to customize something. When a package is removed, the files marked as config files are not removed, unless the package is atually "purged". That way, the user can reinstall the package later, or install a new version, and carry on.

---

### Post by Boelcke on 2007-05-08
fakie_flip, you mentioned that you do a complete install, rather than an upgrade.  I've got a dapper machine whose upgrade from Breezy to Dapper didn't go 100% flawlessly.  I'd like to do a fresh install of Edgy.

How do I do that, and retain the stuff in my /home partition?

---

### Post by fakie_flip on 2007-05-09
If you created two partitions, then it will be easy. If not find another place to backup your files before installing fresh such as blank dvds, another computer over the network, or an external harddrive, and create two partitions next time you install Ubuntu, so you can do this. To do what you want, you should have two partitions, one that mounts at / and the other that mounts at /home. Let Ubuntu install on the partition that mounts at / and format that partition. Do not format the partition that mounts at home. Formatting erases everything. Make sure it does not format, and your files should still be there after doing a fresh install. Instead just make it mount at /home again when using manual partitioning. Do not use automatic partitioning for this. There is also a swap partition, so you should have three partitions total. You can keep your swap partition and use it again.

---

### Post by fakie_flip on 2007-05-09
If you only have one partition, you could try resizing that partition and creating another using a gparted live cd. Do all of this at your own risk though. I'm not responsible if you lose something because of a bug in an installer, accident, or any reason. People always say you should have a backup of files you can't afford to lose before trying any of this.

---

