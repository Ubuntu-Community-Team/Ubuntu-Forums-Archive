---
title: "ttf-mscorefonts-installer broken?"
date: 2016-11-18
forum: General Help
---

### Post by marknaz on 2016-11-18
Using Ubuntu 16.04.1 32 bit

A while back, an update tried to reinstall ttf-mscorefonts-installer, but it failed. Subsequent attempts fail on my 32 bit machine, but apparently worked on my 64 bit machine.

Getting the following message:

```

username@perl:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer 
[sudo] password for username: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 29.5 kB of archives.
After this operation, 0 B of additional disk space will be used.

Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse i386 ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29.5 kB]
Fetched 29.5 kB in 0s (66.4 kB/s)                  
Preconfiguring packages ...
(Reading database ... 177033 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
**mscorefonts-eula license has already been accepted**

Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)

Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 1s (110 kB/s)                                                          
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)

Get:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe) [554 kB]
Fetched 554 kB in 1s (341 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)

Get:1 [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe) [168 kB]
Fetched 168 kB in 1s (158 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arialb32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)

Get:1 [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe) [969 B]
Err:1 [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)                                
  Hash Sum mismatch
Fetched 969 B in 0s (1,319 B/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/comic32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

**E: Failed to fetch [http://downloads.sourceforge.net/mirrorproblem?failedmirror=pilotfiber.dl.sourceforge.net](http://downloads.sourceforge.net/mirrorproblem?failedmirror=pilotfiber.dl.sourceforge.net)  Hash Sum mismatch**

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
username@perl:~$ 

```

Anyone else getting this?

Not sure how to proceed. Any help appreciated.

---

### Post by howefield on 2016-11-18
Personally I have started using the 3.6 ttf-mscorefonts-installer package instead of the broken 3.4 version included in the repository but seeing as you have attempted to install 3.4, try this...

```
mkdir /home/$USER/mscorefonts && cd /home/$USER/mscorefonts
```

```
grep Url: /usr/share/package-data-downloads/ttf-mscorefonts-installer | awk '{print $2}' | xargs -n 1 wget
```

```
sudo /usr/lib/msttcorefonts/update-ms-fonts /home/$USER/mscorefonts/*
```

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

---

### Post by marknaz on 2016-11-18
Thank you for your reply, but the second step gives the following:
> 
username@perl:~/mscorefonts$ grep Url: /usr/share/package-data-downloads/ttf-mscorefonts-installer | awk '{print $2}' | xargs -n 1 wget
grep: /usr/share/package-data-downloads/ttf-mscorefonts-installer: No such file or directory
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
username@perl:~/mscorefonts$ 

Can not the proper thing be done by fixing the broken package?

---

### Post by howefield on 2016-11-19
> **marknaz said:**
> Thank you for your reply, but the second step gives the following:

Ok, I guess the system has removed the ttf-mscorefonts-installer deb package before running that command.

Here is another way.

Download the fonts from : 

```
https://sourceforge.net/projects/corefonts/files/the%20fonts/final/
```

and store them in the /home/$USER/mscorefonts folder that you created earlier (I have uploaded them as a [single file]("https://www.dropbox.com/s/5d51u2ofl00wxet/mscorefonts.tar.gz?dl=0") if you want) and run..

```
sudo /usr/lib/msttcorefonts/update-ms-fonts /home/$USER/mscorefonts/*
```
```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

> Can not the proper thing be done by fixing the broken package?

Yes, sounds so easy, doesn't it :)

This is why I downloaded the 3.6 deb package and install it with apt.

---

### Post by kurt18947 on 2016-11-20
I've created a 'standard font set' on a flash drive.  AFAIK Ubuntu stores fonts at /usr/share/fonts. In addition to Microsoft's core fonts I have other free fonts. When I do a fresh install I delete fonts that I don't use and copy over those that I do.

---

### Post by missmoondog on 2016-11-20
fwiw,
yes, i've gotten that same error on my 6 lubuntu machines also. haven't even paid attention if it was only on my 32bit machines or not and don't really care as nothing seems to be effected.

not about to jump through the hoops required to do what howefield says to do either! if it isn't broke, don't fix it!! :)

---

### Post by marknaz on 2016-11-20
Well, here's what I decided to do:

Firstly, a big thanks to all who replied with their suggestions.

Now, a listing of my **/usr/share/fonts/truetype/msttcorefonts/** directory still has all of the fonts from the initial installation, and some, told by time stamp, from subsequent reinstall attempts.

But I was still receiving nag mail from logwatch about the update failure.

So now I head over to **/var/lib/update-notifier/package-data-downloads/** and get this:

```

