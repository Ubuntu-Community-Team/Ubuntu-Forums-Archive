---
title: "some assorted xubuntu/xfce problems."
date: 2007-04-18
forum: General Help
---

### Post by mojoman on 2007-04-18
I've  just installed 64-bit Xubuntu Feisty and got some assorted issues that I could use some help with. Here it goes.

1) For some reason the fonts in the application menu have become quite small and I swear on a stack of bibles that I didn't do a thing! In the windows the fonts are fine, it's just in the menu and in thunderbird (just in the folders and headers text though, the messages themselves look fine). This happened after I restarted the computer and it looked good initially. I want these fonts bigger, and as far as I've understood this is not set under Window Manager Settings. Any ideas on how to change this?

2) I'm trying to add the xfce4-places-plugin for the xfce panel (with a tarball from xfce.org as it isn't in  the repositories). However, when I run the script I get the message that I need to install a version of gtk+-2.0, version 2.6.0 or later. I can't find this package in the repositories or anywhere else, or indeed, anything resembling it. A repository search on gtk+ gives a an output the size of a phonebook, and even piping it through grep doesn't give me any good candidates. Any ideas on what this package might be? I really want a menu with shortcuts to the different folders in a mounted HD, that's one Gnome-feature I really like and this plug-in supposedly does just that.

3) I got almost all the applications I need (I used xubuntu dapper on my laptop before I switched it to Debian Etch with Fluxbox so I'm fairly familiar with applications that don't depend on Gnome or KDE) but I do miss some. A good, gui fm-radio is one thing I lack, and a substitute for Soundconverter is another.

4) When the system boots there is a really good looking Xubuntu logo, complete with the xfce mouse and a progress bar (in dark shades of blue on black background). It's really beautiful and I was thinking about using  in a wallpaper but cannot for the life of me locate it on the computer. Does anyone know where it is?

Any and all help with this - or for that matter, other useful tips for xfce - is very much appreciated.

Best regards
/mojoman

---

### Post by mojoman on 2007-04-18
Ok, I've managed to find the answer to question number 1. In the home folder there is a file called "./config/xfce4/Xft.xrdb". I simple added the following line to that file:

```
Xft.dpi: 96
```

Saved the file, logged out of xfce without saving the current settings, restarted x, logged in and beheld fonts in the menu that were just the right size.

As far as the other questions are concerned ... well ... bump. 

Best regards
/mojoman

---

### Post by trincamckee on 2007-05-16
2) the package you need is **libgtk2.0-dev**.

I tried to install that plugin too, i have all dependencies but when i try to make gives me some error, maybe you can help me...

good luck :)

---

### Post by trincamckee on 2007-05-16
Ok, i did install places plugin after all.

