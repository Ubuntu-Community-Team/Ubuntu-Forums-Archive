---
title: "Error when I attempt to install Firefox"
date: 2005-10-20
forum: General Help
---

### Post by TheSaladCaper on 2005-10-20
I wanted to upgrade to the latest version of Firefox (1.0.7), but whenever I attempt to do so, I get an error saying "Couldn't open xpistub library"... I can't make head nor tail of this...

---

### Post by mike1138 on 2005-10-22
I have the same issue. Some help would be grately appreciated!

---

### Post by mlomker on 2005-10-22
1.0.7 is the default in Breezy.  How are you going about trying to upgrade?

Post the output of:

```

sudo apt-get upgrade

```

---

### Post by mike1138 on 2005-10-22
From my attemt to sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  firefox firefox-gnome-support mozilla-firefox-gnome-support
The following packages will be upgraded:
  mozilla-firefox
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 37.1kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mozilla-firefox
Install these packages without verification [y/N]? y
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main mozilla-firefox 1 .0.7-0ubuntu15
  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main) /binary-i386/mozilla-firefox_1.0.7-0ubuntu15_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

---

### Post by mlomker on 2005-10-23
> Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main)  

The mirrormax repos were taken offline a few weeks ago. 

If you remove references to them from your /etc/apt/sources.list file (or uncheck them in Synaptic) then it'll download from the Ubuntu repo instead.

---

### Post by mike1138 on 2005-10-23
I've removed all references to the above repos, and update seemed to get through, but I'm given this error:

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  mozilla-firefox mozilla-firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8856kB of archives.
After unpacking 24.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 70115 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.debE: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by mlomker on 2005-10-23
You can't have two copies of firefox installed.  You'll need to remove **firefox** (the mirrormax version) before installing **mozilla-firefox** (the Ubuntu one).

---

### Post by dbernar1 on 2005-10-23
Yay for backports! 

Another successfully borked system, and more requests for help. Good work on explaining to the newbies how to use backports...

dabaR

---

### Post by dbernar1 on 2005-10-23
This is how you should use backports. Add it to your sources.list file with a # in front of it, so it is commented out, and not used.

Then, you hear there is this version of a program you can not live without for some reason, and you go to your sources.list and remove the #, save, and reload in synaptic, or aptitude|apt-get update. You then get the program you want, and only that program, by using synaptic, or aptitude|apt-get install. Then you again go to your sources.list and put the # back, to comment it out. Then you reload/update again. 

Otherwise, you have a system full of unstable packages, and are just waiting for your apt system to complain about things like this. 

So, learn how to use backports before you use them to bork your system.

On another note, whenever you are posting about trouble with installing something, these are mandatory follow-ups:
1) a post of your /etc/apt/sources.list file to pastebin.ubuntulinux.nl, post the URL you get from pastebin in your request for help.
2) a post of what your error that you get, or output of the apt-get|aptitude command.

Those are basic, otherwise how would I know what your system for installing things looks like, and what the error you get is?

You can also post the above to just to the forums, I am not sure how much text they allow, but I think plenty. 

As for your error above, first poster, I suggest you try removing backports(# in front of the line) from your sources.list file, then reload/update your package list. If you get errors, run sudo apt-get -f install and see whether that runs with no errors. If you get any errors, post them, so we can know what to fix.

dabaR

---

### Post by mike1138 on 2005-10-23
I have removed the mirrormax version and installed the ubuntu version. 

i'm in /home/me, type <firefox>, and nothing happens. applications->internet->firefox launches the program but a window never shows up. all that happens is that a box on the toolbar is created, but then nothing appears.

as far as borking my system, most of the time i try to follow advice of people smarter than me. only way to learn is to try, right?

i have expressed thanks before, and will do so again, to all those who support n00bs like me in fixing these problems: thank you for all your effort and help.

---

