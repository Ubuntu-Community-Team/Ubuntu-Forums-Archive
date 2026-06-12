---
title: "1680x1050 monitor setting"
date: 2008-02-05
forum: General Help
---

### Post by tc101 on 2008-02-05
I just got a new Dell 1680x1050 monitor.  I went to system/preferences/screen resolution and there is no 1680x1050 setting there.  It is currently set to 1280x1024 which was for my old CRT monitor.  This works OK but I would like to get the 1680x1050 setting.  How do I do that?

---

### Post by Fraktyl on 2008-02-05
Go to System->Administration->Screens and Graphics.

Change the Model to the monitor you have, you can also set the resolutions.  Save, log out of X, log back in.

---

### Post by tc101 on 2008-02-05
The monitor is a Dell E228WFP.  
I went to System->Administration->Screens and Graphics and set it to that monitor.
I hit the test button and it came back and said "configuration test failed" "please verify the selected devices and configuration".  

Also, under the list of resolutions it has 1600x1200 but not 1680x1050.

---

### Post by Fraktyl on 2008-02-05
You can try the plug and play setting under the Generic vendor.

Or use the Dell monitor you have, you may have to check the Widescreen box under the list.  Then set your resolution.

---

### Post by der_joachim on 2008-02-05
Open up a terminal and use the following command:
```

sudo dpkg-reconfigure xserver-xorg

```
Just answer the questions and you should be set.
[edit] Do not forget to make a backup of your /etc/X11/xorg.conf .

---

### Post by tc101 on 2008-02-05
> You can try the plug and play setting under the Generic vendor.

Or use the Dell monitor you have, you may have to check the Widescreen box under the list. Then set your resolution.

I tried those things.  None of them worked.

> Open up a terminal and use the following command:
Code:

sudo dpkg-reconfigure xserver-xorg

Just answer the questions and you should be set.
[edit] Do not forget to make a backup of your /etc/X11/xorg.conf .

I know how open the terminal and enter commands but I am not an experienced linux terminal user.  I am just a guy who uses the ubuntu GUI because it is better than windows and normally I do everything from the GUI desktop.  Is there much chance I will mess up something by doing what you recommend and then not be able to use the computer at all?

---

### Post by tc101 on 2008-02-05
Since I did that plug and play thing and turned off the monitor and turned it back on it is now much worse.  I can just barely see to type this.  I would like to get it back to the quality it was before, which was some custom setting, set up buy ubuntu when I first set it up, but I don't know how.

---

### Post by tighem on 2008-02-05
If you have an nvidia card run "nvidia-settings" and you can make changes there. Nvidia-settings works much better than the default display app.

---

### Post by tc101 on 2008-02-05
I do have a nvidia card.  How do I run nvidia settings?

---

### Post by tc101 on 2008-02-05
One more thing before I sign off:

I  know  I messed up something when I did the plug and play option.  I
reconnected my old monitor, a CTX model VL700.  I went to
system/admin/screens and graphics and selected it.  It will not let me
select the old 1280x1024 settings.  They are no longer in the drop down
box.  When I hit the test button the screen comes up bright gray, then
returns with the message "Configuration test failed, please verify the
selected devices and configuration".

---

### Post by der_joachim on 2008-02-06
> **tc101 said:**
> 
I know how open the terminal and enter commands but I am not an experienced linux terminal user.  I am just a guy who uses the ubuntu GUI because it is better than windows and normally I do everything from the GUI desktop.  Is there much chance I will mess up something by doing what you recommend and then not be able to use the computer at all?

That's why I recommended making a backup of your xorg.conf . If you somehow mess up, you can easily revert to your old settings by restoring your backup. Safe and simple. :)

Making a backup from your X configuration file is quite easy. Open up a terminal (or work from the command line) and issue the following commands:
```

cd /etclX11
sudo cp xorg.conf xorg.conf.bak

```

To restore your older version, just copy your backup file over your current xorg.conf. To get more familiar with terminal commands, I recommend reading the manual pagees for the command in question. The command *man cp* gives you the manual page for the cp command. Konqueror, a file manager for KDE has a built-in manual page viewer. I do not know whether Nautilus has one as well.

The dpkg-reconfigure program is safe enough. If X does not like your settings, it simply won't start. You won't fry your monitor or anything. If by some misconfiguration X won't start, just rerun the command I mentioned in my earlier posting from the command line. It'll work.

An earlier poster recommended using nvidia-settings.In KDE, nvidia-settings is in my menu under "System". Since I am not familiar with recent versions of Gnome, I cannot tell you whether Gnome has a shortcut as well, but I assume there is. Of course, the Nvidia manager can be called from a console as well.

---