I created a quick deb file, if you want...
[http://rapidshare.com/files/31611964/xfce4-places-plugin_0.2.0-1_i386.deb.html](http://rapidshare.com/files/31611964/xfce4-places-plugin_0.2.0-1_i386.deb.html)
Done with a pentium4.

Take care

---

### Post by mojoman on 2007-05-16
> **trincamckee said:**
> Ok, i did install places plugin after all.

I created a quick deb file, if you want...
[http://rapidshare.com/files/31611964/xfce4-places-plugin_0.2.0-1_i386.deb.html](http://rapidshare.com/files/31611964/xfce4-places-plugin_0.2.0-1_i386.deb.html)
Done with a pentium4.

Take care

Thanks but I use 64-bit so I',m not sure I can use it. Anyway, I had a look at the package libgtk2.0-dev and it want to install a ton of dependencies with it. 

```

The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev
  libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
```

I might give it a go anyway.

Cheers
/mojoman

---

### Post by mojoman on 2007-05-17
Ok, I gave it a go despite it pulling down a ton of dependencies (some 65 MB after unpacking of mostly-dev-packages) and tried once more. It got a bit longer on the ./configure part before once more complaining on missing packages. I installed those (more -dev-packages that I really don't know why I would need), tried again and got just a little bit longer before the same thing happened once. This procedure repeated itself a couple of times before ./configure spitted out:

```
checking for libxfce4panel-1.0 >= 4.3.99.1... not found
*** The required package libxfce4panel-1.0 was not found on your system.
*** Please install libxfce4panel-1.0 (atleast version 4.3.99.1) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
```
and this package is, as far as I can see, not in the repositories.

Now, I have a fairly standard 64-bit feisty xubuntu so it's not that I have the slimmest system in the universe. I must say I really don't see why one would make what would arguably be a fairly standard plugin dependent on packages that are far from standard? Would the normal user want to download and install some 100 MB of dev-packages just to get this plugin?

---

### Post by trincamckee on 2007-05-17
That package is **xfce4-panel-dev**.
Well i dont know why this plugin is not on repositories, is far more imporant  that other plugins and was done before feisty release.

A part of those gtk dependencies i see why we need this "xfce-dev" packages, anyway you are almost done, i think that is the last dependency.

---

### Post by mojoman on 2007-05-17
Ok, got it working know. Apart from the ordinary run-of-the-mill xubuntu installation, *at least* another 64 MB of dependencies was needed to install this plugin :shock: It might actually have been a bit more as I had already installed some more (though I tend to keep my system fairly slim). Still, it's a very handy plugin to have. Thanks for the help guys. 

On a side note, any tips for a good gui FM radio or sound converter (complete with tags) that doesn't install a zillion MB of Gnome or KDE libraries?

/mojoman

---

### Post by trincamckee on 2007-05-17
After you install the plugin you can safely remove all *-dev packages you installed, those package only served to compile.

Cheers

---

### Post by mojoman on 2007-05-17
Oh, didn't know that. Thanks for the tip. A quick question, if I may. If I would have had the plugin as a .deb-file, could that have been installed without the -dev-packages?

---

### Post by trincamckee on 2007-05-17
The awser is yes. dev(stands for development) package are only needed to compile. :)

---

### Post by mojoman on 2007-05-17
> **trincamckee said:**
> The awser is yes. dev(stands for development) package are only needed to compile. :)

Ok, then it makes a little more sense and I've learned something as well. :)  I should probably compile a .deb so I have a 64-bit. Thanks!

EDIT: I've compiled a 64-bit ubuntu .deb-package for this plugin. If anyone wants it, just pm me and I'll transfer it.

---

### Post by kerry_s on 2007-05-17
#3. Have you tried vlc?
#4. on mine backgrounds are in /usr/share/images/desktop-base, you can use locate to find the image you want. In the terminal run> sudo updatedb <then> locate "image-name.jpg" and it will tell you the pathe to the file.

---

### Post by mojoman on 2007-05-17
> **kerry_s said:**
> #3. Have you tried vlc?
#4. on mine backgrounds are in /usr/share/images/desktop-base, you can use locate to find the image you want. In the terminal run> sudo updatedb <then> locate "image-name.jpg" and it will tell you the pathe to the file.

I know I can stream music with vlc but can I really use it as as FM-radio reciever (utilizing my tv/radio-card)? If so, that would be an option, it's one of the more versatile players around. 

As for using locate, the problem is that I don't know the name of the file. Just doing a wildcard search for the suspected formats (.jpg, .png) gives the outprint of a phonebook and even combining it with grep xfce or xubuntu to narrow down the search isn't doing me any good. 

cheers
/mojoman

---

### Post by kefir on 2007-05-17
[http://packages.ubuntulinux.org/edgy/sound/xmms-fmradio](http://packages.ubuntulinux.org/edgy/sound/xmms-fmradio)

Perhaps that's an alternative to question nr.3. Haven't tried it though but sounds like what you want.

apt-cache search fm radio - gave quite a few useful options

---

### Post by mojoman on 2007-05-17
> **kefir said:**
> [http://packages.ubuntulinux.org/edgy/sound/xmms-fmradio](http://packages.ubuntulinux.org/edgy/sound/xmms-fmradio)

Perhaps that's an alternative to question nr.3. Haven't tried it though but sounds like what you want.

apt-cache search fm radio - gave quite a few useful options

Kefir,

Actually, I already installed it but I can't for the life of me start it. When I start xmms there is no option to play FM and I can't start it from CLI using 'xmms-fmradio' either (command unknown and 'whereis' just gives 'xmms-fmradio:' as output but that was a longshot anyway, it is, after all, a plugin for xmms and shouldn't be started separete). The plugin is enabled and under configuration it has even located the correct device (/dev/radio0).

The card is working as radio (the CLI application) works though this application uses the wrong device (/dev/radio, mine is /dev/radio0) and I haven't been able to change it (meaning I have to state what device I want to use everytime I start it). If I could change this configuration, I might just be able to use the xfce-panel plugin alternative (not sure which backend the xfce-panel plugin uses) but if I try that as things are now I get an error stating that no device is configured (so my guess is that the xfce-panel plugin goes for /dev/radio instead of /dev/radio0)

Anyway, thanks for the tip. Any further thoughts on this is much appreciated.
/mojoman

---

### Post by kerry_s on 2007-05-17
under desktop preference, where you select the background image should have the name of the background.

---

### Post by mojoman on 2007-05-18
> **kerry_s said:**
> under desktop preference, where you select the background image should have the name of the background.

I'm sorry if I was a bit muddled but I meant the dark blue xubuntu splash screen that is visible during boot together with a progress bar och a black background.

---

### Post by kerry_s on 2007-05-19
my bag, go to the settings manager it should be set to that splash,click on configure and it should so the path to the image.

---

### Post by trincamckee on 2007-05-19
A new version(0.3) of xfce place plugin as been released with some new features. :)

[http://goodies.xfce.org/projects/panel-plugins/xfce4-places-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-places-plugin)

---

### Post by mojoman on 2007-05-20
> **kerry_s said:**
> my bag, go to the settings manager it should be set to that splash,click on configure and it should so the path to the image.

But that's for the Xfce splash screen, isn't it? I'm talking about the Xubuntu splash screen that is visible during boot. Because I don't have a Xfce splash screen, which is consistent with those settings. Or am I mistaken here?

---

### Post by kerry_s on 2007-05-20
So your talking about the boot splash. Sorry can't help with that 1, i don't use a boot splash i like to see the loading messages so i uninstall that. Just use synaptic, do a search for " boot splash " there are several, i don't remember what xubuntu uses and check where the files are installed.

---

