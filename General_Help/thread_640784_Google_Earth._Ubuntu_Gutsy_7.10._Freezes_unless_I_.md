---
title: "Google Earth. Ubuntu Gutsy 7.10. Freezes unless I go fresh install first."
date: 2007-12-14
forum: General Help
---

### Post by Roasted on 2007-12-14
I'm using a Toshiba A215-S7422. AMD X2 CPU, 1gb RAM, ATI X1200 graphics card.

If I install GoogleEarthLinux.bin and cd to Desktop and run ./GoogleEarthLinux.bin, it'll reinstall. Afterwards it gives me the option to start where it runs FLAWLESSLY. 

An icon was created on my desktop. That icon won't boot Google Earth right. It'll come up with the splash screen and just freeze after a while. 

I do not know what command I'd type in terminal to get it to run from terminal. I tried googleearth, google-earth, and google earth. Command not found.

The only way I can get it to run again is if I do another install by doing ./GoogleEarthLinux.bin in my Desktop.

How can I get around this?

---

### Post by stchman on 2007-12-14
> **Roasted said:**
> I'm using a Toshiba A215-S7422. AMD X2 CPU, 1gb RAM, ATI X1200 graphics card.

If I install GoogleEarthLinux.bin and cd to Desktop and run ./GoogleEarthLinux.bin, it'll reinstall. Afterwards it gives me the option to start where it runs FLAWLESSLY. 

An icon was created on my desktop. That icon won't boot Google Earth right. It'll come up with the splash screen and just freeze after a while. 

I do not know what command I'd type in terminal to get it to run from terminal. I tried googleearth, google-earth, and google earth. Command not found.

The only way I can get it to run again is if I do another install by doing ./GoogleEarthLinux.bin in my Desktop.

How can I get around this?

Do you have the proper ATI drivers for your card installed?  OpenGL is needed to run google earth.

You can get google earth from the Medibuntu repos.  To install the Medibuntu repos use the following:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

The turorial is on DVD ripping, but just pay attention to the Medibuntu stuff.

---

### Post by Roasted on 2007-12-14
Restricted drivers are in use. For the record, Compiz Fusion is up and fully running smoothly.

I am unsure as to whether or not OpenGL is running. 

I tried installing from the repos by doing sudo apt-get install googleearth. I got the same problem.

I tried with the .bin file to see if it yielded different results. I was excited when it did, but once I shut it off and try to run it again, it won't give me anything different. In order to get it running I must run another ./GoogleEarthLinux.bin

---

### Post by hari_home on 2007-12-31
In case you still have this problem, I did 32-bit Gutsy install because I had too many problems with 64-bit. I used restricted driver for graphics and automatix to install Google. Worked great on Toshiba A215-S7416.

---

### Post by dcstar on 2007-12-31
> **Roasted said:**
> I'm using a Toshiba A215-S7422. AMD X2 CPU, 1gb RAM, ATI X1200 graphics card.

If I install GoogleEarthLinux.bin and cd to Desktop and run ./GoogleEarthLinux.bin, it'll reinstall. Afterwards it gives me the option to start where it runs FLAWLESSLY. 

An icon was created on my desktop. That icon won't boot Google Earth right. It'll come up with the splash screen and just freeze after a while. 

I do not know what command I'd type in terminal to get it to run from terminal. I tried googleearth, google-earth, and google earth. Command not found.

The only way I can get it to run again is if I do another install by doing ./GoogleEarthLinux.bin in my Desktop.

How can I get around this?

You may want to install the **googleearth-package** package and then (in a terminal):

```
make-googleearth-package
```

This will download the latest googleearth.bin file and then create a .deb package that you can install (like any other Ubuntu package).

The .deb will set up all the correct menu items etc. and you should have a usable application.

This will even create a 64bit .deb if you use the "--force" option (for those using this version of Ubuntu).

---

### Post by VictorR on 2008-01-04
> 
You may want to install the googleearth-package package and then (in a terminal):
Code:
make-googleearth-package
This will download the latest googleearth.bin file and then create a .deb package that you can install (like any other Ubuntu package).

I tried this and failed. Seems Google had change something, so I got a message:
> ~$ make-googleearth-package
--09:24:10--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.255.91
Connecting to dl.google.com|72.14.255.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:24:10 ERROR 404: Not Found.

Could not download Google Earth! (You may need to use --file)


---

### Post by dcstar on 2008-01-05
> **VictorR said:**
> I tried this and failed. Seems Google had change something, so I got a message:

In a terminal:
```
gksudo gedit /usr/bin/make-googleearth-package
```

Change the line to:
GoogleEarth_bin_URL="http://dl.google.com/earth/client/current/GoogleEarthLinux.bin"

Save the file and run everything again (I wish someone would fix that package.......)

---

### Post by Mike Atnip on 2008-01-05
> **dcstar said:**
> In a terminal:
```
gksudo gedit /usr/bin/make-googleearth-package
```

Change the line to:
GoogleEarth_bin_URL="http://dl.google.com/earth/client/current/GoogleEarthLinux.bin"

Save the file and run everything again (I wish someone would fix that package.......)

I am having the same problems.
First I downloaded the bin from Google EArth, setup went ok.  Got the GE icon on the desktop.  When I click it, the GE splash screen comes up briefly, the screen blinks a couple of times, displays some startup lines, then sends me to the Ubuntu login screen.  And I log in to a fresh desktop.

So I tried downloading the GE package maker with synaptic (and with apt-get).  Whenever I try to install this, I get a message to put the Gutsy 7.10 CD into my drive so it can copy something.  I do so, but it does not do anything but tell me I cannot install that package.

Sigh...
Then I tried the medibuntu download.  Same thing.
Perhaps I need to uninstall everything I have done so far and start from... where???
I am using Ubuntu 7.10 on a Dell Inspiron 1000 with 512 RAm 2.4g celeron.
Help?!

---

### Post by lsutiger on 2008-01-06
where is the deb created? I did a locate google*.deb and got notta in return

---

### Post by VictorR on 2008-01-06
Thanks, dcstar, it works.
I had to de-install the existing version of GoogleEarth before a newly created .deb file could proceed successfully.
BUT I am still confused :confused: - it is supposed to install version 4.2.205, while I still have 4.2.198, the same I had before. Actually the installation from .bin went smoothly as well, but the location of the GE files differ from what was stated in the Google web-site, and the version is still 4.2.198. 
Any ideas?

---

### Post by dcstar on 2008-01-07
> **VictorR said:**
> Thanks, dcstar, it works.
I had to de-install the existing version of GoogleEarth before a newly created .deb file could proceed successfully.
BUT I am still confused :confused: - it is supposed to install version 4.2.205, while I still have 4.2.198, the same I had before. Actually the installation from .bin went smoothly as well, but the location of the GE files differ from what was stated in the Google web-site, and the version is still 4.2.198. 
Any ideas?

Don't know, my version is 4.2.0205.5730 - that returns as the latest when I do "Help-Check for updates online".

Delete the downloaded .bin file to force it to download the latest version when you run the package process again.

---

### Post by dcstar on 2008-01-07
> **lsutiger said:**
> where is the deb created? I did a locate google*.deb and got notta in return

In the directory where you ran the command - if it completed successfully.

---

### Post by VictorR on 2008-01-07
Finally I got it. I removed everything from everywhere what could be related to Google Earth, then installed it from freshly downloaded GoogleEarthLinux.bin.
Now I have version 4.2.205.5730.:guitar:

Thanks very much!

---

