---
title: "Display problem in breezy"
date: 2005-10-20
forum: General Help
---

### Post by tspec on 2005-10-20
I've just updated Ubuntu to 5.10 and seem to have lost the ability to load gnome. I was running warty and tried to upgrade it to breezy by typing the command apt-get dist-upgrade (after updating my sources file). Thats all fine, it spent a while downloading and installing all sorts of packages. After it had finished doing all this I decided to reboot but I can't actually get back into gnome because as soon as it's about to load the gui my monitor display shuts off and shows one of the default monitor messages: "Attention - 112k / 74Hz Frequency Is Out Of Range" (I get this on 2 different monitors).

I'm not sure what changed in the way of display settings during the upgrade to Breezy, previously I was running 1600x1200 on a 19" Phillips CRT with a Geforce3 Ultra card. One thing thats probably worth mentioning though is when the upgrade to Breezy finished I did get a message right at the end of it all that said:

"find: warning: you have specified the -maxdepth option after a non-option argument -name, but are not positional (-maxdepth affects tests specified before it as well as those specified after it). Please specify options before other arguments."

Does this mean anything in terms of the problem I described above?

Any help would be greatly appreciated.

---

### Post by xristos on 2005-10-20
Boot with the recovery mode and check your /etc/X11/xorg.conf file .
Especially the Section "Monitor" and put the correct HorizSync and  VertRefresh values .

Hope it helps

---

### Post by mykey on 2005-10-20
sounds like an xserver issue again - try **sudo dpkg-reconfigure xserver-xorg**

---

### Post by pinkfloyd65 on 2005-10-20
I also just updated to 5.10 breezy and now when Ubuntu starts, I only get a command line prompt. How do I get into Gnome?

When I run sudo dpkg-reconfigure xserver-xorg I get the message "xserver-xorg is not installed".

I am a very green newbie in Linux, trying to "emigrate" gradually from the Windows world, so any advice is appreciated.

Thnx

---

### Post by tspec on 2005-10-20
[QUOTE=xristos]Boot with the recovery mode and check your /etc/X11/xorg.conf file .
Especially the Section "Monitor" and put the correct HorizSync and  VertRefresh values .

Hope it helps[/QUOTE]

Fantastic, that fixed it... I don't know why it didn't click but i actually encountered a similar problem a long time ago in an earlier version of ubuntu using different hardware at the time. A guy at my work that helped fix that one who actually knows some of guys that work on Ubuntu and he claimed they had this problem fixed in breezy, it's better than it was the last time i encountered the problem though, last time the HorizSync and  VertRefresh lines were completely missing from the xserver file, this time the values were just simply wrong... ahh well, hopefully it'll be an easy one for them to fix up for future releases of Ubuntu when they get a chance.

[QUOTE=mykey]sounds like an xserver issue again - try **sudo dpkg-reconfigure xserver-xorg**[/QUOTE]

thanks, i did try that but got an error saying xserver-xorg wasn't installed but the manually editing the xserver.xorg file did the trick, thanks for you help though.

---

### Post by tspec on 2005-10-20
[QUOTE=pinkfloyd65]I also just updated to 5.10 breezy and now when Ubuntu starts, I only get a command line prompt. How do I get into Gnome?

When I run sudo dpkg-reconfigure xserver-xorg I get the message "xserver-xorg is not installed".

I am a very green newbie in Linux, trying to "emigrate" gradually from the Windows world, so any advice is appreciated.

Thnx[/QUOTE]

what happens when you type in [COLOR="Red"]startx[/COLOR] ?

---

### Post by pinkfloyd65 on 2005-10-20
command not found

---

### Post by Avicus on 2005-10-20
Did you do a 'server' install? Try this at the prompt:

   sudo apt-get install x-window-system-core

Then try:

   startx

If that works, you might want to reinstall and do a normal install this time (Hit enter at the parameters prompt on first boot from disc). Or you can attempt install of a window manager/desktop environment like Gnome, KDE, or XFCE4....

