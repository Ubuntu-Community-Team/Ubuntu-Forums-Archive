---
title: "Edgy eft....any repos????"
date: 2008-06-03
forum: General Help
---

### Post by Fenris_rising on 2008-06-03
hi all
im running 8.04 on my pc and on my budget laptop (had xp on it) i had xubuntu 7.10. now ive done a complete install of edgy eft instead and it fair rips along when compared to xubuntu. so im happy with that i even got the wireless dongle working within 10 mins. but!!! there appear to be no active repos. is this correct is edgy eft extinct! if so is there anything i can do about it other than go up to fiesty fawn or gibbon as i tried them and they fair crawled along on the lappy. i like edgy its quick on my system and of course being ubuntu is laid out in a familiar way. i have trawled the net for repos but they all seem to be deader than a dead thing thats very dead.....and then some. lappy specs provided for anyone to suggest an GOOD alternative Distro if edgy eft is dead. i use the laptop for browsing the web, music movies and openofficed type stuff.
laptop specs;
40Gb HDD
CD RW/DVD drive
1.2Mgz Nemahia cpu
256Mb ram shared with GPU

---

### Post by Joeb454 on 2008-06-03
No there's no repo's for edgy eft anymore, support for edgy ended in October 07 from what I recall :)

I believe dapper drake is still supported for another year :)

---

### Post by msburko on 2008-06-04
Am I as screwed as it seems?

I want to upgrade from Edgy to Feisty. To do that Edgy must get all its updates. Edgy repos are gone so Edgy cannot update.

How do I upgrade away from Edgy?

Mitch

---

### Post by doorknob60 on 2008-06-04
Not sure if this will work well, but it should.

Press alt-f2, and type this:
```
gksu mousepad /etc/apt/sources.list
```
I'm assuming you're still on Xubuntu, if not, replace mousepad with gedit.

Change wherever it says 'edgy' to either 'feisty', 'gusty', or 'hardy'.

Then open a terminal and type this:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you don't like the slowness of newer versions, I recommend Debian with Xfce, it's a ton faster than any version of Xubuntu i've ever used. If you want to try it, I can give you some links and tips :)

---

### Post by zvacet on 2008-06-04
> Change wherever it says 'edgy' to either 'feisty', 'gusty', or 'hardy'.

You can not do that.Upgrade must be one step at the time so Edgy>Feisty>Gutsy>Hardy.To change your source list to Feisty type in terminal

```
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by msburko on 2008-06-04
As recommended, I replaced "edgy" with "feisty" in /etc/apt/sources.list

When I ran
```

sudo apt-get update && sudo apt-get dist-upgrade

```
It seemed to retrieve 18 packages. Some produced a 404 error like the ones show for the 18th package shown here
```

Get:18 http://us.archive.ubuntu.com feisty-updates/restricted Sources [956B]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1885kB in 6s (288kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I went back to the Package Manager GUI ( icon at the top of the screen next to the date). I selected Upgrade to 7.04. It down loaded 600+ files and seemed to go though the update.

It has reported 1 broken package. It tells me to use the "broken" filter to fix it. I have not found that filter yet.

I restarted the Package Manager GUI and noticed the UPGRADE button is now for 7.10. Some level of upgrade to 7.04 has occured. The Package Manager told me the Software Index is Broken and to run "sudo apt-get install -f". So I did that.


It did a bunch of stuff then said changes would be complete when all X session were closed. I decided to restart the system.

The Update Manager listed 300+ updates to be done. I guess they were not run when they were downloaded. Did them, restarted then got into trouble.

All the menu text is box characters. I can open a text file and see the text. But the "GUI text" i.e. the desktop menus and the window titles are all boxes.

I navigated by icons to the Update Manager but it does not start! Opps!

---

### Post by zvacet on 2008-06-05
It look like you still have some Edgy repos in your source list.

```
cat /etc/apt/sources.list
```

Post output here.

---

### Post by msburko on 2008-06-05
I did look for that. Could the edgy reference be somewhere else. I am thinking Edgy is in the Dependencies.

```

msburko@ubu2:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu feisty-security universe
# deb-src http://security.ubuntu.com/ubuntu feisty-security universe

```

I run 
```
sudo apt-get update
```
and keep seeing the same 3 retrieval attempts 
```
msburko@ubu2:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security Release.gpg
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com edgy-security Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Ign http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Ign http://us.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Ign http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://us.archive.ubuntu.com edgy-updates/universe Packages
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Fetched 3B in 1s (2B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
msburko@ubu2:~$  
```

