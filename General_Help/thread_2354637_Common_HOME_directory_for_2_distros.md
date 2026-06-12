---
title: "Common HOME directory for 2 distros"
date: 2017-03-04
forum: General Help
---

### Post by jf-moniquelevi on 2017-03-04
HI,

I have ubuntuMATE and I wanted to  try lubuntu, to see if my old Thinkpad would perform better.
I am using both OS right now but it is annoying because every file I download, every file I create and save have to be duplicated in the HOME directory of the other OS.  
My 2 HOME directories are in their own partitions, but both can be accessed by either OS.
Having 2 copies of each file uses a lot of space especially photos, I have hundreds of them at 10-15 megs a piece...

I cannot use the same HOME, because of the .config files and others that are specific to the OS.

I was thinking to create a new directory which both OS would use for my files but I don know how to implement it, so that each OS would look at the new common directory.
I am not familiar with links, maybe it would be an option ?

Any suggestions would be welcome, thanks.

---

### Post by T.J. on 2017-03-04
There is no need for a separate home directories, or even separate installations if you are using the same distro release, say for the sake of discussion: 16.04.  Ubuntu Mate 16.04 and Lubuntu 16.04 are the exact same OS, only with a different interface on top. If you want both interfaces, you can have both in a single install. A single Linux install can have multiple graphical interfaces installed at the same time. Then you just pick which session type you want when you log in.

 You can install Lubuntu on an existing Mate install and vice versa.  The same goes for any of the others: Kubuntu, Xubuntu or so on.  It's all much the same thing.  


Usually, "sudo apt-get install  <name>-desktop" will be sufficient.  So if you want to add Lubuntu on your existing Mate install: sudo apt-get install lubuntu-desktop.  Then choose the session on the log in screen.

---

### Post by Bucky Ball on 2017-03-04
> **T.J. said:**
> There is no need for a separate home directories, or even separate installations.  Ubuntu Mate and Lubuntu are the exact same OS, only with a different interface on top. Linux can have multiple interfaces installed at the same time. Then you just pick which you want when you log in.

 You can install Lubuntu on an existing Mate install and vice versa.  The same goes for any of the others: Kubuntu, Xubuntu or so on. For example to install Lubuntu alongside Mate, just execute  "sudo apt-get install lubuntu-desktop" in a terminal.

Yea, this can work. It can also be extremely problematic, cause conflicts and create redundancy, particularly when you start jamming in three or four desktop environments. They all come with defaults and will bloat the system. Your apps menus will be overloaded with things you may never use. ;)

It is easy enough to use the same /home (and /swap) by using 'Something Else' at the partitioning section of the install and marking /home and /swap to 'Use' but make sure you don't have /home ticked to 'Format'. 

The best, and probably most common way nowadays, is to create a big data partition, keep all your personal data there and create symlinks in the /home _*directory*_ created by default in / when you install which link to the folders in the big /data partition. This avoids redundancy, at least with your personal data, and confusion and you can install and link as many installs as you like to the /data partition. 

When you need to back up your data, just back up the /data partition. When you need to reinstall or back up an install, just backup or reinstall to that OS partition.  

Using the data partition method also means your install partitions only need to be about 20Gb, maybe smaller. The rest of the disk can be /data. 

Hope that helps and good luck. ;)

---

### Post by bearlake on 2017-03-05
I have always used 2 or 3 distro with the same Home directory.

At this time I'm using Xubuntu and Lubuntu on this SSD.

---

### Post by markackerman8@gmail.com on 2017-03-08
WOW SYmLinks - here's proof they work perfectly - but I never thought to use it for this reason - brilliant.

I have been using symlinks in a Cutting edge SSD M.2 Laptop with one disadvantage the M.2 is only 512 GB (the price 4 months ago for just the M.2 SSD was ~>$1/GB or >$500 and a TB >$1,000 so tha's why my $2,500 HP Omen decided not to put a larger one in - I digress but FYI, in the last 3-6 months the price of these M.2 ram type SSDs has dropped by at least 50%)

BUt I decided to use an external superfast SSD and dual-boot and have been using SymLinks for my data on an Ext. 2.5" drive, and they have proven to work flawlessly

Just FYI, but for multiple OS's brilliant!

---

### Post by oldfred on 2017-03-08
I have used symlinks for years as I typically have my current LTS as main working install and either the older or next LTS as well as each of the inbetween releases installed. They all use same /mnt/data and after manually doing it several times, I realized I could just script it. I just copied history (after I edited out errors) into bash file.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by jf-moniquelevi on 2017-03-12
> **Bucky Ball said:**
> Yea, this can work. It can also be extremely problematic, cause conflicts and create redundancy, particularly when you start jamming in three or four desktop environments. They all come with defaults and will bloat the system. Your apps menus will be overloaded with things you may never use. ;)

It is easy enough to use the same /home (and /swap) by using 'Something Else' at the partitioning section of the install and marking /home and /swap to 'Use' but make sure you don't have /home ticked to 'Format'. 

The best, and probably most common way nowadays, is to create a big data partition, keep all your personal data there and create symlinks in the /home _*directory*_ created by default in / when you install which link to the folders in the big /data partition. This avoids redundancy, at least with your personal data, and confusion and you can install and link as many installs as you like to the /data partition. 

When you need to back up your data, just back up the /data partition. When you need to reinstall or back up an install, just backup or reinstall to that OS partition.  

Using the data partition method also means your install partitions only need to be about 20Gb, maybe smaller. The rest of the disk can be /data. 

Hope that helps and good luck. ;)

That&#347; exactly what I was thinking; however I am not familiar with "symlinks", need to find a good documentation.
Since I have now 2 /Home dir. ,I should create a big /data partition, move my personal data from my 2 /Home dir. to /data  and them create the symlinks ?

Thank you guys for the suggestions, keep them coming :)

---

### Post by Bucky Ball on 2017-03-12
> **jf-moniquelevi said:**
> 
Since I have now 2 /Home dir. ,I should create a big /data partition, move my personal data from my 2 /Home dir. to /data  and them create the symlinks ?

Yes, but with a caveat. What then do you do with the empty /home partitions? I believe they hold some system data so you can't just delete them. Also, make sure you don't move any system stuff from /home partition to the data partition. Breakage will occur. So, it is not quite as straightforward as it may at first appear. 

You don't need extensive documentation for symlinks; they're easy. The syntax goes like this:

```
ln -s 'location to link to' 'name of symlink'
```

For example:

```
ln -s /media/ExternDrive moreFilesLink
```

You need to replace the path in the above code to match the path for your setup. [See this page for more detail]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html") if required (which is where the syntax explanation came from).

---

