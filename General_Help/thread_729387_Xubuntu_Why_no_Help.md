---
title: "Xubuntu: Why no Help?"
date: 2008-03-19
forum: General Help
---

### Post by pthomas on 2008-03-19
Xubuntu, current release
From the main menu, clicking "Applications", "Help" just results in
```
File not found
Firefox can't find the file at /usr/share/xubuntu-docs/desktopguide/C/index.html. 
```
I checked  /usr/share/xubuntu-docs/ and /desktopguide/ does not exist.
Why doesn't Xubuntu install it? Is the "Help" button some kind of recursive joke?

---

### Post by Oldsoldier2003 on 2008-03-19
> **pthomas said:**
> Xubuntu, current release
From the main menu, clicking "Applications", "Help" just results in
```
File not found
Firefox can't find the file at /usr/share/xubuntu-docs/desktopguide/C/index.html. 
```
I checked  /usr/share/xubuntu-docs/ and /desktopguide/ does not exist.
Why doesn't Xubuntu install it? Is the "Help" button some kind of recursive joke?
Dont know why but to install them :
```
sudo apt-get install xubuntu-docs
``` 
I didn't dig around for the package name for the desktop guide.

---

### Post by PeterJS on 2008-03-19
> **Oldsoldier2003 said:**
> Dont know why but to install them :
```
sudo apt-get install xubuntu-docs
``` 
I didn't dig around for the package name for the desktop guide.

Interesting addendum, I searched for the file, but it doesn't appear to be owned by any package:
```

peter@Osirus:~$ apt-file search /usr/share/xubuntu-docs/desktopguide/C/index.html
peter@Osirus:~$ 

```

I do like the suggestion of bad recursive joke, so that gets my vote because it makes me chuckle.

---

### Post by Taino on 2008-03-19
> **pthomas said:**
> Xubuntu, current releasee

[Xubuntu Gutsy 7.10 Docs]("http://packages.ubuntu.com/gutsy/all/xubuntu-docs/download")

you can download the docs from there from many links. :)

then to install it, from a terminal window, goto the
directory you downloaded it to and use

sudo dpkg -install xubuntu-docs_7.10.1_all.deb

---

### Post by pthomas on 2008-03-19
> **Oldsoldier2003 said:**
> Dont know why but to install them :
```
sudo apt-get install xubuntu-docs
``` 
I didn't dig around for the package name for the desktop guide.

That didn't help:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-docs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Any other ideas?

---

### Post by pthomas on 2008-03-19
> **Taino said:**
> [Xubuntu Gutsy 7.10 Docs]("http://packages.ubuntu.com/gutsy/all/xubuntu-docs/download")

you can download the docs from there from many links. :)

then to install it, from a terminal window, goto the
directory you downloaded it to and use

sudo dpkg -install xubuntu-docs_7.10.1_all.deb

OK, I reinstalled that package.
Didn't help.
I don't think the missing files are even in that package.

---

### Post by pthomas on 2008-03-19
Ok, I'm still trying to fix this but so far no one seems to know what to do.
Now I'm wondering, is the main menu "Help" function broken on all current Xubuntu systems?
In other words, if I reinstall the OS will that fix it?
I'd hate to think that Xubuntu is like the old Win 9X systems where the best way to fix them was often to reinstall the OS.

---

### Post by Taino on 2008-03-20
> **pthomas said:**
> OK, I reinstalled that package.
Didn't help.
I don't think the missing files are even in that package.

Thats very odd, i have to wonder if your install CD is all there, or possibly corrupt, you could redownload and reburn a new ISO of it just to make sure and verify its md5 checksum before install.

---

### Post by PeterJS on 2008-03-20
> **Taino said:**
> Thats very odd, i have to wonder if your install CD is all there, or possibly corrupt, you could redownload and reburn a new ISO of it just to make sure and verify its md5 checksum before install.

Both the online listing, and my search of apt package listings, contain no mention of the file that is missing:
```

/usr/share/xubuntu-docs/desktopguide/C/index.html

```
Xubuntu-Docs, might be the right package, but it looks like there's a bug in the default menu that has help associated with the wrong file.

---

### Post by Taino on 2008-03-20
> **PeterJS said:**
> Both the online listing, and my search of apt package listings, contain no mention of the file that is missing:
```

/usr/share/xubuntu-docs/desktopguide/C/index.html

```
Xubuntu-Docs, might be the right package, but it looks like there's a bug in the default menu that has help associated with the wrong file.

That could the case, may have to file a bug report to the Xubuntu team. :)

The specific files that seem to be missing are in this archive [xubuntu-docs_7.10.1.tar.gz]("https://launchpad.net/ubuntu/gutsy/+source/xubuntu-docs/7.10.1/+files/xubuntu-docs_7.10.1.tar.gz")

But that is a "source file" archive.

Inside that archive are the folders for xubuntu gutsy named 
common
debian
libs
xubuntu

inside the "xubuntu one" are contained...
[COLOR="Red"]xubuntu/desktopguide/C/index.html[/COLOR]

