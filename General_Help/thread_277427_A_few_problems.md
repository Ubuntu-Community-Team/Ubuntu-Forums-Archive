---
title: "A few problems"
date: 2006-10-14
forum: General Help
---

### Post by Alexeon Lanar on 2006-10-14
I have a few problems. I dont know how to fix them so Im hoping someone can help.

When I try to update I get two error messeges. I took screenshots.
[[IMG]http://img49.imageshack.us/img49/6091/screenshotyh8.th.png[/IMG]](http://img49.imageshack.us/my.php?image=screenshotyh8.png)
[[IMG]http://img237.imageshack.us/img237/2442/screenshot1kx1.th.png[/IMG]](http://img237.imageshack.us/my.php?image=screenshot1kx1.png)
[[IMG]http://img237.imageshack.us/img237/8822/screenshot2ya0.th.png[/IMG]](http://img237.imageshack.us/my.php?image=screenshot2ya0.png)


My second problem is really just kind of an annoyance. When I turn on my PC, I get a lot of options for grub. I have like 4 or 5 Ubuntu options and one WinXP option (which is fine since Im dual booting.)
I dont want so many options... how can I get rid of them?

My last problem is that when I try to add a new printer, I dont have the drivers... where can I find drivers for an HP Photosmart 8050 printer and a Dell Photo printer 720?

Thank you for your help.

---

### Post by Kateikyoushi on 2006-10-14
Copy these lines to terminal it should solve the problem you posted in the screenshots.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

The long grub list is your older unused kernels I think.
You can remove them with synaptic.
Start synaptic and check in the left frame installed (local or obsolate).

One or two might be there.
It is not a bad idea to keep one backup kernel just in case.

I do not know how to install the printers, hopefully someone can lend you a hand with it.

---

### Post by taurus on 2006-10-14
1.  Update your system from a terminal would make it much easier, Applications -> Accessories -> Terminal...

```
sudo update 
sudo upgrade
```

2.  You can edit your /boot/grub/menu.lst and remove whichever entry you don't want.  The best way is to put a # in front of those lines, leaving your Ubuntu, the recovery mode in case you need to boot from it, and your XP alone...

```
gksudo gedit /boot/grub/menu.lst
```

3.  There should be drivers in the database for your printers!  Have you looked for your models when you install them?

---

### Post by Alexeon Lanar on 2006-10-14
Thank you. I did what you told me and I tried the update to check if it worked, but I got this messege:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)


I tried looking for "Installed (local or obsolete)" "local" and "obsolete" and I couldnt find a section labeled like that in the left window.

Thanks though. ^^



I could do the update by terminal... Its just that the GUI gives info on what Im installing...

When I put my default OS selected, do I count the # options?

I looked for drivers in the options that came up if thats what you mean.

---

### Post by taurus on 2006-10-14
Maybe you are using some old out-of-date repos.  Post your /etc/apt/sources.list here then.  Open a terminal, Applications -> Accessories -> Terminal, and type this command it.  Cut 'n past the output here.

```
more /etc/apt/sources.list
```

Lines start with # don't count.  They are comments and void...

p.s.  I found HP PhotoSmart 8000 & 8100.  Try using PhotoSmart 8100 to see if it works with your HP printer.

---

### Post by Alexeon Lanar on 2006-10-14
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free



## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


There it is.

---

