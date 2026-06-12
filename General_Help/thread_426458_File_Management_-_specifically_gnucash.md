---
title: "File Management - specifically gnucash"
date: 2007-04-28
forum: General Help
---

### Post by gwatts on 2007-04-28
I am new to Linux (using Ubuntu 7.04) and trying to understand how to do things that have some familiarity with Windows.  I would like to go somewhere and find the gnucash executable for example and create a shortcut or icon on the desktop. I would also like to back up the xac files or “main data file”.

gnucash help says:
“To restore an old backup file, simply open the .xac file------So which files should you keep around? Keep your main data file, of course - data files do not have an automatic file extension. It's a good idea to keep some of the more recent .xac files,”

When I go into the usr/bin and try to change permissions so as to try backup or create a desktop icon with the gnu files I am not allowed. So:

1 How do I assume root powers. I am the only owner and user?
sudo chown me gnucash or gnucash-bin > “no such file”.

2 How do I find an executable gnucash file so I can start it or create a desktop icon?

3 How do I find and backup either the “main data file” or the “.xac”?

Thank you.

---

### Post by shawnrgr on 2007-04-28
How did you install GnuCash? You should goto Application>Add/Remove... Then search for it via the search box. If you don't see it in there you need to add extra repositories which will make available to you many more applications. This is easy if you follow these steps exactly:

In a terminal (applications>accessories>terminal) paste these lines ONE AT A TIME:
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```
Then:
```
sudo gedit /etc/apt/sources.list
```
Then replace everything in the file with the following:
```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Save the edited file, then close the text editor.

Then again in terminal:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Then:
```
sudo aptitude update
```

If you mess something up just run this:
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

Then launch Add/Remove and search for GnuCash again. Install it.

If you have installed gnucash through add/remove programs, then there will already be a shortcut to launch it under Applications>Office, left-click and hold, then drag to the panel to create a new shortcut there.

---

### Post by gwatts on 2007-04-29
Got it 

Thank you.

---

