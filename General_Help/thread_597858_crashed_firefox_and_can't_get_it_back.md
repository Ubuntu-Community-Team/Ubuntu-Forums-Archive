---
title: "crashed firefox and can't get it back"
date: 2007-10-30
forum: General Help
---

### Post by uberMongo on 2007-10-30
hello everyone.
first of all I must say that I'm a noob at this, so please bear that in mind when/if you post your awnsers.

second: HEEEEEELP!!!

I was messing around firefox and decided to install the Stylish extension ( [http://userstyles.org/styles/1084](http://userstyles.org/styles/1084) ). I restarted FF and added the line ''body { overflow-y: hidden ! important; overflow-x: auto ! important; }'' to the Stylish preferences. When I tried to restart FF again it simple shows up in the Window List as ''Starting Firefox'' (or something like that) and disapears.

I tried uninstalling/reinstalling with the Synaptic Package Manager and with apt-get (probably the same thing). Both didn't work.
Tried downloading from mozilla and installing but also with no good result.
Finally I, stupidly, decided to remove every folder and file, related to Firefox and Mozilla, by hand (desperate times...) and reinstalling again with the same result from previous atempts.

So here I am now, extremelly ashamed for not asking you guys first about this.
Firefox won't start, I probably deleted important files and I'm using the Live CD to post this.

Can anyone help me get FF back please? I'm about to do a full install of Ubuntu to solve the problem.

Thank you for all the help you can give me.

p.s.: I'm running Ubuntu 7.04 Feisty Fawn, Firefox was 2.0.0.8

---

### Post by AlexThomson_NZ on 2007-10-30
Did you try installing FF from the .tar.gz from the Mozilla site (rather than using Ubuntu reposity)?  What does is the output say when running from command-line in the actual (new) FF directory (rather than the version the symlink points to in the /usr/bin directory)

---

### Post by uberMongo on 2007-10-30
I tried installing like that but I don't know how to do it.
there's a "readme.txt" file in that folder but all it says is to go to [http://getfirefox.com/releases/](http://getfirefox.com/releases/), from there I go to release notes and then to Installing but all it says is that somethings will be overwriten and other won't.
if I run the file "firefox" the darn thing starts (using it now) but I see nothing to get the instalation going.


can someone give the step-by-step instructions please?

---

### Post by AlexThomson_NZ on 2007-10-30
Installing it is pretty simple, what I do (may or may not be 100% the best way, but is what I have done since before firefox 1).  Assuming that .tar.gz is downloaded onto the desktop:

In a terminal run:
```

cd ~/Desktop
tar -xvf firefox-2.0.0.8.tar.gz
sudo cp -r firefox /opt
cd /opt/firefox
./firefox &

```

That should open the just installed FF with no errors.

Is that what you were after?  (There is no 'installation' script or icon as such)

---

### Post by TeeAhr1 on 2007-10-30
Before you go reinstalling, here's a quick and dirty solution: go into your home folder, select "see hidden files" (or whatever, it's in the View menu), and delete the .mozilla directory.  That'll wipe all your FF preferences and customizations, and you should be able to just start over.  If that doesn't do it for you, go into Synaptic and select "reinstall" for Firefox.

---

### Post by uberMongo on 2007-10-30
done that and created a link and it works, but Firefox is still marked as "not installed" in the Synaptic Package Manager. [Screenshot here]("http://pwp.netcabo.pt/0231644101/screenshot1.png")

and if i run:
```
sudo apt-get install firefox
```
I get the following error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9272kB of archives.
After unpacking 29.4MB of additional disk space will be used.
(Reading database ... 127645 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.8+1nobinonly-0ubuntu1_i386.deb) ...
Replaced by files in installed package libnss3 ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.8+1nobinonly-0ubuntu1_i386.deb (--unpack):
 unable to create `./usr/lib/firefox/firefox': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.8+1nobinonly-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

FF is running now but I'm not to confident that it will keep running correctly

---

### Post by uberMongo on 2007-10-30
> **TeeAhr1 said:**
> Before you go reinstalling, here's a quick and dirty solution: go into your home folder, select "see hidden files" (or whatever, it's in the View menu), and delete the .mozilla directory.  That'll wipe all your FF preferences and customizations, and you should be able to just start over.  If that doesn't do it for you, go into Synaptic and select "reinstall" for Firefox.

nope, still no dice... same problem... and, as you can see in the screenshot I posted fire is marked as not installed, so there is no "reinstalling" it, thanks anyway

---

### Post by uberMongo on 2007-10-31
ok, I solved it, I think!!

I was using FF when I realised that I couldn't view quicktime movies, so I did a apt-get install mozilla-mplayer and (don't ask me how) the missing icon in the Main Menu reapeared by itself, I recieved a messege from the Notification Area saying that Firefox had just been installed or update and FF is now listed as "installed" in the Synaptic Package Manager. :D 
if anyone know why this happened please share it, I'd reeeaaaly like to know why!

again, don't ask me how, but everything appears to be working fine now.
if I notice any kind of strange behaviour I'll post it here.

thanks for the help guys.

---

### Post by nowshining on 2007-10-31
u could of removed the lines u input last time or restored it from a backup - the backups all end with a ~ in their name and are auto created and hidden. OR you  could of opened up a terminal and typed firefox --profilemanager and created a new profile and restored ur bookmarks from the .mozilla folder.

---

### Post by uberMongo on 2007-10-31
thanks for the tips nowshining.

---

