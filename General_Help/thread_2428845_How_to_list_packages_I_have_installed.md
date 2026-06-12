---
title: "How to list packages I have installed?"
date: 2019-10-10
forum: General Help
---

### Post by orthoducks on 2019-10-10
With emphasis on "I": what packages have *I*, and not a piece of software, installed?

I want a list of packages I have installed on one system so I can duplicate my work on another system. The lists I can get with "apt list" or "dpkg --get-selections" include dozens of packages that are either installed with Ubuntu or are installed as dependencies of packages I installed. I don't want to list those; how can I eliminate them?

---

### Post by dragonfly41 on 2019-10-10
One simple way .. run command

```
history | grep install
```

but you might have duplicates so possibly pipe this output to a file to be parsed..

And you could explore Aptik in System Tools.

---

### Post by Impavidus on 2019-10-10
You could use```
[s]apt-mark manual[/s]
apt-mark showmanual
```That won't show the packages that were installed as dependencies, but will show many packages that were installed with the OS. On a different, freshly installed Ubuntu system, these same packages are already installed and marked as manual, so that might not be a problem.

You can check your command line history as suggested above, but that will miss packages not installed by terminal and the history only goes back 1000 commands by default. Or you could check old log files. /var/log/dpkg.log* goes back one year, which may be long enough to go back to your last fresh install.```
# For the uncompressed log files:
grep " install " /var/log/dpkg.log
grep " install " /var/log/dpkg.log.1
# For the compressed log files:
zcat /var/log/dpkg.log.2.gz | grep " install "
# etcetera
```It doesn't mention whether the packages were automatically or manually installed, but at least it won't show the packages installed along with the operating system. So find the packages listed by both commands, those are the ones manually installed.

---

### Post by &amp;KyT$0P# on 2019-10-10
Does [this script]("https://ubuntuforums.org/showthread.php?t=2355157&p=13618967&viewfull=1#post13618967") do what you're looking for?

---

### Post by TheFu on 2019-10-11
> **orthoducks said:**
> With emphasis on "I": what packages have *I*, and not a piece of software, installed?

I want a list of packages I have installed on one system so I can duplicate my work on another system. The lists I can get with "apt list" or "dpkg --get-selections" include dozens of packages that are either installed with Ubuntu or are installed as dependencies of packages I installed. I don't want to list those; how can I eliminate them?

Packages are installed using either sudo or root accounts.  It is unlikely with 100% certainty the system can tell that YOU were typing, not anyone else.

```
sudo apt-mark showmanual
```
is what I use in my backup scripts to know which packages I need to install during the restore process.  I can't be 100% certain that "I" installed them, but someone with admin rights did.
BTW, the option is "showmanual", which is certainly what Impavidus meant.  Sometimes I forget the exact option too and have to check the manpage.

If you really want to know which you installed, keep a text file with that information.  Would be interesting to compare your manual log with the apt-mark list after some time.

---

### Post by orthoducks on 2019-10-13
I've tried impavidus's second suggestion (grepping from dpkg.log) so far, but the results do not make sense.

To find out what has been added since installation I grepped the logs from my system and an Ubuntu Live system and diffed the two. The diff shows a clear division; everything up to line 1795 is identical, everything beyond that point has a different date and is in my list only. But none of the additional entries look familiar, and packages I know I've installed (e.g. gparted) are not there.

impavidus, if you can suggest what may have gone wrong I'll try again. Meanwhile I'll try later suggestions.

A note to TheFu: I neglected to say explicitly that no one else uses my Ubuntu machine, so "who installed something?" is not an issue; only whether Ubuntu itself installed it, or I did.

---

### Post by TheFu on 2019-10-13
> **orthoducks said:**
>  
A note to TheFu: I neglected to say explicitly that no one else uses my Ubuntu machine, so "who installed something?" is not an issue; only whether Ubuntu itself installed it, or I did.

```
sudo apt-mark showmanual
```
is the answer if there's only 1 admin.

My backup script (perl) contains these lines to deal with manually installed packages through any APT front-end:
```
 `$aptmark showauto | tee $local_backup/apt-mark.auto`;
 `$aptmark showmanual | tee $local_backup/apt-mark.manual`;
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
```

Clearly, the list of packages file needs to be in the stuff backed up.  Then at restore time, use those other commands.

---

### Post by Impavidus on 2019-10-13
I don't know if the packages installed during Ubuntu install are listed in /var/logs/dpkg.log*, but apparently so. The logs go back one year, but I haven't done a fresh install in almost three. Everything installed later must be installed by you or as a dependency.

I don't see what you diffed exactly, but keep in mind that what's present on a live disk is not the same as what's present on a freshly installed Ubuntu system. For example, gparted is present on the live disk, but not on a freshly installed Ubuntu, so I'm not surprised it's not in your diff.

Most of the packages installed later are dependencies of other packages, so they may sound unfamiliar. That's why I suggest you compare it to the list of packages marked as manually installed.```
grep -Ff <(apt-mark showmanual) 'file with everything from the log files after install' >'file with manually installed entries from log files'
```

Anyway, if it's to get a list of packages you have to install on a different system to make it identical to your first, listing the packages that were installed along with the OS won't harm. They are on the target computer already, assuming that's an Ubuntu system too.

---

### Post by orthoducks on 2019-10-14
Impavidus, I realize that Live Ubuntu has a different set of applications than a fresh installation. That shouldn't matter. Take GParted as an example. As you said, it's available on Live Ubuntu but initially not on a freshly built system. Therefore *it will appear in a diff* because there is an entry for it in Live Ubuntu's log that isn't in the installed system's log.

Now suppose the user has installed GParted on his no-longer-quite-so-fresh installation, as I have. Now it will appear in the diff *twice:* once as an entry in Live Ubuntu's log which doesn't appear at the corresponding place in the installed system's log, and once as the reverse.

But in my case it didn't appear in the diff at all. As I said, the results do not make sense.

I tried running sudo apt-mark showmanual, and I got results that did make sense. It lists all of the installed packages in alphabetic order, which is not quite ideal -- I can't tell what I installed after I installed Ubuntu, but the next time I do a fresh installation I'll be able to tell. Since I won't need to know until then, it's good enough!

I'm still curious about why the diff on the logs isn't giving me useful information, but since I've solved my problem I no longer need to figure it out.

---

