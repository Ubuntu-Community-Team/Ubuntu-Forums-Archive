---
title: "Backup Issues and Restoration Attempts"
date: 2019-08-12
forum: General Help
---

### Post by Shibblet on 2019-08-12
I am looking for a piece of software that will restore my desktop settings and specifications.

I install Kubuntu, and then go through all of the setup and customizations.  Then when I have the desktop and OS configured the way I want, I would like to make a backup of this that I can restore in case I mess something up.

I have tried Clonezilla, and when I restore my image, it messes up Grub, and it won't boot into Kubuntu.  In which case I have to do a complete re-installation of the OS and then reconfigure my settings to get it back to where I was.

Any ideas?

---

### Post by GhX6GZMB on 2019-08-12
Timeshift.
It has rescued me so many times. Using rsync, it'll take a snapshot of your system that includes everything. Even if you crash your HDD/SSD, you can boot from a live DVD, reinstall Timeshift, and re-create your system.

---

### Post by TheFu on 2019-08-12
Any ideas? Sure.

[https://ubuntuforums.org/showthread.php?t=2421171&p=13867057#post13867057](https://ubuntuforums.org/showthread.php?t=2421171&p=13867057#post13867057) is what I think from a question you asked previously
and
[https://ubuntuforums.org/showthread.php?t=2392127&p=13767841#post13767841](https://ubuntuforums.org/showthread.php?t=2392127&p=13767841#post13767841) about the tool I actually use.

Instead of just worrying about personal settings, how about making daily, versioned, backups to protect the entire system from a disk failure?  It isn't much harder and usually doesn't require all that much storage.

aljames2 is working to make a really good daily, versioned, consistent, backup here: [https://ubuntuforums.org/showthread.php?t=2422831](https://ubuntuforums.org/showthread.php?t=2422831)  Both Al and I use LVM, but for your needs, that part can probably be ignored.  I'm happy to help nail down the script for your needs following this example.

---

### Post by Shibblet on 2019-08-12
> **TheFu said:**
> Any ideas? Sure.

[https://ubuntuforums.org/showthread.php?t=2421171&p=13867057#post13867057](https://ubuntuforums.org/showthread.php?t=2421171&p=13867057#post13867057) is what I think from a question you asked previously

Yep, that was me...  I did take your advice and tried Clonezilla, but that causes problems with GRUB when I try to restore and image.
So, I did already start that other thread, but I thought my question had changed enough to start another.  If they are the same, go ahead and nuke the previous thread please.

> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2392127&p=13767841#post13767841](https://ubuntuforums.org/showthread.php?t=2392127&p=13767841#post13767841) about the tool I actually use.

Instead of just worrying about personal settings, how about making daily, versioned, backups to protect the entire system from a disk failure?  It isn't much harder and usually doesn't require all that much storage.

I like that idea.  I am going to give TimeShift a try, and see if it works the way I need it to.  I am assuming if your system crashes, you install Kubuntu, then just run TimeShift and it will load up a previious saved version with all of your settings and software?

> **TheFu said:**
> aljames2 is working to make a really good daily, versioned, consistent, backup here: [https://ubuntuforums.org/showthread.php?t=2422831](https://ubuntuforums.org/showthread.php?t=2422831)  Both Al and I use LVM, but for your needs, that part can probably be ignored.  I'm happy to help nail down the script for your needs following this example.

I tend to shy away from bash scripts, but I will look into it.

---

### Post by GhX6GZMB on 2019-08-12
"[COLOR=#000000]I am assuming if your system crashes, you install Kubuntu, then just run TimeShift and it will load up a previious saved version with all of your settings and software?"[/COLOR]

You don't even need to install *Ubuntu. Run a live DVD, install Timeshift and do the restore. This will bring your system back to life as it was before.

EDIT: Important: your backup media must be formatted as ext4, otherwise Timeshift won't work.

---

### Post by TheFu on 2019-08-13
Don't fear bash.  The scripts are just the commands you would type into a terminal copied into a file.

I've been saved by backups about 1-2 times a year for the last 15+ yrs.  Perhaps 5 times due to disk failures, about 5 times as I moved from 1 system to another or a release upgrade failure, and about 10 times due to my stupidity of deleting files that I still needed.
Testing the restore is the only way to know if your backups do what you need.  Be certain that you test on completely different hardware.  That's the cracked motherboard test.  If you can't restore to a new system, I think the backups aren't good enough.  That's another reason why image-based backups or backups that don't restore to a freshly installed OS don't interest me. 

I've had a laptop stolen in an airport.  Visited the local "big box" store, bought a replacement, then did a fresh Ubuntu install and restore over the network.  

Consider all the possible failures from which you might need to restore.

---

### Post by Shibblet on 2019-08-13
> **ml9104 said:**
> "EDIT: Important: your backup media must be formatted as ext4, otherwise Timeshift won't work.

So, partition off a chunk of my external HD, and format it EXT4?

---

### Post by SeijiSensei on 2019-08-13
All your Kubuntu settings are stored in the directory $HOME/.kde/.

You can create an inventory of installed software using the command "dkpg --get-selections".  If you feed that output to a file

```

cd $HOME
dpkg --get-selections > myselections

```

then you can restore the system using "sudo dpkg --set-selections < myselections".

---

### Post by TheFu on 2019-08-13
Another way to get the list of installed packages, which has a little more control is apt-mark. Both methods work, I've used both, but switched to apt-mark since 16.04.
```

######[ to save the list of pkgs to files ]#######
 apt-mark showauto | tee $local_backup/apt-mark.auto
 apt-mark showmanual | tee $local_backup/apt-mark.manual

######[ to restore pkgs ]#######
### sudo apt-mark auto $(cat apt-mark.auto)
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
```

I only restore the manually installed packages, since those automatically installed will be there or pulled in due to dependencies.  I think this will keep a cleaner, new install, since dependencies might change from release to release.

---

### Post by Shibblet on 2019-08-13
TimeShift looks like it makes a complete image of the drive.  This would be ideal for time saving, and distro-hopping.  Backup your main install, load whatever distro you like... if you prefer your main, reload it from a live USB.  Lather, rinse, repeat as necessary.

---

### Post by GhX6GZMB on 2019-08-13
> **Shibblet said:**
> TimeShift looks like it makes a complete image of the drive.  This would be ideal for time saving, and distro-hopping.  Backup your main install, load whatever distro you like... if you prefer your main, reload it from a live USB.  Lather, rinse, repeat as necessary.

You need to be precise about your requirements. Timeshift is for backups on a single PC. It is not suitable for cross-platform use. And it does not not make a complete image of the drive, for that you'd need DD. But it does make a complete image of the file system.

Timeshift is good if:
you're only working with one PC
you have a stable installation/configuration that you want to keep
you do incremental updates that you want to roll back
you want to feel secure when experimenting on that one PC
you experience a HDD crash

In that case, Timeshift will save you every time, provided you have a live DVD/USB at hand. Then, a rollback can _always_ be done.

If the scenario is, that you have multiple hardware that needs to be be backed up. or you need to transfer your image to new hardware, then Timeshift is the wrong solution.

---

### Post by Shibblet on 2019-08-13
> **ml9104 said:**
> You need to be precise about your requirements. Timeshift is for backups on a single PC. It is not suitable for cross-platform use. And it does not not make a complete image of the drive, for that you'd need DD. But it does make a complete image of the file system.

Sounds Perfect.

> **ml9104 said:**
> Timeshift is good if:
[COLOR="#00FF00"]Check!  [/COLOR] ---- you're only working with one PC
[COLOR="#00FF00"]Check!  [/COLOR] ---- you have a stable installation/configuration that you want to keep
[COLOR="#00FF00"]Check!  [/COLOR] ---- you do incremental updates that you want to roll back
[COLOR="#00FF00"]Check!  [/COLOR] ---- you want to feel secure when experimenting on that one PC
[COLOR="#FF0000"]Hope not...  [/COLOR] ---- you experience a HDD crash

> **ml9104 said:**
> In that case, Timeshift will save you every time, provided you have a live DVD/USB at hand. Then, a rollback can _always_ be done.

Can I make a LiveUSB with Ubuntu, and restore a Kubuntu (Xubuntu, Ubuntu-Budgie, Ubuntu-MATE) image?

---

### Post by Artim on 2019-08-13
I totally love **SystemBack** even better than Timeshift, because it's super-simple.  You can use it to make incremental backups and stuff, but it also makes a bootable copy of your installed OS *and* can also include everything in your /home partition too!  Learn about SystemBack [here]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10").

---

### Post by GhX6GZMB on 2019-08-14
TBH, I did try SystemBack, but it failed me. I used it for a bootable backup on USB and for test purposes did a sudo rm -r / to provoke a crash (which worked perfectly) :)

However, the bootable USB did not work and I lost confidence in SystemBack.

That's why I switched to a live DVD (which always works) and Timeshift for the backup. It has not failed me yet, and I've had several (user-caused) issues that have necessitated a system restore.

---

### Post by Artim on 2019-08-14
Good to know!  It works on fine on my computers but as they say, "Your mileage may vary."

---

