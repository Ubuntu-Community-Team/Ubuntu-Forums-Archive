---
title: "New Ubuntu Software doesn't start in 16.04 anymore"
date: 2016-08-31
forum: General Help
---

### Post by Papiur on 2016-08-31
Hi,

So recently updated Ubuntu from 14.04 to 16.04. Initially new Ubuntu Software was running, but was playing with it a little bit and ended up removing/purging and re-installing it back again few times. Now it's in the state where once I start it process seems to be hanging but no GUI is displayed.

This is how process looks like:
> ps aux | grep software
my_user     30625 32.8  1.6 1395400 132252 ?      Sl   23:17   0:01 /usr/bin/gnome-software --gapplication-service

This is what I'm seeing when I run it from terminal with verbose option:
> (gnome-software:30664): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-backports-multiverse' to com.dell.uefie0f614ed.firmware
(gnome-software:30664): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-backports-multiverse' to com.hughski.ColorHug.firmware
(gnome-software:30664): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-backports-multiverse' to com.hughski.ColorHug2.firmware
(gnome-software:30664): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-backports-multiverse' to com.hughski.ColorHugALS.firmware
(gnome-software:30664): As-DEBUG: run appstream::refine
(gnome-software:30664): As-DEBUG: run GsPlugin::hardcoded-blacklist(gs_plugin_refine)
(gnome-software:30664): As-DEBUG: run hardcoded-blacklist
(gnome-software:30664): As-DEBUG: run GsPlugin::moduleset(gs_plugin_refine)
(gnome-software:30664): As-DEBUG: run moduleset::startup
(gnome-software:30664): As-DEBUG: run GsPlugin::menu-spec-refine(gs_plugin_refine)
(gnome-software:30664): As-DEBUG: run GsPlugin::ubuntu-reviews(gs_plugin_refine)
(gnome-software:30664): As-DEBUG: run GsPlugin::apt(gs_plugin_refine)


---

### Post by Bucky Ball on 2016-10-06
Issues with Ubuntu Software since 16.04 release almost. 

Best and easiest is to just install Synaptic Package Manager and use that. You might prefer it anyway. In a terminal:

```
sudo apt install synaptic
```

That's it. Enjoy. :)

 Have you tried completely purging Ubuntu Software and reinstalling? This won't make any difference to the fact there are some issues with it, but they have to do with not all software showing up. Not sure what you've done with you explorations.

---

### Post by rainwater4 on 2016-10-09
I am having the same issue. ubuntu-software does not show a gui. It is sitting in processes. Running ubuntu-software in terminal produces no output.

---

### Post by Geoffrey_Arndt on 2016-10-10
1.   via the Command Line, install Synaptic (sudo apt-get install synaptic).
2).  Post your software sources list.

---

