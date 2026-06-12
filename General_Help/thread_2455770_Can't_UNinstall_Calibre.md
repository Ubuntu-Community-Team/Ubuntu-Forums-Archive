---
title: "Can't UNinstall Calibre"
date: 2020-12-27
forum: General Help
---

### Post by 0georgebaldwin0 on 2020-12-27
Hi,

I posted here recently when I was trying to install a light-ish more up-to-date version flavour of Ubuntu than my excellent but now venerable 16.04 Mate. I tried Budgie which looked fabulous, was very fast but just wouldn't be nice to me when I wanted to do even fairly simple stuff. A number of kind and patient people here gave me a lot of help but I just couldn't make it jump through the hoops...so I gave up and installed 20.04 Mate. It's not as pretty and 5 or so seconds slower to boot...but everything WORKS!....at least it did until today.

Truthfully everything that I need still does work but I've come across a strange (to me) situation in that I can't seem to uninstall Calibre. I installed it through the "Software" app (version 3.36.1) but I realise that I don't need or want an e-library manager and just need a simple cataloguer instead....so I tried to uninstall it, again through the Software app but all I get is a message saying "Unable to Remove Calibre, no packages to remove".  It's lying to me as Calibre is still there and functions perfectly but why is it a-sayin' that thar ain't no packidges?

This is obviously a PIBCAK issue but once again I'd be very grateful for any help.

MTIA

gb

---

### Post by TheFu on 2020-12-27
apt package or snap package?

```
sudo apt remove 
```
or
```
sudo snap remove
```

An **apt search** shows only the apt version on my 20.04 system. No snap version.

---

### Post by ajgreeny on 2020-12-27
What does the command ```
which calibre
``` show as output, and once you have that output run command ```
ll <output from first command>
``` editing that output line to what you actually see from first command, of course.

I always install calibre direct from the website [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux) with their binary install command which put the whole application in /opt but has a linked executable file /usr/bin/calibre to the actual executable /opt/calibre/calibre

I tell you this as it may be that you have all of calibre installed in /opt; you can quickly find out by running command ```
locate calibre
```

If you find that just about all of calibre is installed in /opt I suspect you can simply remove the /opt/calibre folder.  It will, if installed the way I do, leave broken links to several files but they will be of little if any consequence and you could remove them manually after finding them with a repeat of the ```
locate calibre
```

---

### Post by HermanAB on 2020-12-28
Howdy, I learned decades ago never to uninstall anything.  The problem is that the uninstall functions are the poor untested step children of the install functions and they frequently make a big mess of it.  A few unused programs won’t hurt, but some erroneously removed library can totally break your system. So I just don’t.

---

### Post by 0georgebaldwin0 on 2020-12-29
OK, thanks to TheFu, AJgreeny and HermanAB:

3 excellent suggestions and my results on trying them-
1) The Fu
"sudo apt remove calibre" gives me 'Package 'calibre' is not installed, so not removed'
"sudo snap remove calibre"     "        'snap "calibre" is not installed'

2) AJgreeny
"which calibre"  results in bugger all, just nix,nada,bubkiss...so obviously not a lot of point in trying the "ll" command
"locate calibre" gave 'mlocate not installed'
so Installed mlocate and now "locate calibre" gives me files in /snap, /usr and /var....but nochnage to the outputs from The Fu's suggestions.

3) In the absence of an idiot-proof work-around (or some kind of fast acting and painless poison) I think HermanAB's solution might be the most practical for me....
I did absolutely nothing so absolutely nothing happened. 
I deleted the little Calibre launcher sphincter thingy so at least that annoyance is invisible and I think that maybe this "doing nothing" approach suits my pay-grade to a T.

 The poor untested step-child will have to stay on the streets  for a while longer but still many thank to AJ and the TheFu.

......and a very Happy New Year!!

---

### Post by TheFu on 2020-12-29
I've been running the repo version of Calibre at least 5 yrs, probably 8+ yrs.

Well, how did calibre get installed?  It is a server and a thick-client program.  The server requires some config changes and a restart of the service daemon.  
```
$ sudo apt search calibre
Sorting... Done
Full Text Search... Done
calibre/xenial-updates,xenial-updates,xenial-security,xenial-security,now 2.55.0+dfsg-1ubuntu0.2 all [installed]
  e-book converter and library management

calibre-bin/xenial-updates,xenial-security,now 2.55.0+dfsg-1ubuntu0.2 amd64 [installed,automatic]
  e-book converter and library management
```

So, that leaves 4 other options for installation - direct .deb file, flatpak, appimage, or source files.  None of those would have been automatic. Someone choose to install it and chose the method for that installation.

Calibre isn't a core tool and won't remove core libraries on removal.  There is little to zero danger in removing it, provided a package system was part of the install/removal.  Removal of source-built stuff is often left for the installer to figure out and perform safely. If you aren't good with that, don't bother. Just disable the calibre service startup and forget about it.
```
$ sudo systemctl status calibre-server.service 
&#9679; calibre-server.service
   Loaded: loaded (/etc/init.d/calibre-server; bad; vendor preset: enabled)
   Active: active (exited) since Sat 2020-11-21 16:58:37 EST; 1 months 7 days ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 0
   Memory: 0B
      CPU: 0

Nov 21 16:58:37 istar calibre-server[2605]: Starting Calibre server...
Nov 21 16:58:37 istar systemd[1]: Starting calibre-server.service...
Nov 21 16:58:37 istar systemd[1]: Started calibre-server.service.
```
I'd use the 'stop', then 'disable' then 'mask' options for the **systemctl** command. That's three separate commands. Like this:
```
sudo systemctl **stop** calibre-server.service
sudo systemctl **disable** calibre-server.service
sudo systemctl **mask** calibre-server.service
```
That's the normal pattern to disable any service controlled under systemd. If I wanted it running later and enabled, 
```
sudo systemctl **unmask** calibre-server.service
sudo systemctl **enable** calibre-server.service
sudo systemctl **start** calibre-server.service
```
Simple. The normal pattern.  In the olden-days, we'd find the file in /etc/default/calibre and edit it for "STARTUP=true" or something like that so it would start on boot. Each of those files in /etc/default/ does it a little different, but all have comments.

---

### Post by 0georgebaldwin0 on 2020-12-30
Fu! Thanks for your tenacity:-)

I'm honestly very grateful for your attention and I'm sure that less neurone-challenged people will find your instructions a breeze. 

After many years of "fixing" things that were working ok and then having them work less well (or not at all) I'm now pretty sceptical of my abilities and especially so when it comes to anything modern computer related. My OS days in the sun were when Bill was killing with MSDOS and still had his name on the tin and my skills roughly followed the decline from W3.11 to W7 at which point I saw the light ...or came over to the dark-side, depending on your degree of cynicism. I've been with Ubuntu since 12.04 and can honestly say that because of Ubuntu I've got worse and more ignorant because I no longer have to troubleshoot and reinstall broken stuff every few days or so. 

A very round-about way of explaining why I'm going to opt for your advice "[COLOR=#000000]If you aren't good with that, don't bother. Just disable the calibre service startup and forget about it." [/COLOR]which I've now done, and so all is well.

Thanks again

GB

---

### Post by ajgreeny on 2020-12-30
Had you installed direct from the calibre website at [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux) and run the shown command everything would have been in /opt except for about half a dozen symbolic links to executables in opt (to add the application to the default $PATH).

This means that you can simply remove the calibre folder in /opt recursively without any danger, not something usually recommended, though in this case safe to do.
You would also get calibre-5.8.1 instead of 4.99 from the repos.

---

