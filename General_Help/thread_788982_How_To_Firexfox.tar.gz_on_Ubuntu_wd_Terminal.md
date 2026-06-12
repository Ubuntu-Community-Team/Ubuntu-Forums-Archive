---
title: "How To Firexfox**.tar.gz on Ubuntu wd Terminal???"
date: 2008-05-10
forum: General Help
---

### Post by rinav on 2008-05-10
. Downloaded the Firefox 2.0.0.14.tar.gz
. Untared
. A Folder named "firefox" created
. now what shall i do???
. I am the Super User and the files have read-write and Exec permission

i don't want to install from Package Manager as I've already downloaded tar.gz.
Want to learn to install from Terminal


Terminal :~/firefox$ sudo ./configure
sudo: ./configure: command not found

Terminal :~/firefox$ sudo make
sudo: make: command not found

Terminal :~/firefox$ sudo make install
sudo: make: command not found

Terminal :~/firefox$

this is what I tried and the output

. is configure a file name or command???
. if File den configure does not exists after i untared it

Is firefox ***.tar.gz already compiled? or di i have to Compile it?

please provide me with step by step guide...

---

### Post by tacutu on 2008-05-10
well, did you download the precompiled binaries or the sources?

(btw, i think firefox 2.0 is still in the repositories, so why bother to compile?)

---

### Post by rinav on 2008-05-10
well, did you download the precompiled binaries or the sources?

> **tacutu said:**
> (btw, i think firefox 2.0 is still in the repositories, so why bother to compile?)

Its Compiled I Guess. How do I check It???

I know its in the Repositories,
I want to learn How to do it Manually using Terminal(Hard Way)..
I have some other apps which i use it for Programming I need those too in Ubuntu... 

So running form Terminal is not the Best Option.

---

### Post by Lateralis on 2008-05-10
The following two links will help you with installing programmes from "tarballs".  

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Essentially, once you've untarred the tarball, cd to the new directory and open up the readme file - that should tell you any important information for the installation.  Generally though, you'll need to go:

./configure 
make
make install

./configure may not always work and spit out some errors - you sometimes need newer or new packages and libraries.  In the event of ./configure failing, the terminal will tell you what it failed on.  You will also definitely need build-essential before you do anything: 

sudo apt-get install build-essential

Hope this helps. :)

---

### Post by rinav on 2008-05-10
The following two links will help you with installing programmes from "tarballs".  

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Essentially, once you've untarred the tarball, cd to the new directory and open up the readme file - that should tell you any important information for the installation.  Generally though, you'll need to go:

> **Lateralis said:**
> 
./configure 
make
make install

./configure may not always work and spit out some errors - you sometimes need newer or new packages and libraries.  In the event of ./configure failing, the terminal will tell you what it failed on.  You will also definitely need build-essential before you do anything: 

sudo apt-get install build-essential

Hope this helps. :)



I have already Tried $ sudo /.configure
But Nothing Works
It says :: 

Terminal :~/firefox$ sudo ./configure
sudo: ./configure: command not found

Terminal :~/firefox$ sudo make
sudo: make: command not found

Terminal :~/firefox$ sudo make install
sudo: make: command not found

**Also I ahve already Installed the build-essential Package**

I have already Gone through both the Links But No Luck
what do i do next???

---

### Post by fsmithred on 2008-05-10
If you unpacked the tarball in your home directory, just open a terminal and type:

```
firefox/firefox &
```

and firefox will open.

---

### Post by Lateralis on 2008-05-10
You don't go "sudo ./configure" etc...  Just ./configure should do the trick.

---

### Post by rinav on 2008-05-10
> **fsmithred said:**
> If you unpacked the tarball in your home directory, just open a terminal and type:

```
firefox/firefox &
```

and firefox will open.

Nope It Doesent Open!!! :confused:

---

### Post by rinav on 2008-05-10
> **Lateralis said:**
> You don't go "sudo ./configure" etc...  Just ./configure should do the trick.

This toooooooo I Tried dont work for me...

---

