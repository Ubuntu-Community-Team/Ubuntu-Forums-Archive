---
title: "[SOLVED] hacking screensavers"
date: 2008-04-18
forum: General Help
---

### Post by mr_adam on 2008-04-18
Hi,
    I want to have a play around with the screensavers
on xscreensaver, but it's been a while since i've done 
any programming. Specifically, I don't know how to handle
the linking within the xscreensaver package. 

I downloaded the newest version with the source code, but as far as 
compiling (and running) individual screensavers I'm a bit in the
dark. If I compile the whole package (which I haven't done yet), will
that sort out the links to header files etc? 

I have a nasty feeling I'll be forced to do a big research mission 
on makefiles, but if there's an easier way, please let me know.

---

### Post by ibuclaw on 2008-04-18
You can download the source-code for xscreensaver using apt-src.
That is a good app to get you started.

```

sudo apt-get install apt-src

```
Then once it is finished, enable "Source Code" in your repository.
[[IMG]http://img384.imageshack.us/img384/4449/screenshotsoftwaresourcev6.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotsoftwaresourcev6.png)

Update your repository and "apt-src" xscreensaver
This will download the source packages in your current folder, so making a separate folder for them is good practise.
```

mkdir src
cd src
sudo apt-get update
sudo apt-src install xscreensaver

```
All dependancies to compile xscreensaver and its demo screensavers will be auto installed too. You'll notice a few dev packages being installed.
This includes libgle3-dev quilt x11proto-screensaver-dev and others.

Once finishes, you'll be left with the source folder along with the original tarballs and dsc file.
The latter we don't need so we will remove them.
Also, we'll need to change the ownership of the folder to you to, as it is currently set as root.
```

sudo rm xscreensaver*.diff.gz
sudo rm xscreensaver*.orig.tar.gz
sudo rm xscreensaver*.dsc
sudo chown yourname:yourname xscreensaver* -R

```
Now you can enter the directory and view the code.

If you want to build the Makefiles for it, type in:
```
 ./configure 
```

All screensavers are in the "**hacks**" folder.
To compile them, you'll need the header files from the utils folder from within the source folder.
And you'll probably need a Makefile, as the "include" list is very long:

I haven't yet managed to compile any of them myself in my half hour of trying it.

But some hints can be found in the "README.hacking" file.

Regards
Iain

---

### Post by mr_adam on 2008-04-19
Thanks for that, I think I have the overall package installed 
and so forth. The problem I have now is compiling my own 
edited screensavers. As you say, there are a lot of files that
need to be included at compilation. 

I seem to be getting mainly errors along the lines of
  undefined reference to 'XQueryTree'
so I'm guessing some X11 library is missing or not found.
Any ideas on identifying the problem? 

-- Actually, scratch that, tried putting -lX11 in the gcc command and it got rid of the 
'X' related errors, but still many undefined references to random stuff. Still need to 
know how to find where these come from.

Regards 
Adam

---

### Post by mr_adam on 2008-04-19
Okay
It actually turns out to be a problem with how I 
set up the files I think.
Evidently the makefile in the hacks directory 
was the wrong one, the utils makefile had 
ended up there by mistake (I think). Not sure how 
I managed that one.

Anyway, I downloaded the one suggested from
the ubuntu repository (4.23) and the individual hacks
make with no problem.
Thanks

---

