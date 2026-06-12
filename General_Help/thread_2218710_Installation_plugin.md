---
title: "Installation plugin"
date: 2014-04-21
forum: General Help
---

### Post by M1k4 on 2014-04-21
Hi,
I would like to install

[LIST]
[*][[IMG]http://www.adobe.com/images/icons/download.gif[/IMG]Download the Linux Flash Player 11.2 Plugin content debugger]("http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz") (TAR.GZ, 7.06MB)
[/LIST]

from [http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

I unzip it but i dont understand the readme

"Installing using the plugin tar.gz:
    o Unpack the plugin tar.gz and copy the files to the appropriate location.  
    o Save the plugin tar.gz locally and note the location the file was saved to.
    o Launch terminal and change directories to the location the file was saved to.
    o Unpack the tar.gz file.  Once unpacked you will see the following:
        + libflashplayer.so
        + /usr
    o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr"

Copy the files to the appropriate location? Manually?!? I will need to change every rights of my system's files!!!???

They say that I can use RPM or standalone
I don't know this things at moment, not my topic's object but if you can tip me one or the other

Thx

---

### Post by dragonfly41 on 2014-04-21
I checked where my plugin is installed ...

```
sudo updatedb
sudo locate libflashplayer.so
```

result:
/usr/lib/flashplugin-installer/libflashplayer.so

---

### Post by waburden-4 on 2014-04-22
I avoided all this crap by installing the Synaptic Package Manager from  the Ubuntu Software Center and then from Synaptic installing the flashplugin-installer. Why the default installation doesn't install this plugin by default is a mystery so that FB flash videos work.

---

### Post by PotatoHead007 on 2014-04-22
I believe that you should just install it from terminal - takes seconds :)

Open terminal, and type:
```
sudo apt-get install flashplugin-installer
```
Then enter your password and follow prompts :) If you are new to Ubuntu, then know that you will not see your password when you type it; this is to prevent peeping people :P Hope i helped :)

---

### Post by Yellow Pasque on 2014-04-22
> **waburden-4 said:**
> Why the default installation doesn't install this plugin by default is a mystery so that FB flash videos work.

Adobe's EULA is to blame, but the installer could certainly ask the user if they want to install it (and make it clear that saying 'yes' means the user accepts the EULA, just as installing the package does).

---

### Post by Yellow Pasque on 2014-04-22
BTW, if you're trying to install a firefox/mozilla plugin manually, you want to put it in ~/.mozilla/plugins (create plugins dir if it does not exist). Do not dump files into /usr if they're not part of a .deb package.

---

### Post by M1k4 on 2014-04-24
bump
i dont find that mozilla file (except in usr file)

sudo apt-get install flashplugin-installer isn't what i want to install


synaptic isn't what i want to install... except if I need to
I don't know that thing and I dont know if it will be usefull...


@dragon fly
/usr/lib/flashplugin-installer/libflashplayer.so

---

### Post by dragonfly41 on 2014-04-24
Re: manual installation .. this thread ...

[http://forums.adobe.com/thread/1066869](http://forums.adobe.com/thread/1066869)

refers to this YouTube tutorial thread .. which should help you ..

[http://www.youtube.com/watch?v=gerD__lYnqc](http://www.youtube.com/watch?v=gerD__lYnqc)

***However*** since you don't have flash properly installed you will not be able to view YouTube !!

You already have downloaded .tar.gz so you can skip some of the steps.

The target installation directory in this tutorial is /usr/lib/mozilla/plugins

---

### Post by Yellow Pasque on 2014-04-24
> **M1k4 said:**
> i dont find that mozilla file (except in usr file)
It's a hidden file...
```
cd ~/.mozilla
mkdir plugins
cp <plugin.so file you want> plugins/
```

---

### Post by 3rdalbum on 2014-04-24
Everyone: before replying, please note that he wants Flash Plugin Content Debugger, not the ordinary Flash Plugin. He already has that installed.

---

### Post by Yellow Pasque on 2014-04-25
> **3rdalbum said:**
> Everyone: before replying, please note that he wants Flash Plugin Content Debugger, not the ordinary Flash Plugin. He already has that installed.

Indeed. I should have pointed that out since I understood it, but being a lazy typist, I didn't.

Still, the code snippet in my previous comment should do the trick..

---

