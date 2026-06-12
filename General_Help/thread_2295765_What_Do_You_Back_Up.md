---
title: "What Do You Back Up?"
date: 2015-09-21
forum: General Help
---

### Post by Adler on 2015-09-21
Hi All,

I use a Backup app called [KBackup]("https://www.maketecheasier.com/linux-application-review-kbackup/") to do my periodic backups. This tool is pretty straight forward. The files that I backup are: Documents, Downloads, Music, Pictures, and Video. I also have a few Folders that I have created myself e.g. Art, and my Shared Virtualbox files.

I also backup my .mozilla, and .thunderbird files. After a fresh install I can then delete the .mozilla, and .thunderbird files from the new install, and drop in my backups to restore all passwords, e-mail settings, etc.

There is an endless variety of files that I've never bothered with, that I could backup e.g. PlayOnLinux's Virtual Drives, .googleearth, etc. At one time I did also backup my /etc/apt/sources.list. That way I had a list of the repos, and ppas, that I'd installed.

Any thoughts on what would make sense to *really* backup files in order to make that new, fresh install, that much easier?

Thanks in advance for any thoughts.

Adler[I]
Down On The Jersey Shore[/I]

---

### Post by tgalati4 on 2015-09-21
Your list pretty much covers it.  It helps to perform a:

```
dpkg --get-selections > my_currently_installed_packages.txt
```

And back up that list as well.  Then you can apply that file to the new installation:

[http://askubuntu.com/questions/124315/how-can-i-filter-dpkg-get-selections-to-just-packages-available-in-repositor](http://askubuntu.com/questions/124315/how-can-i-filter-dpkg-get-selections-to-just-packages-available-in-repositor)

Some other hints:  [http://askubuntu.com/questions/101931/restoring-all-data-and-dependencies-from-dpkg-set-selections](http://askubuntu.com/questions/101931/restoring-all-data-and-dependencies-from-dpkg-set-selections)

Understand that if you upgrade to a newer version from 14.04 to 16.04 for instance, that list of packages may not be helpful because libraries are frequently changing, renamed, rebundled, etc.  So trying to apply a 14.04 package list to 16.04 may not work as well as you think.

If you want a second system that mirrors your current setup, you can rent some cloud space and set up an identical virtual system, or grab another machine from the pile and make a second machine with a similar setup.

Make a list of recovery scenarios that you expect to be prepared for.  Then write out the procedures for each recovery scenario and the files required.  Make sure you have backups for those files. 

You could set up a RAID1 mirror or install a second drive and simply clone it every 6 months or every 3 months.  Having a separate NAS to store work files and backups is helpful, then any working computer can access those files.

How often do you expect to perform a fresh installation?

---

### Post by ian-weisser on 2015-09-21
I keep a directory of all customizations (and copies of them, with documentation on how to install/remove them) in my /home. Including crontabs, custom /etc config files, etc. Makes backups very easy, and it's a handy archive of my old tips and tricks.
But I don't customize too much anymore. Rode that horse for years until it got old.

I find annual clean installs handy for clearing out unused applications and customizations and helping me identify what I still use.
I don't bother backing up packages and applications - apt makes installing them again at first need trivial...and the list of stuff I haven't needed to reinstall after all is very long.

---

### Post by ajgreeny on 2015-09-21
I keep a very good incremental backup of my /home partition only, using rsync to an external hard drive formatted to ext4 to avoid permission problems.  I don't bother with anything else as it is so quick to re-install if needed.

I have found in the past that I am often too keen to install packages that then sit on my system but never get used, so now tend to wait and install applications when I find that I need them.

Like ian-weisser above, I have a lot of short notes with information on specific configurations I have made to installed applications, but as most configurations are in /home, I have seldom needed them so far.

---

### Post by Adler on 2015-09-21
Hi All,

I'd like to thank all for those interesting, and important thoughts.

> I keep a very good incremental backup of my /home partition only, using  rsync to an external hard drive formatted to ext4 to avoid permission  problems.

ajgreeny - I've been looking into going into the rsync direction, and - in fact - will be wiping / formating a 500Gb drive just for that purpose this evening. And, I do know those *permission* problems all too well!

> How often do you expect to perform a fresh installation?

tgalati4 - Well, if I don't drop, get caught in the rain with my Notebook every 6 - 7 months. I am now only installing LTS versions. I gave up distro hoping / keeping up will everything new about 1 year ago. 

> But I don't customize too much anymore. Rode that horse for years until it got old.


ian-weisser - I am still addicted. Wanna' see my cool icons, wallpapers, cursers, themes, etc., etc.? LOL!

Thanks again to all.

Adler
*Down On The Jersey Shore*

---

