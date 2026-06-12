---
title: "Video resolution"
date: 2008-01-26
forum: General Help
---

### Post by Lajoie on 2008-01-26
Ubuntu 7.10 AMD-64
CTL 770 VF Monitor (not in the list)
Dual Boot with Windows XP

I started Ubuntu this morning and the screen resolution had reset itself to 800x600 after months of loyal service. It has done this before, and my solution was to reinstall Ubuntu, which is a pain.

So, I tried to select a different monitor, the 1280x1024 generic. 
My monitor did not sync to that. 

Looked in the forums, and someone tried
*sudo dpkg-reconfigure -phigh xserver-xorg  *
that selects a video card, but it didn't help my monitor problems.

Someone else said to edit the */etc/X11/xorg.conf* file. I did that, setting the horizontal and vertical frequencies to what my monitor can use. That didn't help.

Someone else said to try:
*sudo /etc/init/gdm restart* 
My monitor complained sync out of range.  :(

So, I guess I'm back to reinstalling, which I hate to do. **I'd sure like knowing if there is an easier way to do this than reinstalling every few months**.  When it works, Ubuntu is better than Mandriva or SUSE, imho. But if I can't get X11 working... 

Oh well.

---

### Post by taurus on 2008-01-26
What video card do you have and which driver did you choose when you reconfigure X server with that command?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Lajoie on 2008-01-26
My built in video card says it has "VIA DeltaChrome Graphics", so I picked the VIA option.

---

### Post by Lajoie on 2008-01-26
Wow. Now it won't even let me do a new install. I put in my install CD, select install, and it hangs. :(

---

### Post by BAsecamp.88 on 2008-01-26
This problem has annoyed me on most live cd Ubuntu installs. The screen defaults to 640x480 and you cannot see the buttons to move through the install without at least 1024x768.

Open a terminal and type:

```
sudo gedit /etc/xorg.conf
```

Look for a section called **Section "Screen"**

You will see listings that resemble the following:

```
SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
```

You will need to add the resolutions you want by hand:

```
SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480" "640x400" "800x600" "1024x768"
	EndSubSection
```

Save and either restart or use **CTRL-ALT-F12** to apply the changes.

You should be able to change the resolution from **System > Preferences > Screen Resolution**. I think that Only resolutions your monitor can support will be selectable.

---

### Post by Lajoie on 2008-01-27
Thank you for the help. Sadly, it did not work. 

I guess what I'm hearing is that in dual boot configurations with Microsoft Windows, the screen resolution of Ubuntu 7.10 can change itself to something pitifully bad, and it forgets all other modes except the low resolution mode. 

The things I found in the other posts, to 
sudo dpkg-reconfigure -phigh xserver-xorg 
edit the /etc/X11/xorg.conf file. 
and 
sudo /etc/init/gdm restart
Seems to mess things up so I can't even do a reinstall from the Ubuntu 7.10 disk.

 I'm really bumbed. I'm going to lose a lot of data and now I don't trust Ubuntu; not until I can afford to put it on it's own machine without dual booting Windows, anyway.

---

### Post by Lajoie on 2008-01-27
Oh well.

So, I couldn't get Ubuntu 7.10 to do any kind of repair or even do a new install; it was smart enough to read the hard disk and get the same screwed up configuration that the hard disk was trying to use. 

I thought this thing was a live CD. Why would a Live CD do that? 

Oh well. I've lost my data now by intalling OpenSUSE. 

If it makes you feel any better, Mandrivia can't understand serial ATA drives. 

Let me know if that nasty bug where Ubuntu re-sets it's video resolution. Maybe I'll try Ubuntu again. 

Thanks anyway.

---

