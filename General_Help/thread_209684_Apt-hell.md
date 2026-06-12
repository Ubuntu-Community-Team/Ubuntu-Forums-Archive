---
title: "Apt-hell"
date: 2006-07-05
forum: General Help
---

### Post by deiniol on 2006-07-05
I've just upgraded from Breezy to Dapper and although it was a struggle, I got through it. A couple of days later, however, and I want to install a couple of new things and apt has decided to hate me.

Whenever I try to do pretty much anything, from sudo apt-get -f install
onwards, it returns the following error:

```
(Reading database ... dpkg: error processing 
/var/cache/apt/archives/libtotem-plparser0_1.2.0-0ubuntu3.1_i386.deb 
(--unpack): unable to open files list file for package `libgtkspell0': No
such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libtotem-plparser0_1.2.0-0ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Where "libtotem-plparser0_1.2.0-0ubuntu3.1_i386.deb" can be any package at all.

I've tried everything that I can think of. sudo aptitude purge libgtkspell0 returns the same error code. I've even manually downloaded libgtkspell0_2.0.10-3_i386.deb and placed it in /var/cache/apt/archives/ and I have no idea what else to try. ](*,) 

Any help would be greatly appreciated!

---

### Post by Dr. Nick on 2006-07-05
you ever clean your cache out?

try 
sudo apt-get clean

that will erase all downloaded package files from teh /var/cache/apt folder. May help since It will redownload the applications

then run 

sudo apt-get update

---

### Post by deiniol on 2006-07-05
Just tried that but it still throws up the same error. :(

---

### Post by deiniol on 2006-07-05
Just a thought, is there a way to install packages without using apt or dpkg?

---

### Post by Dr. Nick on 2006-07-06
[quote=deiniol]Just a thought, is there a way to install packages without using apt or dpkg?[/quote]


The only other method to install is a source compile, but to install from source you would probably need to install some depesndencies and thius would need apt/dpkg :(

Thier is also some applications using .run files but they are few.

---

### Post by Dr. Nick on 2006-07-06
A few ideas of other things you can try 
[B]
sudo apt-get -f install [/B]should try to force installation of packages not loaded due to errors.
[B]
sudo dpkg --configure -a [/B]Will try to configure packages which are installed but  unconfigured because of some error

---

### Post by ash211 on 2006-07-06
EDIT: sorry, Dr. Nick already suggested this.

You can manually compile and install tarballs (.tar.gz, .tgz, .tar.bz2, etc. they're just compressed source code to a program) without going through apt or dpkg.  But then uninstalling is a gamble.  

It just works if the tarball's creator put an uninstall function into it, or you use apt or dpkg to keep track of it for you with a program called checkinstall.  But then you're back around to the same problem!

---

### Post by deiniol on 2006-07-06
Neither of those worked either- still bringing up the libgtkspell0 error. Is there something I can do manually to this package in order to make it work?

---

### Post by Dr. Nick on 2006-07-06
Similar problem apperars to be solved here
[http://ubuntuforums.org/showthread.php?t=184555]("http://ubuntuforums.org/showthread.php?t=184555")

his "files list file" appears corrupt, while it apperas you have none.

here is the contents of my libgtkspell0.list file
```

/.
/usr
/usr/lib
/usr/lib/libgtkspell.so.0.0.0
/usr/share
/usr/share/doc
/usr/share/doc/libgtkspell0
/usr/share/doc/libgtkspell0/copyright
/usr/share/doc/libgtkspell0/changelog.gz
/usr/share/doc/libgtkspell0/changelog.Debian.gz
/usr/lib/libgtkspell.so.0
```

---

### Post by deiniol on 2006-07-06
Hm. This is really weird. I tried sudo gedit libgtkspell0.list but was told that I didn't have permission to open the file. Checking the properties, it says that its filetype is "x-special/device-block", so I can't modify it, or even change the  permissions. Gah.

---

### Post by Dr. Nick on 2006-07-06
you ran this command?

sudo gedit /var/lib/dpkg/info/libgtkspell0.list

It works correctly here, I am starting to think that maybe that file is corrupted and causing this mess.

---

### Post by deiniol on 2006-07-06
So I ran fsck. 

Bugger.

It fixed a lot of errors, but now I get a completely different error from apt. This one:

```
(Reading database ...
dpkg: serious warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `hwdata' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `scrollkeeper' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `python-minimal' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libpopt0' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libpt-1.10.0' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libgnomeprint2.2-0' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-panel' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libecal1.2-3' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-menus' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-media' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `evince' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libcomerr2' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libscim8c2a' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libxmlsec1-nss' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `evolution-exchange' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-panel-data' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `python2.4-clientcookie' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libgtkhtml2-0' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `evolution' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libtag1c2a' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `xscreensaver-gl' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `python2.4-apt' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-about' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.1_i386.deb (--unpack):
 unable to open files list file for package `gstreamer0.10-alsa': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Which doesn't look good.

---

### Post by deiniol on 2006-07-06
Perhaps I should just track down the .list files for each of them and key them in manually?

---

### Post by Dr. Nick on 2006-07-06
that may work ,I am not sure if them errors are the root of your ropblem or not, worth a try though.

not sure why fsck would mess it up more though.

I can probably add all the files from my system to a .tar fle if you wanted.

EDIT I have attached a copy of all the missing files from my computer if you want to try and extract them to /var/lib/dpkg/info

EDIT 2 I forgot to add the last gstreamer file to the attachement, if you use the other files and it solves them erors I will upload it

EDIT 3 I would also do a backup of any important files that you need incase something goes horribly wrong (always a chance) 
I would keep trying **apt-get install -f **and** apt-get remove [COLOR=Red]whatever package gives errors [/COLOR]**[COLOR=Red][COLOR=Black]when trying remove though make sure it isnt going to erase alot of important packages like gnome/xorg though[/COLOR][/COLOR][B][COLOR=Red]
[/COLOR][/B]

---

### Post by deiniol on 2006-07-06
Dr Nick, you're a star! I think I'm actually getting somewhere now!

I copied the files into /var/lib/dpkg/info and it cut the errors right down, now it's just giving the following error:

```
(Reading database ...
dpkg: serious warning: files list file for package `evolution-exchange' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `gnome-panel-data' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `python2.4-clientcookie' missing, assuming package has no files currently installed.
dpkg: serious warning: files list file for package `libgtkhtml2-0' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.1_i386.deb (--unpack):
 unable to open files list file for package `gstreamer0.10-alsa': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If you could attach copies of those files as well I'd be really grateful- I think that when fsck went and deleted all the corrupt files/inodes or whatever it does it wiped those files which buggered it all up. Replacing them manually seems to be pleasing to apt for some reason.

---

### Post by Dr. Nick on 2006-07-07
ok will attach the rest, I included the login one aswell, not sure if that will help the other error it gives.

---

### Post by deiniol on 2006-07-07
Sweet gods above! It worked! It worked! Hurrah! Thanks Dr. Nick! Whoopee! My confidence is restored.

---

### Post by Dr. Nick on 2006-07-07
Hehe glad that got it all fixed up.

---

