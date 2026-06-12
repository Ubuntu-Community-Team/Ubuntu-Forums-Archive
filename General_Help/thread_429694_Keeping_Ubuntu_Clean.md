---
title: "Keeping Ubuntu Clean?"
date: 2007-05-01
forum: General Help
---

### Post by Old Pink on 2007-05-01
Hi there,

When using WIndows (almost a year ago now) I used to use [CCleaner](http://www.ccleaner.com) (Crap Cleaner) to clean all the "crap" from Windows, temp files, stray files... all the junk.

I know not as much builds up on Linux, if any at all, but I've used 30 Gigabytes of my harddrive now (still not even 40% full) but that's around the amount I vaguely remember Windows having full, with all the crap.

There must be some sort of small build ups I can keep an eye on? :) 

Just looking for a similar program really. Although I do like the Disk Usage Analyzer in Feisty... I'm not really sure what's up for deletion. ;) 

Matt

---

### Post by mcduck on 2007-05-01
Well, you could run 'sudo apt-get clean' every now and then to remove .deb packages that apt caches when you install/update programs.

Also if you feel your some of your disk space is missing check the sizes of log files in /var/log, if there's some problem in your system it could flood some log file with error messages, causing the file to grow very big.

Apart from those, just use the Disk Usage Analyzer to see how your disk space is used.

---

### Post by 50words on 2007-05-01
Other than log files, you won't find much. I run "sudo apt-get autoremove" every now and then for the same reason McDuck mentioned.

---

### Post by mcduck on 2007-05-01
> **50words said:**
> Other than log files, you won't find much. I run "sudo apt-get autoremove" every now and then for the same reason McDuck mentioned.

'apt-get autoremove' removes packages installed as dependencies after the original package is removed from the system. 'apt-get clean' removes cached package files. ('apt-get autoclean' only removes cached packages of programs no longer installed on your system). So they are 3 different things.

You can of course instead just go to /var/cache/apt/archives and remove them yourself, but when there's a single command to do the job why bother doing it by hand? ;)

---

### Post by Old Pink on 2007-05-01
> **mcduck said:**
> Well, you could run 'sudo apt-get clean' every now and then to remove .deb packages that apt caches when you install/update programs.

Also if you feel your some of your disk space is missing check the sizes of log files in /var/log, if there's some problem in your system it could flood some log file with error messages, causing the file to grow very big.

Apart from those, just use the Disk Usage Analyzer to see how your disk space is used.

> **50words said:**
> Other than log files, you won't find much. I run "sudo apt-get autoremove" every now and then for the same reason McDuck mentioned.

Cheers guys, that took off 600MB. 

Running GtkOrphan then took another 100Mb.

Total lost so far = 700Mb

So far so good. :)

---

### Post by stchman on 2007-05-01
> **mcduck said:**
> 'apt-get autoremove' removes packages installed as dependencies after the original package is removed from the system. 'apt-get clean' removes cached package files. ('apt-get autoclean' only removes cached packages of programs no longer installed on your system). So they are 3 different things.

You can of course instead just go to /var/cache/apt/archives and remove them yourself, but when there's a single command to do the job why bother doing it by hand? ;)

So the moral of the story is to run both of them:

sudo apt-get autoremove

&

sudo apt-get clean

That will take care of all the crap.

---

### Post by stchman on 2007-05-01
> **Old Pink said:**
> Hi there,

When using WIndows (almost a year ago now) I used to use [CCleaner](http://www.ccleaner.com) (Crap Cleaner) to clean all the "crap" from Windows, temp files, stray files... all the junk.

I know not as much builds up on Linux, if any at all, but I've used 30 Gigabytes of my harddrive now (still not even 40% full) but that's around the amount I vaguely remember Windows having full, with all the crap.

There must be some sort of small build ups I can keep an eye on? :) 

Just looking for a similar program really. Although I do like the Disk Usage Analyzer in Feisty... I'm not really sure what's up for deletion. ;) 

Matt

That is insane amounts of space for Ubuntu.  I have only used about 7 Gigs for a complete install with all the stuff I use.  Do you do video editing or something with huge files?

What is GtkOrphan?  From the name it sounds like the removal of packages or other software that is no longer needed.

---

### Post by Old Pink on 2007-05-01
> **stchman said:**
> That is insane amounts of space for Ubuntu.  I have only used about 7 Gigs for a complete install with all the stuff I use.  Do you do video editing or something with huge files?

7GB of Music
5GB of Videos

Trash is empty, by the way.

[I][B]Disk Usage Analyzer Screenshot Updated without /media folder due to unnessecary inclusion of DVD/CD.
[/B][/I]

---

### Post by Old Pink on 2007-05-01
> **stchman said:**
> What is GtkOrphan?  From the name it sounds like the removal of packages or other software that is no longer needed.

Exactly that.

Removes left over orphaned configuration files from previous uninstalls.

And removes any orphaned unneeded dependancies.

```
sudo aptitude install gtkorphan
```

[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

---

### Post by mcduck on 2007-05-01
> **Old Pink said:**
> Exactly that.

Removes left over orphaned configuration files from previous uninstalls.

And removes any orphaned unneeded dependancies.

```
sudo aptitude install gtkorphan
```

[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

If you don't feel like getting another app for cleaning things, just install the deborphan package and create a new filter in Synaptic to only show packages with status 'Orphaned'. Then you can clean orphaned packages easily from Synaptic.. (Gtkorphan is just a graphical frontend for deborphan)

---

### Post by adromidon on 2007-05-01
Is there a way to setup maybe Cron to run these tasks on a scheduled basis say once a month to keep the OS completely clean of unused or un-needed files.

---

### Post by Old Pink on 2007-05-02
> **adromidon said:**
> Is there a way to setup maybe Cron to run these tasks on a scheduled basis say once a month to keep the OS completely clean of unused or un-needed files.

I too would be extremely interested in this. :)

---

### Post by stchman on 2007-05-02
> **Old Pink said:**
> Exactly that.

Removes left over orphaned configuration files from previous uninstalls.

And removes any orphaned unneeded dependancies.

```
sudo aptitude install gtkorphan
```

[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

Does gtkoprhan get orphaned packages that clean and autoremove don't get?

---

### Post by stchman on 2007-05-03
Yes, gtkorphan freed up quite a bit of disc space.

Thanks.

---

