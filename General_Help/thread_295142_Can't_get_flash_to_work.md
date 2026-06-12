---
title: "Can't get flash to work"
date: 2006-11-07
forum: General Help
---

### Post by thecynicality on 2006-11-07
I've tried to get flash for firefox 2 ways, the first thing i tried was downloading the file from adobe and using the "./flashplayer-installer" command, it looked like it worked but i still can't load flash objects online it tells me to download flash.

The second thing i tried was using the sudo commands: 

sudo apt-get install flashplugin-nonfree;
sudo apt-get install libflash-mozplugin

that also installed fine, but i still can't view flash objects.

Does anybody know whats going on?

---

### Post by pay on 2006-11-07
Are you running i386 or amd64? If you are on amd64 then you need a 32bit firefox to run the 32bit flashplayer.

---

### Post by swj on 2006-11-07
1. Simply download the linux beta.

2. create a folder named plugins in .mozilla

3. extract libflashplayer.so in .mozilla/plugins


I have never understood why this is even a package. :-?

---

### Post by thecynicality on 2006-11-07
The files are in the plugins folder, i checked, they installed fine, but it still doesn't work.

---

### Post by taurus on 2006-11-07
So, the new flash 9 is in ~/.mozilla/plugins.  Restart firefox and in the address field, check it with 

```
about:plugins
```
Do you see flash 9 in there?

---

### Post by thecynicality on 2006-11-07
I see flash 7, every time i tried to download 9 it redirected me to 7, is that the problem?

---

### Post by taurus on 2006-11-07
> **thecynicality said:**
> I see flash 7, every time i tried to download 9 it redirected me to 7, is that the problem?
Go into /usr/lib/firefox and remove libflashplayer.so...

```
sudo rm /usr/lib/firefox/libflashplayer.so
```
Then, download version 9 from here [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html), Download Installer for Linux (GZ, 2.48MB), and unpack and move it to /usr/lib/firefox again...

```

cd Desktop
tar xvzf FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55
sudo cp libflashplayer.so /usr/lib/firefox

```
Now, fire up firefox again and type

```
about:plugins
```
to see if you have Flash 9 this time...

---

### Post by Crashmaxx on 2006-11-07
I have the same problem. I did a fresh install of edgy, using firefox 2 and no flash. Flash 7 will install and work, but flash 9 won't work regardless.
> **taurus said:**
> Go into /usr/lib/firefox and remove libflashplayer.so...

```
sudo rm /usr/lib/firefox/libflashplayer.so
```
Then, download version 9 from here [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html), Download Installer for Linux (GZ, 2.48MB), and unpack and move it to /usr/lib/firefox again...

```

cd Desktop
tar xvzf FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55
sudo cp libflashplayer.so /usr/lib/firefox

```
Now, fire up firefox again and type

```
about:plugins
```
to see if you have Flash 9 this time...
Didn't work for me. Any other ideas?

---

### Post by taurus on 2006-11-07
Did you restart firefox?

---

### Post by Crashmaxx on 2006-11-07
I got it fixed. First, his code is wrong, the second section should be:
```

cd Desktop
tar xvzf FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55
sudo cp libflashplayer.so /usr/lib/firefox/plugins

```
Note the last line, now it is the plugins folder in firefox, and not the firefox folder itself.

Second, I'd recommend doing:
```

locate libflashplayer.so

```
Before any of the rest of this, so you can replace all the flash plugins on your system, not just the one firefox should be using.

Hope that helps someone else.

---

### Post by taurus on 2006-11-07
Otherwise, just move the darn thing to ~/.mozilla/plugins...  :rolleyes:

---

### Post by Flying caveman on 2006-11-08
yeah! I put it in /usr/lib/firefox/plugins and  ......../mozilla/plugins/ and .../mozilla-firefox/plugins/            just be be sure ;-)

---

### Post by Tarnic on 2006-11-08
I have done all of these things to try to get flash to work... but everytime I go to a page with a flash file, Firefox just crashes... This only happened when I upgraded to Edgy. Back on Dapper Drake I ran Firefox 2.0 and got flash player to work fine. It could be my video drivers messing up but I don't know... Help Please

Also:
If you look at the system requirements page ([http://labs.adobe.com/technologies/flashplayer9/releasenotes.html](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html)) for Flash Player 9 for Linux it says it is for Firefox 1.5.0.7

---

### Post by vidak on 2006-11-08
what about automatix?

---

### Post by thecynicality on 2006-11-08
> **Tarnic said:**
> I have done all of these things to try to get flash to work... but everytime I go to a page with a flash file, Firefox just crashes... This only happened when I upgraded to Edgy. Back on Dapper Drake I ran Firefox 2.0 and got flash player to work fine. It could be my video drivers messing up but I don't know... Help Please

Also:
If you look at the system requirements page ([http://labs.adobe.com/technologies/flashplayer9/releasenotes.html](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html)) for Flash Player 9 for Linux it says it is for Firefox 1.5.0.7


"Note: if firefox crashes when visiting a website with flash content, do the following:

sudo gedit /usr/bin/firefox

and add the following line as last but one line of the file:

export XLIB_SKIP_ARGB_VISUALS=1

Now firefox shouldn't crash anymore. (Launchpad bug report: [1])

    * Restart Mozilla Firefox "

- From the ubuntu guide, hope it helps.

---

### Post by vidak on 2006-11-08
> **thecynicality said:**
> "Note: if firefox crashes when visiting a website with flash content, do the following:

sudo gedit /usr/bin/firefox

and add the following line as last but one line of the file:

export XLIB_SKIP_ARGB_VISUALS=1

Now firefox shouldn't crash anymore. (Launchpad bug report: [1])

    * Restart Mozilla Firefox "

- From the ubuntu guide, hope it helps.

As I saw on the forums this workaround helped in a lot of cases (for me it didn't)
If you experience the same thing, try to remove every flash-package, and install flash9 using automatix. As far as I remember there was a font package which was also installed (probably this was what solved the problem)

ps.: this thread [http://ubuntuforums.org/showthread.php?t=286069&highlight=flash+firefox](http://ubuntuforums.org/showthread.php?t=286069&highlight=flash+firefox) may also help

---

### Post by Flying caveman on 2006-11-08
I had the same problem when I upgraded to Edgy.  I used Automatix2 to install Flash.  But actually I had to un-install Automatix2 first and then install the Edgy version of Automatix2.

---

