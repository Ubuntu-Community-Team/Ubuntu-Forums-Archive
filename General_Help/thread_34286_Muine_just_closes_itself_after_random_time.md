---
title: "Muine just closes itself after random time"
date: 2005-05-14
forum: General Help
---

### Post by dilerra on 2005-05-14
Hi,

I have a problem with Muine. If I leave my computer for a while playing music, Muine closes itself after a while. That is, the application "dies". I don't know if it properly shuts itself down, or if there is some other fault.

Someone else who has experienced similar things? Muine can also "die" when I'm working with other apps...

/ Mattias

---

### Post by ssam on 2005-05-14
can you run muine from a terminal

(open Terminal from Applications -> System Tools. then type "muine" (without quotes) and press return)

you can minimise the terminal, but dont close it.

when muine dies, then look in the terminal, and see if it left a message.

sam

---

### Post by dilerra on 2005-05-14
Hi again,

Started Muine from a shell, and after a while it crashed leaving a message "Segmentation fault". Do you know how to track this down further? Still doesn't help me just knowing that a segmentation fault occured =/

Thanks / Mattias

---

### Post by ow50 on 2005-05-14
Are you using the Hoary versions (ones from official Hoary repositories) of Muine and Mono?

---

### Post by dilerra on 2005-05-14
Hm,

How can I tell what versions I use? I have added additional repositories (hoary backports and marillat).

[INDENT]deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted[/INDENT]

Can I use Synaptic in my search for a solution? It should be able to tell me which versions I got...

Thanks again / M

---

### Post by ow50 on 2005-05-14
For me Muine segfaulted on song change with the Mono from backports. With the Hoary Mono that doesn't happen. This could be the case for you as well.

In Synaptic find the package "mono" and check the version number. If it's from backports, the version number will contain ~5.04ubp. If it's from Hoary, the version tab in the properties will state "1.0.5-1 (hoary)".

---

### Post by dilerra on 2005-05-14
Hm...

Is there any easy way to "downgrade" so that I can get the official Hoary packages again?

/ M

---

### Post by ow50 on 2005-05-14
[QUOTE=dilerra]Is there any easy way to "downgrade" so that I can get the official Hoary packages again?[/QUOTE]
In synaptic search for "mono". List all the installed mono packages (mono*, libmono*) that are from backports. Then at command line (after closing synaptic) include all the packages in one command with "/hoary" after each package name:
```
sudo apt-get install mono/hoary mono-common/hoary ...
```
After downgrading either remove backports from your sources.list or lock the mono packages' versions in synaptic to avoid unwanted updating.

---

### Post by Rnd227 on 2005-05-26
[QUOTE=ow50]Are you using the Hoary versions (ones from official Hoary repositories) of Muine and Mono?[/QUOTE]

I'm using hoary versions of both mono and Muine. Muine seg-faulted during the song imports (after 5 minutes, I have a lot of songs), and since segfaults after just a couple of seconds.

I have removed and reinstalled to no avail. I'm running latest hoary kernel update for K7. 

On the other hand I have installed f-spot and that one doesn't seg-fault, so maybe Mono is not involved ?

---

### Post by ntd on 2005-05-26
[QUOTE=Rnd227]I'm using hoary versions of both mono and Muine. Muine seg-faulted during the song imports (after 5 minutes, I have a lot of songs), and since segfaults after just a couple of seconds.
[/QUOTE]

This happens when it encounters a file that it can't handle (either one that is corrupt or a file format you haven't installed a gstreamer plugin for)...try to do the import section by section (select like 20 at a time or something) and see which section it segfaults on...once you track down which files muine is having issues with install a gstreamer plugin for that type or make sure that the files don't have any weird characters in their filenames if you have the right plugin.

To install plugins, make sure you have the marillat repository, go into synaptic, search for gstreamer, and select the gstreamer-plugin-xxx package for that type

---

### Post by ow50 on 2005-05-26
[QUOTE=ntd]This happens when it encounters a file that it can't handle (either one that is corrupt or a file format you haven't installed a gstreamer plugin for)...try to do the import section by section (select like 20 at a time or something) and see which section it segfaults on...once you track down which files muine is having issues with install a gstreamer plugin for that type or make sure that the files don't have any weird characters in their filenames if you have the right plugin.

To install plugins, make sure you have the marillat repository, go into synaptic, search for gstreamer, and select the gstreamer-plugin-xxx package for that type[/QUOTE]

Or just install all gstreamer plugins with the package gstreamer0.8-plugins. As for the repositories, most of the plugins should be in hoary repositories. If you must check elsewhere, see [this thread](http://www.ubuntuforums.org/showthread.php?t=35480). Those are Ubuntu specific packages instead of the debian specific Marillat packages

---

### Post by Rnd227 on 2005-05-27
[QUOTE=ntd]This happens when it encounters a file that it can't handle (either one that is corrupt or a file format you haven't installed a gstreamer plugin for)...try to do the import section by section (select like 20 at a time or something) and see which section it segfaults on...once you track down which files muine is having issues with install a gstreamer plugin for that type or make sure that the files don't have any weird characters in their filenames if you have the right plugin.

To install plugins, make sure you have the marillat repository, go into synaptic, search for gstreamer, and select the gstreamer-plugin-xxx package for that type[/QUOTE]

Gee. I was afraid someone would say a thing like that. I have like 12 000 files, a lot of them with accentuated characters.

---