There are references to Edgy. I am guessing the IGN means Ignore.

After the the GET should there be some indication of applying the update?

Thanks, Mitch

---

### Post by zvacet on 2008-06-05
In your source list there is no edgy repos and that is O.K. but then it shouldn´t looking for them.I saw that you are missing one line so 

```
gksudo gedit /etc/apt/sources.list
```

and remove all security lines and add these

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by msburko on 2008-06-05
Got the Box Characters fixed. It was a common flaw of an incomplete update from 6.10 to 7.04. I fixed mine by removing and installing ubuntu-desktp.
```

sudo aptitude remove ubuntu-desktop
sudo aptitude ubuntu-desktop

```

As for the upgrade that is not finished yet. I removed "libsasl" with the GUI package Manager. That allowed the correct package to install. 

When I run ```
 sudo aptitude update
``` I still have 1 module download that is looking for an edgy file.
```
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-updates/universe Packages
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 3B in 1s (2B/s)
Reading package lists... Done
msburko@ubu2:~$
```

Yes I did edit /etc/apt/sources.list. I did not show the code fragment of the edit command because I showed the file after it was edited. Sorry that was not clear.

Thanks, Mitch

---

### Post by msburko on 2008-06-06
I found more references to edgy. /etc/apt contains a folder named "sources.list.d". In it is a file named "edgy-universe.list" as shown.
```
msburko@ubu2:~$ cat /etc/apt/sources.list.d/edgy-universe.list
# automatically added by gnome-app-install on 2007-01-10 15:00:31.572516
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates universe
msburko@ubu2:~$

```
I changed edgy to feisty  ```

msburko@ubu2:~$ cat /etc/apt/sources.list.d/edgy-universe.list
# automatically added by gnome-app-install on 2007-01-10 15:00:31.572516
# 06jun08 MB changed edgy to feisty. Trying to complete upgrade from 6.10 to 7.04
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates universe
msburko@ubu2:~$
```

Then the errors in ```

sudo aptitude update

``` stopped. Oddy it only retrieved the files it did not install them. 

The file "/etc/apt/sources.list.d/edgy-universe.list" disappeared. 

I'm now running the install update option from the update manager (top of screen next to clock).

---

### Post by msburko on 2008-06-06
IT WORKED!! The systems is now at Feisty Fawn, 7.04. Update manager offers me an upgrade to 7.10. YEEEE HAAAAA!!!!!

Thanks for all the help folks.

In summary 2 files needed to be edited. Both needed all references of edgy to be changed to feisty. The files are:

/etc/apt/sources.list
/etc/apt/sources.list.d/edgy-universe.list

Then just keep banging on the update, upgrade and dist-upgrade until it is done.

THANKS AGAIN, YEEEE HAAAAAAA!

---

### Post by omrsafetyo on 2008-06-11
Yeah - I thought it was kind of fishy when I navigated to [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) and din't see Edgy - that's how I finally found this thread, after quite a while of reading "The mirror must be down" in google results.  

I finally came here, and rather than creating a new thread, searched for "Edgy repos gone", and lo and behold...

---

### Post by omrsafetyo on 2008-06-13
Hey - this didn't go so well for me.
I restored my original sources.list file that was packed with ubuntu - uncommented all sources, and then did a find and replace with sed to switch edgy with feisty.

I ran ```
sudo apt-get update
``` which seemed to go pretty well, followed by ```
sudo apt-get dist-upgrade
```

This command finished with a couple errors (which I didn't save).  I went to go see what version I was at - when checking this I was told I had 1 broken module.  The version still pointed to 6.10.

I decided to try a reboot to see if that would show the updated version - but unfortunately my PC never came back up.  When it gets to the Ubuntu loading screen, it just sits there.  From the GRUB menu, I can actually get to a shell prompt if I use the 1.16?? (as opposed to 1.17?? - the lesser of the two choices) kernel recovery option.
On loading, it fails to load hardware drivers - though successfully mounts my file systems.  I am currently in the process of gzipping my files so that I can put them on another drive and reformat - but does anyone else have any suggestions?

Oh yeah - If I try to re-install the OS, it tells me that 7.04 is already installed on the FS during the GRUB installation; but it certainly doesn't boot to that.  Unfortunately I do not have a LiveCD - I originally downloaded the alt distribution for 64 bit (I have a 64 bit processor).  I did have to force quite a few installations and even recompiled a couple 32 bit sources for 64 bit.  My nVidia drivers were the proprietary drivers that I downloaded and installed using instructions I found somewhere around here.  Just some extra info.

---

