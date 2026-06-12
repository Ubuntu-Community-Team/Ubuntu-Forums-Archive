---
title: "Firefox 1.0.2 on Warty?"
date: 2005-03-29
forum: General Help
---

### Post by jnoreiko on 2005-03-29
I'd like to upgrade my version of firefox, as the current one seems a bit buggy (eg searchplugins won't install), and I'm used to the newer features such as the search bar and live bookmarks.

I've got the installer from Mozilla.org.
Now what?
Which folder do I tell it to install to?

---

### Post by bored2k on 2005-03-29
you can install it wherever you want .
It will probably install in firefox-installer, wich is the directory you are running it through.

It won't substitute the one on /usr/lib this way, but you'll have your brand new Firefox (not sure if installing it on /usr/lib will overwrite the old one without errors, but you could set install directory to /usr/lib/mozilla-firefox and hope it goes ok ;)) .

edit > I just checked both directories and I saw:
> ls /usr/lib/mozilla-firefox/
chrome             libjsj.so           libxpistub.so
components         libmozjs.so         mozilla-firefox-xremote-client
components.ini     libnspr4.so         plugins
defaults           libnss3.so          regchrome
defaults.ini       libnssckbi.so       regxpcom
extensions         libplc4.so          res
firefox            libplds4.so         run-mozilla.sh
firefox-bin        libsmime3.so        searchplugins
greprefs           libsoftokn3.chk     xpcshell
icons              libsoftokn3.so      xpicleanup
libgkgfx.so        libssl3.so          xpidl
libgtkembedmoz.so  libxpcom_compat.so  xpt_dump
libgtkxtbin.so     libxpcom.so         xpt_link 
and > ls Files/firefox-installer/
browserconfig.properties  icons               libxpcom.so
chrome                    install.ini         libxpistub.so
components                install.log         license.txt
components.ini            libmozjs.so         mozilla-xremote-client
config.ini                libnspr4.so         plugins
defaults                  libnss3.so          registry
defaults.ini              libnssckbi.so       res
extensions                libplc4.so          run-mozilla.sh
firefox                   libplds4.so         searchplugins
firefox-bin               libsmime3.so        watermark.png
firefox-installer         libsoftokn3.chk     xpi
firefox-installer-bin     libsoftokn3.so      xpicleanup
greprefs                  libssl3.so
header.png                libxpcom_compat.so 

Meaning? looks like you could overwrite without problems (haven't tested it though) .

---

### Post by lorap on 2005-03-30
hi friends!
i've done it myself but every time i've run it the terminal window was popuped.
pavel

---

### Post by Jagera27 on 2005-03-31
I am having trouble getting Firefox 1.0.2 to install into Warty and stay there. I unzipped and extracted it from the Home directory and it comes up nicely with the Google Firefox wrapped around the globe. But when I close it and re-click on the icon in  the toolbar at the top, only the old 0.9.3 version appears. Logging out and restarting Ubuntu doesn't help. Where's it gone??

thanks

Nick   :?:

---

### Post by bored2k on 2005-03-31
[QUOTE=Jagera27]I am having trouble getting Firefox 1.0.2 to install into Warty and stay there. I unzipped and extracted it from the Home directory and it comes up nicely with the Google Firefox wrapped around the globe. But when I close it and re-click on the icon in  the toolbar at the top, only the old 0.9.3 version appears. Logging out and restarting Ubuntu doesn't help. Where's it gone??

thanks

Nick   :?:[/QUOTE]
 You installed it in firefox-installer directory, not system wide.
So go to /home/jagera27/firefox-installer [speculating here] and run firefox from there .

---

### Post by jnoreiko on 2005-03-31
I've got it to work by installing in my home folder and making a new panel icon for it.
Oddly, now that's done, the regular icon launches something that's firefox 1.0.2 too -- though I'm not sure if that's a new instance of the one in my folder, just a new window of it, or the broken 1.0.2 I tried to install as root that now magically works...

I've enabled warty-backports as described in the ubuntu guide -- this might be the easiest way to update firefox, as it has 1.0.2, but apt-get said "Conf mozilla-firefox (1.0-2ubuntu4-warty99 Ubuntu Stable Backports for Warty (4.10):warty-backports)" when I ran it in simulation mode.

---

### Post by goodboy on 2005-04-02
i try to install new Firefox 1.0.2. But i get Fatal Error (-618) Couldn't open xpistub library. Where i can this library? And what should i do? Can it be fixed somehow?

---

### Post by jnoreiko on 2005-04-02
I managed to install a newer firefox with apt-get from warty-backports, though I was wrong above when I said it was 1.0.2 -- the version number listed by apt is 1.0-2 (and then a load of stuff about being a backport), and once it runs it says it's 1.0.

If you've tried to run the mozilla installer with sudo and install to /usr/lib, you'll need to uninstall with apt and then manually remove the folder before trying again, otherwise it'll still be broken.

---

### Post by goodboy on 2005-04-02
I tried to install just clicking on .bin file. It worked fine, because of error it didn't installed. 

Sorry, i am just a newbie in Linux :)

---

### Post by goodboy on 2005-04-02
i've done it :) I don't know how, but i did :) and it works :)
I installed it in the same folder where the 1.0 was ... 
/usr/lib/mozilla-firefox ... everything works fine

---

### Post by Alex4R on 2005-04-04
Sorry, this thread is a couple days old... But here is what I did. First, I downloaded firefox 1.0.2, to /usr/lib/mozilla-firefox/firefox-installer. Then I deleted the files in the /usr/lib/mozilla-firefox folder. Next I ran the installer, and chose to install in the /usr/lib/mozilla-firefox directory. It installed, and bingo, it works from the original links on the taskbar and applications menu.

 8)

---

### Post by Psquared on 2005-04-04
I don't know why, but mine upgraded using Synaptic with backports enabled. I am definitely running v. 1.0.2.

---

