---
title: "Installing programs (Skype, specifically)"
date: 2005-10-21
forum: General Help
---

### Post by karoolis on 2005-10-21
Ok, I'm a total noob at Linux. Anyway I installed KUbuntu and I want to add some programs. The problem is don't know how :mad: . Can anyone giove a step-by-step how to install or uninstall a program? (i want to install Skype)

---

### Post by wanger123 on 2005-10-21
Hey karoolis, you need to spend a lot of time reading this:
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
and this:
[http://www.kubuntu.org.uk/docs/kquickguide/C/index.html](http://www.kubuntu.org.uk/docs/kquickguide/C/index.html)

cheers
wanger

---

### Post by shakin on 2005-10-21
[QUOTE=karoolis]Ok, I'm a total noob at Linux. Anyway I installed KUbuntu and I want to add some programs. The problem is don't know how :mad: . Can anyone giove a step-by-step how to install or uninstall a program? (i want to install Skype)[/QUOTE]

I have never installed Skype, but their web site has a Debian repository that you might want to try. From a command line, run 'sudo kate /etc/apt/sources.list'. This will open a text file of repositories. At the bottom, paste 'deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free' (no quotes). Now open Synaptic or Adept from the menu and search for skype. It should show up and let you install it. This should also automatically keep skype updated to the latest version.

If for some reason the Debian version won't work on Kubuntu, you can download the "Static binary tar.bz2 with Qt 3.2 compiled in" version from skype.com. With that you should just extract it to a place such as /opt/skype and run it from there.

For other software, simply run Synaptic or Adept and search for what you want.

---

### Post by GoldBuggie on 2005-10-21
To install skype:
Go to their webpage. Download the compressed file. Extract the files to let's say ~/Skype. Go to that directory and type ./skype. That's it!!! 

There is no compiling or anything. You will get a nice all ready to go program. Then if you want to move it to somewhere else then maybe /usr/share/apps is a good suggestion since other software are there. 

Have been using skype to call home for a month now. Works great!

---

### Post by casper_2095 on 2005-10-21
> Download the compressed file.

Which one?

The debian package, or
the 'dynamic tar requiring qt', or
the 'static tar with qt'
??

---

### Post by casper_2095 on 2005-10-22
Hey, you're right.
I took the "static" version and it works! 
 
Just unzip and type "./skype &" in that directory.  So easy it is seriously disturbing.

(I did check that the microphone was working first with   applications->sound->sound recorder.)

---

### Post by tamskp on 2005-11-02
when extracting the compressed folder - where is it best to put it, in your home directory or somewhere else?

---

### Post by jeremy on 2005-11-02
It is MUCH easier to get the .deb from [http://www.ubuntuforums.org/showthread.php?p=442039#post442039](http://www.ubuntuforums.org/showthread.php?p=442039#post442039)
then right click on it and choose "Kubuntu package menu -> Install package".

---

### Post by Thorsten on 2005-11-02
[quote=tamskp]when extracting the compressed folder - where is it best to put it, in your home directory or somewhere else?[/quote] 
If there is only one account (user) on the system, it doesn't make a whole lot of difference, but conceptionally, Linux (like UNIX-related systems in general) is a multi-user system which basically knows three different kinds of software:

1. Software that came with the system (in this case [k]ubuntu) or that has been installed using the system's installation/update procedure. This software lives in /usr/ and its appropriatesub directories such as /usr/bin/ for executable, /usr/lib /for shared libraries (think DLL on Windows) etc. This this software is managed by the system's update/installation tool (e.g., synaptic, kynaptic, apt-get etc.), it's best not to mess with it manually.

2. Software that is installed manually by the system administrator (user "root") and that should be available to all users generally lives in either /usr/local/ or /opt/. (The reason that both /usr/local/ and /opt/ exist is purely historical. You can choose whichever you like.)

3. Software that is installed by a user without administrator (or "root") priviledges can only live in that users home directory, e.g. /home/tamskp/ or a subdirectory thereof. (BTW In the UNIX/Linux world, "folders" are generally called "directories." It's exactly the same thing.)

I hope that it is clear that Option 2 really is what's appropriate for your purposes. E.g., to install a downloaded skype package, you could do the following. Open a konsole and type:

```

cd /usr/local
sudo su
tar xvfj /home/tamskp/WHATEVER/skype_staticQT-1.2.0.17.tar.bz2
ln -s skype-1.2.0.17 skype
cd bin
ln -s ../skype/skype
exit

``` 
The last four lines of the above aren't really necessary, but they create a symbolic directory /usr/local/skype that points at /usr/local/skype-1.2.0.17 and another link /usr/local/bin/skype that points to the executable program.

If /usr/local/bin is part of your PATH environmet variable (which is usually a good idea), you can start skype simply by typing skype in konsole or Alt-F2 or sth like that. (Of course, you can alway create a menu item or a desktop icon.) 

The reason for the link from /usr/local/skype to /usr/local/skype-1.2.0.17 is the following: If a new version of Skype comes out (let's say, 1.3.1), all you'd have to do is something like
```

 cd /usr/local
 sudo su
 tar xvfj /home/tamskp/WHATEVER/skype_staticQT-1.3.1
rm skype
ln -s skype-1.3.1 skype
 exit
 
``` i.e., extract the new package in /usr/local and change the link /usr/local/skype to point at the new directory, e.g., /usr/local/skype-1.3.1 skype. You **wouldn't** have to change any icons and menu entries that point at /usr/local/bin/skype. In fact, you could easliy switch back and forth between the two versions simply by changing the directory /usr/local/skype points to.

HTH,
Thorsten

---

### Post by skorange on 2006-02-23
thanks! very informative post, mate ;)

---

### Post by aysiu on 2006-02-24
[There are instructions on the Wiki](https://wiki.ubuntu.com/SkypeHowto#head-53c7626aec330bf6e107f272f2a5a7c8506181f9)

---

