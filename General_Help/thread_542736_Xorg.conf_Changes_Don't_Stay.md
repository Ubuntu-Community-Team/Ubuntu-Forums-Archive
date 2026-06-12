---
title: "Xorg.conf Changes Don't Stay"
date: 2007-09-04
forum: General Help
---

### Post by ryankask on 2007-09-04
Hi. I have finally found the right xorg.conf settings for my Dell flatpanel. I tested them out right after saving and it looked great. I then restarted my computer and the splash screen had the correct xorg.conf settings (or so it seemed). Once I logged in, everything turned very blurry and the horizontal display was messed up. I had to click 800 or so pixels to the left of where the box actually displayed on screen to open windows. I finally managed to use the Ubuntu tools to change my resolution to something else and it temporarily fixes the issues. Why does my xorg.conf change when the the computer is restarted? Or, why does everything display correctly but then when I restart it goes back to the messed up screen. Sorry if this seems very vague. I will post my xorg.conf when I am done reinstalling Kubuntu.

---

### Post by ticopelp on 2007-09-04
Are you using

```
gksudo gedit /etc/X11/xorg.conf
```

to make the edits?

I say this only because when I was trying to set up my own monitor, I was using the NVidia configuration tool to edit xorg.conf, and my changes wouldn't stick either -- not until I went into the file with gedit and changed it that way.

Just make sure to always create a backup ;)

Hope that helps.

---

### Post by ryankask on 2007-09-04
Yes I am editing the file directly (though using kdesu kate). Thank you though! Any more help would be greatly appreciated.

---

### Post by ryankask on 2007-09-04
I've attached a photo of what my screen looks like once I login. Even if I manage to change my settings after logging in, once a restart, it always reverts to that...any ideas?

---

### Post by ryankask on 2007-09-05
Anyone?

---

### Post by gtdaqua on 2007-09-05
what is the video driver you are using? 

can u pls post the last 25 lines of this file?

/var/log/Xorg.0.log

---

### Post by raincity on 2007-09-10
I'm a newbie to Linux but have spent quite a bit of time trying different distributions.  I've settled on ubuntu but am also having a problem with changes to xorg.conf after a reboot.

When I restart it loses all of my graphics settings - going back to the default configuration I had when I first loaded ubuntu.  If I restore xorg.conf from a backup and restart the X server my monitor configuration works fine.  

The next time I boot, my video settings are lost and I again have to restore the xorg.conf file.

Does anyone have any idea what might be causing this?

Thanks in advance

---

### Post by fragos on 2007-09-10
I had something that looked like that happen when experimenting with Gutsy.  I'm inclined to think the problem isn't that xorg.conf reverts.  There are programs that register changes to xorg.conf but you have to initiate those programs.

---