### Post by fsmithred on 2008-05-10
If you want practice installing software from source, then pick something else. Sorry I can't think of any simple examples right now - everything I've wanted lately is in repos. I can think of some not-so-easy examples. When you're up for it, try installing apache-php-mysql or better yet, transcode from source.

---

### Post by tacutu on 2008-05-10
go into the firefox directory and type
```
ls
```

post the output here so we can see what you have there.

if you want to learn "the hard way" and have lots of patience and time, you can always try and build your own linux: [www.linuxfromscratch.org](www.linuxfromscratch.org)

---

### Post by rinav on 2008-05-10
> **tacutu said:**
> go into the firefox directory and type
```
ls
```

post the output here so we can see what you have there.

if you want to learn "the hard way" and have lots of patience and time, you can always try and build your own linux: [www.linuxfromscratch.org](www.linuxfromscratch.org)



the Output from ls -l

rinav@UbuntuRocks:~$ ls -l firefox
total 13662
-rwxrwxrwx 1 rinav rinav      232 2008-04-05 03:31 browserconfig.properties
drwxrwxrwx 3 rinav rinav      520 2008-04-05 03:32 chrome
drwxrwxrwx 2 rinav rinav     1480 2008-04-05 03:32 components
drwxrwxrwx 5 rinav rinav      128 2008-04-05 03:32 defaults
drwxrwxrwx 2 rinav rinav      112 2008-04-05 03:31 dictionaries
drwxrwxrwx 5 rinav rinav      184 2008-04-05 03:32 extensions
**-rwxrwxrwx 1 rinav rinav     5286 2008-04-05 03:32 firefox**
**-rwxrwxrwx 1 rinav rinav 10576676 2008-04-05 03:32 firefox-bin**
drwxrwxrwx 2 rinav rinav      144 2008-04-05 03:32 greprefs
drwxrwxrwx 2 rinav rinav      176 2008-04-05 03:32 icons
-rwxrwxrwx 1 rinav rinav      476 2008-04-05 03:32 libfreebl3.chk
-rwxrwxrwx 1 rinav rinav   231468 2008-04-05 03:32 libfreebl3.so
-rwxrwxrwx 1 rinav rinav   631676 2008-04-05 03:32 libmozjs.so
-rwxrwxrwx 1 rinav rinav   176716 2008-04-05 03:32 libnspr4.so
-rwxrwxrwx 1 rinav rinav   430608 2008-04-05 03:32 libnss3.so
-rwxrwxrwx 1 rinav rinav   285152 2008-04-05 03:32 libnssckbi.so
-rwxrwxrwx 1 rinav rinav    15304 2008-04-05 03:32 libplc4.so
-rwxrwxrwx 1 rinav rinav     8240 2008-04-05 03:32 libplds4.so
-rwxrwxrwx 1 rinav rinav   138316 2008-04-05 03:32 libsmime3.so
-rwxrwxrwx 1 rinav rinav      476 2008-04-05 03:32 libsoftokn3.chk
-rwxrwxrwx 1 rinav rinav   309624 2008-04-05 03:32 libsoftokn3.so
-rwxrwxrwx 1 rinav rinav   155560 2008-04-05 03:32 libssl3.so
-rwxrwxrwx 1 rinav rinav    94924 2008-04-05 03:32 libxpcom_compat.so
-rwxrwxrwx 1 rinav rinav   699056 2008-04-05 03:32 libxpcom_core.so
-rwxrwxrwx 1 rinav rinav     9240 2008-04-05 03:32 libxpcom.so
-rwxrwxrwx 1 rinav rinav     8284 2008-04-05 03:32 libxpistub.so
-rwxrwxrwx 1 rinav rinav    10336 2008-04-05 03:32 mozilla-xremote-client
-rwxrwxrwx 1 rinav rinav      112 2008-04-05 03:31 old-homepage-default.properties
drwxrwxrwx 2 rinav rinav       80 2008-04-05 03:32 plugins
-rwxrwxrwx 1 rinav rinav      177 2008-04-05 03:32 readme.txt
-rwxrwxrwx 1 rinav rinav    13062 2008-04-05 03:31 removed-files
drwxrwxrwx 6 rinav rinav     1688 2008-04-05 03:32 res
**-rwxrwxrwx 1 rinav rinav    10492 2008-04-05 03:32 run-mozilla.sh**
drwxrwxrwx 2 rinav rinav      240 2008-04-05 03:31 searchplugins
-rwxrwxrwx 1 rinav rinav    67496 2008-04-05 03:32 updater
-rwxrwxrwx 1 rinav rinav      145 2008-04-05 03:31 updater.ini
-rwxrwxrwx 1 rinav rinav    21368 2008-04-05 03:32 xpicleanup
rinav@UbuntuRocks:~$

