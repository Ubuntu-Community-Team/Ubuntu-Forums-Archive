---
title: "Settings GUI Crashes"
date: 2016-08-22
forum: General Help
---

### Post by zuto2 on 2016-08-22
Hello,

My settings GUI Crashes. As you can see in the gif.

[B]Edit:
[/B]I ran gnome control center in the terminal and I got these errors when clicking sound. That is one of the options that crashes.
```
[COLOR=#111111][FONT=Consolas]gnome-control-center[/FONT][/COLOR]
``````

datetime
deja-dup
online-accounts
universal-access
wacom
keyboard
sound-nua


(GnomeCC:10275): sound-cc-panel-WARNING **: active_input_update - couldn't find a stream from the supposed active input


(GnomeCC:10275): sound-cc-panel-WARNING **: active_output_update - couldn't find a stream from the supposed active output


(GnomeCC:10275): GLib-GIO-ERROR **: Settings schema 'org.gnome.DejaDup' is not installed



```

[IMG]https://media.giphy.com/media/l0HluwjtZrggYawr6/giphy.gif[/IMG]


I tried old kernels, so the new kernel did not do this.

I recently restored a back up, but this has never happened to me before when restoring a back up. 

It was working last month.

Everything else is working fine. None of the settings are broken. I just can not access the settings GUI in any of my desktop environments. Cinnamon. Unity, Gnome, Elementary, etc.

I recently installed a new kernel from the update manager. Well...I will just add images of recently updated things. Mono is not the cause. At least I do not think Mono complete kills the settings. I installed Mono complete on July 23rd.

[IMG]https://s14.postimg.io/iy08lsu29/Selection_001.png[/IMG]

[IMG]https://s14.postimg.io/l3ujgaxip/Selection_002.png[/IMG]

---

### Post by zuto2 on 2016-08-22
The solution for others. I fixed.
```
sudo apt-get install deja-dup
```

---