---

### Post by pinkfloyd65 on 2005-10-20
I installed the x-window-system-core. Installation went OK. But at startx, the screen goes blank for a second and then comes back with message:

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"

Then I run sudo dpkg-reconfigure xserver-xorg-dbg, go through all the settings, but to no avail.

I will try to reinstall Ubuntu and see what happens then.

How do I a windows environment, preferably Gnome?

Thanks

---

### Post by Avicus on 2005-10-20
If you do a default install, Gnome and all the supporting software needed are installed automatically. Do the reinstall and I think you should be happy.

---

### Post by pinkfloyd65 on 2005-10-20
You were right! I reinstalled and now I have Gnome...Thanks!

One last question:

Is there a reason why I cannot log in as root at the initial logon screen? It says the system administrator cannot log in from there. I know I activated root on the system (sudo passwd root)...

---

### Post by Ali_Baba on 2005-10-20
In System-Administration-Login Screen Setup you have to enable,allow root to login with GDM option.Then you can login as root user.It's a security issue.

---

### Post by Avicus on 2005-10-20
BTW, you don't need root user to be activated.... that is what the sudo command is for on your main account.

---

### Post by Incendium on 2005-10-22
[QUOTE=xristos]Boot with the recovery mode and check your /etc/X11/xorg.conf file .
Especially the Section "Monitor" and put the correct HorizSync and  VertRefresh values .

Hope it helps[/QUOTE]

How would I know what the correct values are?

---

### Post by claymore on 2005-10-22
[QUOTE=Incendium]How would I know what the correct values are?[/QUOTE]

The best way is to grab the values from your monitor manual or stats on the webpage.  That way, Ubuntu will only let you choose values your monitor can display.

---

### Post by gadge47 on 2005-10-24
I think I'm in the same boat as the rest of the folks in this thread but the normal solutions aren't working. In fact, things aren't behaving as I'd expect.

I installed Hoary Hedgehog on this Dell that I have and it took me a while (and a post on the forums) to get X configured properly so that it would display on the crappy chipset and picky Dell LCD. Not too long ago I switched monitors to a Sony (SDM-S204) and everything continued to work. Right when Breezy Badger came out I upgraded by changing the sources in Synaptic and everything seemed to go okay except that when I rebooted, X wouldn't display. I think, it's still running because I hear the normal Ubuntu/Gnome noise that it makes when it asks you to log in. However, the monitor itself displays a message in one of its little on-screen menus that says:

Out of Range
93.5kHz/ 87Hz

And according to specs I found [online]("http://www.dealtime.com/xPF-SDM_S204E_B_20IN_LCD_1600X1200_BLK_SDM_S204E_B_20IN_LCD_1600X1200_BLK") those rates are indeed outside what the monitor will accept. However, the strange part (to me at least) is that those are also outside the rates that I specify in /etc/X11/xorg.conf.

In my monitor section I have these lines...

HorizSync 28-92
VertRefresh 48-85

I also tried nuking this file and using the one generated by running sudo dpkg-reconfigure xserver-xorg but that didn't help. Not did modifying the resulting xorg.conf file to contain the refresh options from above.

Any suggestions?

---

### Post by Incendium on 2005-10-24
My problem was that ubuntu was trying to display resolutions my monitor couldn't handle, so I had to edit the conf file and remove all of the instances where the incompatible resolutions appeared. Make sure you aren't trying to use resolutions your monitor can't handle.

---

### Post by gadge47 on 2005-10-24
I tried changing the mode lines and removed all resolutions other than 1600x1200 on the default line and it changed the message displayed by my monitor to a different range
87.8kHz/ 70Hz
Which is odd because those numbers are /within/ the limits that I found online (vert refresh 48-85Hz; horiz refresh 28-92kHz) but still, nothing displays.

---

