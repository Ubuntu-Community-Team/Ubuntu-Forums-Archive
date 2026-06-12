---
title: "Adept installer error"
date: 2007-12-10
forum: General Help
---

### Post by Helgiks on 2007-12-10
Hello.

I am very new to Linux and decided to install Kubuntu for try because i really hate windows, so I thought I'd give it a try. I went through the installation smoothly without errors. But when i started it the first time it told me to update, wich i did. While in the middle of the update i get the following error message: 

> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

And now this error message comes when ever i try to install anything with this installer. I can't seem to be able to install anything because of this. Please help, and please be exact, because I don't really know anything about linux.

Kv,
Helgiks

---

### Post by p_quarles on 2007-12-11
You can likely get some better error information by running this update from the command line. You'll need to open a terminal (alt-F1), and then run the following commands:
```
sudo apt-get update
```
This one should run okay. Then:
```
sudo apt-get upgrade
```
This command will attempt to download and install new versions of currently installed packages, and I'm guessing that this is where the error is occurring. Please copy and paste whatever error message comes up after running this command. This message will probably give us a clue as to where the problem lies.

---

### Post by Helgiks on 2007-12-15
Hehe, well thanks for the help but i moved to Ubuntu from Kubuntu, not having that proplem there, and i like it better.

---

### Post by ncochard on 2008-04-05
Hello

I am new to Kubunu and I am getting precisely the same problem when I try to run the updates.
```

There was an error committing changes.
Possibly there was a problem downloading some packages or the commit would break packages.
```

When I try to run the command "sudo apt-get update", I get the following error message.

```
ncochard@ncochard-laptop:~$ sudo apt-get update
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_GB
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_GB
Get: 1 http://gb.archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://gb.archive.ubuntu.com gutsy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/restricted Translation-en_GB
Get: 2 http://security.ubuntu.com gutsy-security Release.gpg [191B]
.... some text has been removed from here....
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (3B/s)
[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]
```

When I type the command "sudo apt-get upgrade", I get exactly the same error message.

```
ncochard@ncochard-laptop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So I tried the "dpkg" command...

```
ncochard@ncochard-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
```

So, I used the "su" command to become super user to run the command "dpkg --configure -a" but my user password does not work.

I am a bit lost, the installation of kubuntu never asked me for a root (super user) password, my own password cannot be used to run the "dpkg" command. As a result, I am unable to get the information that I need to solve this installation problem.

Am I missing something obvious?

Thanks a lot in advance for your help.

Nicolas

---

### Post by SOULRiDER on 2008-04-05
Use sudo:
```
sudo dpkg --configure -a
```

And then run
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Remember, **aptitude** is better than **apt-get**, so use it instead of apt-get.

---

