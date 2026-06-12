---
title: "Nvidia settings never save..."
date: 2019-07-01
forum: General Help
---

### Post by shadowstorm56 on 2019-07-01
So it's pretty simple, I set all my screen positions and resolutions as well as refresh rates. Apply them and save them to the config file. Next time I restart it reverts back to default, I tried running settings as root, copying the preview to the file directly and enabling the little setting in the bottom configuration to label screens? I think it wass... I forget now. Every time I get the same result, reboot just wipes it all. I had this issue when I used ubuntu like 4 years or more ago and it gets annoying quite fast. SLI not working which leaves my 1 1080 just sitting there idle is annoying enough but having to redo settings each reboot is just.... no good. Some may say why am I not using windows? Basically windows keeps screwing me with weird little issues and since a windows update corrupted my os beyond repair I decided to explore ubuntu which I really like. I hope one day sli actually works for games since right now it just sits at a black screen but that I can deal with. How do I make the settings stick?

---

### Post by CatKiller on 2019-07-02
From ```
man nvidia-settings
```

> 
Loading Settings Automatically

The NVIDIA X driver does not preserve values set with nvidia-settings between runs of the X server (or even between logging in and logging out of X, with xdm(1), gdm, or kdm ). This is intentional, because different users may have different preferences, thus these settings are stored on a per-user basis in a configuration file stored in the user's home directory.

The configuration file is named ~/.nvidia-settings-rc. You can specify a different configuration file name with the --config command line option.

After you have run nvidia-settings once and have generated a configuration file, you can then run: 

 nvidia-settings --load-config-only

at any time in the future to upload these settings to the X server again. For example, you might place the above command in your ~/.xinitrc file so that your settings are applied automatically when you log in to X. 

Your .xinitrc file, which controls what X applications should be started when you log into X (or startx), might look something like this: 

 nvidia-settings --load-config-only & 
 xterm &
 evilwm 

or:

 nvidia-settings --load-config-only &
 gnome-session

If you do not already have an ~/.xinitrc file, then chances are that xinit(1) is using a system-wide xinitrc file. This system wide file is typically here:

 /etc/X11/xinit/xinitrc 

To use it, but also have nvidia-settings upload your settings, you could create an ~/.xinitrc with the contents:

 nvidia-settings --load-config-only &
 . /etc/X11/xinit/xinitrc 

System administrators may choose to place the nvidia-settings load command directly in the system xinitrc script. 

Please see the xinit(1) man page for further details of configuring your ~/.xinitrc file.


---

### Post by shadowstorm56 on 2019-07-02
Well that should solve that pretty quickly.

---

### Post by shadowstorm56 on 2019-07-02
> **CatKiller said:**
> From ```
man nvidia-settings
```

It does not save resolution, frequency or overclocks. Overclocks are probably not supposed to save but the display frequency and resolution would be nice. Everything else seems to save now though.... it stays in mosiac mode, screens are in the right spot, force composition pipeling stays selected so it is an imporovement.

---

### Post by CatKiller on 2019-07-03
> **shadowstorm56 said:**
> It does not save resolution, frequency or overclocks. Overclocks are probably not supposed to save but the display frequency and resolution would be nice. Everything else seems to save now though.... it stays in mosiac mode, screens are in the right spot, force composition pipeling stays selected so it is an imporovement.

The resolution and refresh rate are really handled elsewhere. The Display part of the normal settings should store your preferences if they are different to "the best available, as determined by XRandR and the driver."

While it (deliberately) won't save your overclock settings, you can still set them from the command line, which means you can set them automatically when you've found settings you like. I have scripts called "overclock" and "clock" which will apply or remove my overclock whenever I choose. You could run something like that at startup, too.

Edit: for reference, this is my overclock script.

```
#!/bin/sh

nvidia-settings -a [GPU:0]/GPUMemoryTransferRateOffset[4]=1000
nvidia-settings -a [GPU:0]/GPUGraphicsClockOffset[4]=100
exit 0
```
Pretty simple.

---