---

### Post by rinav on 2008-05-10
> **fsmithred said:**
> If you want practice installing software from source, then pick something else. Sorry I can't think of any simple examples right now - everything I've wanted lately is in repos. I can think of some not-so-easy examples. When you're up for it, try installing apache-php-mysql or better yet, transcode from source.


All i wanted to do is Install Firefox, Though its a bit tedious job for a newbee but will learn it...  

Ney ways Thanks for d Help n Support

---

### Post by tacutu on 2008-05-10
so it looks like you got the compiled binaries. There's no need for ./configure make and make install. You can just run:
 ```
./run-mozilla.sh
```
and it should work. Also, read the read.me file included, it might contain important info:
```
less readme.txt
```

---

### Post by rinav on 2008-05-10
> **tacutu said:**
> so it looks like you got the compiled binaries. There's no need for ./configure make and make install. You can just run:
 ```
./run-mozilla.sh
```
and it should work. Also, read the read.me file included, it might contain important info:
```
less readme.txt
```


**Terminal Says :: run-mozilla.sh: Cannot execute.**


**Read Me is of no use it says ::**
For information about installing, running and configuring Firefox 
including a list of known issues and troubleshooting information, 
refer to: [http://getfirefox.com/releases/](http://getfirefox.com/releases/)

---

### Post by tacutu on 2008-05-10
dunno why the script won't work, but you can run firefox directly:
```
./firefox
```

---

### Post by rinav on 2008-05-10
> **tacutu said:**
> dunno why the script won't work, but you can run firefox directly:
```
./firefox
```

Nope dis toooooooo:confused:

It says...

rinav@UbuntuRocks:~/firefox$ ./firefox
**./run-mozilla.sh: 424: ./firefox-bin: not found**
rinav@UbuntuRocks:~/firefox$ 

**[SIZE="6"]Y is says ./firefox-bin not found?[/SIZE]**
its present in the directory

---

### Post by tacutu on 2008-05-10
sorry man, i don't know

---

### Post by fsmithred on 2008-05-10
I don't know, either. I downloaded the same version of firefox and tested it this morning, and it worked fine. Something else must be wrong. One other way to try it would be to give the full path to firefox in the command, but that'll probably give you the same result.

```
/home/rinav/firefox/firefox
```

...or whatever your home directory is.

It really shouldn't be any harder than unpacking the archive and running the program.

---

### Post by rinav on 2008-05-11
> **fsmithred said:**
> I don't know, either. I downloaded the same version of firefox and tested it this morning, and it worked fine. Something else must be wrong. One other way to try it would be to give the full path to firefox in the command, but that'll probably give you the same result.

```
/home/rinav/firefox/firefox
```

...or whatever your home directory is.

It really shouldn't be any harder than unpacking the archive and running the program.




Nope it doesnt work!!! :(

I doubt ::** Do I have to Uninstall the Previous Version** (*** 0.0.6)
If dis is d case den Tell me how do i Uninstall

OR

Is der **ney Problem wd Universe or Multiverse**?? Do I hv to Enable Disable Something??

Also Firefox should automatically Update to its latest version (I guess), But its Grayed out in the Option button

---

### Post by fsmithred on 2008-05-11
No, you shouldn't have to remove FF3 to get this to work. Again, I'll say that something else is wrong. Maybe it was a bad download. 

If your goal is just to downgrade from FF3 to FF2, the easiest way would be to do it through synaptic. Remove FF3, and then install FF2. That way, your menus will point to the right version of firefox.

If your goal is to learn how to install from source, pick something other than firefox.

---