and numerous others which were said to be missing based on the Firefox error...

```

File not found
Firefox can't find the file at /usr/share/[COLOR="Red"]xubuntu-docs/desktopguide/C/index.html[/COLOR].

```

Odd that Firefox would be looking for a "source file" in an already packaged ISO and not find it, possibly a bug. :)

---

### Post by the-edmeister on 2008-03-20
/usr/share/xubuntu-docs/desktopguide/C/index.html

Can't you use File > Open File... in Firefox to open that file?

---

### Post by Taino on 2008-03-20
> **the-edmeister said:**
> /usr/share/xubuntu-docs/desktopguide/C/index.html

Can't you use File > Open File... in Firefox to open that file?

The original poster says his directory of /usr/share/xubuntu-docs is empty of files.

---

### Post by pthomas on 2008-03-20
> **Taino said:**
> Thats very odd, i have to wonder if your install CD is all there, or possibly corrupt, you could redownload and reburn a new ISO of it just to make sure and verify its md5 checksum before install.
I just finished rechecking the MD5. It checks OK.

---

### Post by pthomas on 2008-03-20
> **Taino said:**
> The original poster says his directory of /usr/share/xubuntu-docs is empty of files.
No, that directory is not empty. But it does not contain a "desktopguide" directory.

---

### Post by pthomas on 2008-03-20
> **PeterJS said:**
> Xubuntu-Docs, might be the right package, but it looks like there's a bug in the default menu that has help associated with the wrong file.
Do you run Xubuntu and does Help work properly on your system? If so, could you look to see what file what the Help menu entry is supposed to be associated with? Then I guess I could then manually edit the menu to fix it?

---

### Post by Taino on 2008-03-20
> **pthomas said:**
> Do you run Xubuntu and does Help work properly on your system? If so, could you look to see what file what the Help menu entry is supposed to be associated with? Then I guess I could then manually edit the menu to fix it?

I dont have Xubuntu on this machine but i did run it before, version 7.04 and i didnt have issues with the "help system" seems to be a "gutsy 7.10 issue" maybe.

> **pthomas said:**
> No, that directory is not empty. But it does not contain a "desktopguide" directory.

Could try pulling the "desktopguide" directory out of [xubuntu-docs_7.10.1.tar.gz]("https://launchpad.net/ubuntu/gutsy/+source/xubuntu-docs/7.10.1/+files/xubuntu-docs_7.10.1.tar.gz")  for now and try replacing your missing files if its just a few XML-HTML ones you may be able to fix the issue, but a bug report should be filed with the Xubuntu team.

Could also try another Xubuntu CD, if you used the LiveCD to install it and have this issue try the AlternateCD to install instead. (LiveCD might have a bug) AlternateCD may be complete, I used the AlternatedCD for 7.04 when i ran Xubuntu on another PC.

AlternateCD for 7.10
Page [link]("http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/")
ISO [link]("http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/xubuntu-7.10-alternate-i386.iso")

---

### Post by pthomas on 2008-03-20
> **Taino said:**
> Could try pulling the "desktopguide" directory out of [xubuntu-docs_7.10.1.tar.gz]("https://launchpad.net/ubuntu/gutsy/+source/xubuntu-docs/7.10.1/+files/xubuntu-docs_7.10.1.tar.gz")  for now and try replacing your missing files if its just a few XML-HTML ones you may be able to fix the issue, but a bug report should be filed with the Xubuntu team.
I downloaded that archive and extracted the desktopguide directory and copied it to the proper location. However, the "index.html" file seems to be missing even in the archive.

> **Taino said:**
> Could also try another Xubuntu CD, if you used the LiveCD to install it and have this issue try the AlternateCD to install instead.
Trying the live CD is an excellent idea. I'll try that and see if it works there. If so, I'll see if I can figure out the difference.

---

### Post by pthomas on 2008-03-20
Well, it turns out Xubuntu Help on the live CD is broken in the exact same way.

I doubt that I'll go to the trouble to file a bug report. I once found a problem where the default terminal program in Xubuntu would crash X with certain Intel integrated video chips. The dev the report was assigned to answered that he didn't use that kind of video in his personal system so it didn't cause a problem for him and he didn't care. He just marked the issue as resolved and closed the report. That was a couple of versions ago and that bug is still there.

That being how bug reports are treated and considering that the devs themselves probably don't need the Help system, experience tells me that filing a bug report on it would be a total waste of time.

Thanks to Taino and PeterJS for your help anyway.

---

### Post by RobertRobert on 2008-03-22
> **Taino said:**
> The specific files that seem to be missing are in this archive [xubuntu-docs_7.10.1.tar.gz]("https://launchpad.net/ubuntu/gutsy/+source/xubuntu-docs/7.10.1/+files/xubuntu-docs_7.10.1.tar.gz")
...
inside the "xubuntu one" are contained...
[COLOR="Red"]xubuntu/desktopguide/C/index.html[/COLOR]
Taino,
That's very odd. I just downloaded the file you specified and xubuntu/desktopguide/C/index.html is nowhere to be found in it. How do you explain that?

---