username@perl:/var/lib/update-notifier/package-data-downloads$ ls -al
total 12
drwxr-xr-x 3 root root 4096 Nov 18 02:12 .
drwxr-xr-x 4 root root 4096 Nov 20 19:40 ..
drwxr-xr-x 2 root root 4096 Nov 20 02:21 [COLOR=blue]partial[/COLOR]
-rw-r--r-- 1 root root    0 Nov 20 02:21 **ttf-mscorefonts-installer.failed**
username@perl:/var/lib/update-notifier/package-data-downloads$

```
A listing of [COLOR=blue]partial[/COLOR]:

```

username@perl:/var/lib/update-notifier/package-data-downloads$ ls -al partial/
total 2652
drwxr-xr-x 2 root root   4096 Nov 20 02:21 .
drwxr-xr-x 3 root root   4096 Nov 18 02:12 ..
-rw-r--r-- 1 root root    969 Nov 20 02:21 andale32.exe.FAILED
(several more listings here)
-rw-r--r-- 1 root root 185072 Aug 15  2002 webdin32.exe
username@perl:/var/lib/update-notifier/package-data-downloads$

```
And since my fonts directory already has these fonts, I'm calling the [COLOR=blue]partial[/COLOR] as leftovers, and wisely tossed after three days.

```

username@perl:/var/lib/update-notifier/package-data-downloads$ sudo rm [COLOR=blue]partial[/COLOR]/*.*
username@perl:/var/lib/update-notifier/package-data-downloads$

username@perl:/var/lib/update-notifier/package-data-downloads$ sudo rmdir [COLOR=blue]partial/[/COLOR]
username@perl:/var/lib/update-notifier/package-data-downloads$

username@perl:/var/lib/update-notifier/package-data-downloads$ sudo rm **ttf-mscorefonts-installer.failed**
username@perl:/var/lib/update-notifier/package-data-downloads$

```

So now the previous directory has been scrubbed, **ttf-mscorefonts-installer** shows as installed, and the fonts directory still has the fonts.

And since there are fonts, and not code designed to write to disks or whatever, I'm calling my issue fixed.

Also, new installs down here at Central will be done with the 3.6 version: [https://packages.debian.org/jessie/ttf-mscorefonts-installer](https://packages.debian.org/jessie/ttf-mscorefonts-installer)

> **howefield said:**
> 
...
Yes, sounds so easy, doesn't it

This is why I downloaded the 3.6 deb package and install it with apt.
Oh, I'm sure that there's much more to this than I'll ever know. :redface:

Thanks again everyone!

---

### Post by marknaz on 2016-11-24
Hello again, and sorry for the bump. 

It's just that I have some additional info that may be useful for future googlers.

Anyway, I tried installing the Debian ttf-mscorefonts-installer package on a new Ubuntu 16.04.1 32 bit installation, and it failed for me. 

However, I did find some possibly suitable replacements.

> 
**fonts-arkpandora**

This package provides fonts which can be used as drop-in replacement
for Microsoft shipped  fonts **Arial, Times New Roman and Verdana.**

These fonts are designed for screens and printing. It includes
Aerial, Aeirial Mono, Tymes and Veranda.


I installed this one for the Verdana font, and it looks just as good as the original to my eyes.

-Also-
> 
For the **ttf-mscorefonts-installer:**

NOTE: the package **fonts-liberation** contains free variants of the [B]Times,
Arial and Courier fonts.[/B] It's better to use those instead unless you
specifically need one of the other fonts from this package.


Again, sorry for the bump.

Peace.

---

### Post by heldal2 on 2016-12-07
ttf-mscorefonts-installer 3.6 from the debian-repo attempts to work around the download-problem by addressing specific sourceforge-mirrors. This approach may not work for everyone. The proper solution is to either host the fonts on a less complex server elsewhere, or to use a more capable HTTP-client for downloads in the installer to make it able to cope with Sourceforge's methods for redirection and distribution of ads.

---

### Post by SunnyDaze on 2016-12-17
What finally worked for me was to **wget** the 3.6 version of the Debian package, and then install it.

I just typed this into a terminal window.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb
sudo dpkg -i ttf-mscorefonts-installer_3.6_all.deb
```

One thing I did before getting the 3.6 Debian version was **purge** and **autoremove** the **ttf-mscorefonts-installer**.  I did this to make sure the install package was removed, and also to make sure config files, if any, were also removed.  I'm not sure if this was necessary.  Here are the commands I used to purge and autoremove:

```
sudo apt-get purge ttf-mscorefonts-installer
sudo apt-get autoremove ttf-mscorefonts-installer
```

---

