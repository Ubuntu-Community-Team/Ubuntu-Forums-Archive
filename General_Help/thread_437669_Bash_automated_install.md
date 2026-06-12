---
title: "Bash automated install"
date: 2007-05-09
forum: General Help
---

### Post by Scheater5 on 2007-05-09
I'm an experienced Linux user, but not a veteran (about a year of experience), but I'm a newbie to scripting.  I'm trying to write a shell script to automate post-installation setup.  I've hit a roadblock.  I want to rewrite my sources list to the sources list of the unofficial wiki.  How would I include this in a script?  My goal is to have one file and only one file on a pendrive that would rewrite my sources, and then run a series of installations.  Perhaps eventually I'll look into my other setup steps, like configuring the panel, wallpaper and getting proper monitor resolution, and I'd welcome any comments on these steps as well.  Thanks in advance.

---

### Post by spin2cool on 2007-05-09
There are several options.  The easiest would be to also keep a copy of your sources.list on the pendrive, then simply copy it over the other one.  

If it's available online at an address that is stable, you can use wget to pull it down:

```

wget http://www.asdfasdfasdf.com/sources.list
mv sources.list /etc/apt/sources.list

```

Another (ugly) option would be to write out the sources file line by line from bash.

```

echo "line1 asdf asdf asdf" > /etc/apt/sources.list
echo "line2 asdf asdf asdf" >> /etc/apt/sources.list

```

Note that the first line uses a single arrow (overwrite) and the second uses a double arrow (append)

---

### Post by Scheater5 on 2007-05-09
I'm leaning towards writing them out a line at a time in the script.  Besides being a practical application, this is also good training in writing scripts for me.  I'm not entirely sure I get the syntax of echo and the overwrite and append commands.  I'm trying it now, I'll post results.

---

### Post by spin2cool on 2007-05-09
It's fairly simple: I have a file (file.txt) with these contents:
```
this is line 1
```

If I use this command:
```
echo "this is line 2" >> file1.txt
```
Then file1.txt looks like this:
```
this is line 1
this is line 2
```

If I then use this command:
```
echo "this is line 3" > file1.txt
```
Then file1.txt looks like this:
```
this is line 3
```

The double arrows appended the text to the end of the file, the single arrow deleted the contents of the file and overwrote them with the new stuff.

---

### Post by Scheater5 on 2007-05-09
It would seem I have had success.  

```
#!/bin/bash
# First Draft of Automated Installation


sudo cp /etc/apt/sources.list /etc/apt/sources,list_backup
echo "## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to" > /etc/apt/sources.list
echo "## newer versions of the distribution." >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## Add comments (##) in front of any line to remove it from being checked.   " >> /etc/apt/sources.list
echo "## Use the following sources.list at your own risk.  " >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## Uncomment deb-src if you wish to download the source packages" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## If you have a install CD you can add it to the reposity using 'apt-cdrom add'" >> /etc/apt/sources.list
echo "## which will add a line similar to the following:" >> /etc/apt/sources.list
echo "#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted" >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted" >> /etc/apt/sources.list
echo "#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## Major bug fix updates produced after the final release of the" >> /etc/apt/sources.list
echo "## distribution." >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted" >> /etc/apt/sources.list
echo "#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu" >> /etc/apt/sources.list
echo "## team, and may not be under a free licence. Please satisfy yourself as to" >> /etc/apt/sources.list
echo "## your rights to use the software. Also, please note that software in" >> /etc/apt/sources.list
echo "## universe WILL NOT receive any review or updates from the Ubuntu security" >> /etc/apt/sources.list
echo "## team." >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ feisty universe" >> /etc/apt/sources.list
echo "#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu" >> /etc/apt/sources.list
echo "## team, and may not be under a free licence. Please satisfy yourself as to" >> /etc/apt/sources.list
echo "## your rights to use the software. Also, please note that software in" >> /etc/apt/sources.list
echo "## multiverse WILL NOT receive any review or updates from the Ubuntu" >> /etc/apt/sources.list
echo "## security team." >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse" >> /etc/apt/sources.list
echo "#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## Uncomment the following two lines to add software from the 'backports'" >> /etc/apt/sources.list
echo "## repository." >> /etc/apt/sources.list
echo "## N.B. software from this repository may not have been tested as" >> /etc/apt/sources.list
echo "## extensively as that contained in the main release, although it includes" >> /etc/apt/sources.list
echo "## newer versions of some applications which may provide useful features." >> /etc/apt/sources.list
echo "## Also, please note that software in backports WILL NOT receive any review" >> /etc/apt/sources.list
echo "## or updates from the Ubuntu security team." >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse" >> /etc/apt/sources.list
echo "#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu feisty-security main restricted" >> /etc/apt/sources.list
echo "#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted" >> /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu feisty-security universe" >> /etc/apt/sources.list
echo "#deb-src http://security.ubuntu.com/ubuntu feisty-security universe" >> /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu feisty-security multiverse" >> /etc/apt/sources.list
echo "#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)" >> /etc/apt/sources.list
echo "## Medibuntu - Ubuntu 7.04 "feisty fawn"" >> /etc/apt/sources.list
echo "## Please report any bug on https://launchpad.net/products/medibuntu/+bugs" >> /etc/apt/sources.list
echo "deb http://medibuntu.sos-sts.com/repo/ feisty free non-free" >> /etc/apt/sources.list
echo "#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu" >> /etc/apt/sources.list
echo "## servers. RealPlayer10, Opera, DesktopSecure and more to come.) " >> /etc/apt/sources.list
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "## enlightenment e17 beta, use at your own risk" >> /etc/apt/sources.list
echo "## E17 is in Beta and may break or break your system" >> /etc/apt/sources.list
echo "#deb http://edevelop.org/pkg-e/ubuntu feisty e17" >> /etc/apt/sources.list
echo "#deb http://e17.dunnewind.net/ubuntu feisty e17" >> /etc/apt/sources.list
echo "#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17" >> /etc/apt/sources.list
aptitude update
aptitude upgrade
```

Thanks guys.

---

