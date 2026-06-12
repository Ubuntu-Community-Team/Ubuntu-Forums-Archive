---
title: "Issue with 8.10 and Compiz"
date: 2008-06-22
forum: General Help
---

### Post by msimpson3 on 2008-06-22
Hi, i think this is my first thread on this forum, but I've been using ubuntu since last october and loving it.

I'm having an issue.  I've had to uninstall and reinstall 3 times now and problem occurs every time.

I'm running ubuntu 8.10 using gnome with 2.0 dual core with ATI Radeon x900 video card.

Here's my issue:

I install ubuntu - boots fine, then install the restricted drivers for my card, reboot and it works find, display is great.

I then install compiz, using this tutorial:
[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200)

and it works absolutely fantastic, I'm able to enable as many effects as i want and am blown away by the capabilities of this os, but once i restart it prompts me that i am running in low graphics mode, then I select continue.  I log in, and it starts to load, plays the login sound, then flashes white and black and I'm back at the login page.

I have no idea how to fix it and appreciate any help you can offer.

Let me know what other info you need and I will be pleased to supply.

Thanks,
Matt

---

### Post by pietjanjaap on 2008-06-22
2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by Forlong on 2008-06-22
Are you able to boot into the GNOME failsafe session?

---

### Post by msimpson3 on 2008-06-22
> **Forlong said:**
> Are you able to boot into the GNOME failsafe session?

No, when i try the failsafe session it does the exact same thing described

---

### Post by Forlong on 2008-06-22
Boot into the recovery mode and run
```
dpkg-reconfigure -phigh xserver-xorg
```
Then reboot (using the 'reboot' command) and boot into your regular Ubuntu install.

When you are then able to log into GNOME, post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by msimpson3 on 2008-06-22
I did the dpkg command and was able to boot successfully into gnome, I then ran the compiz-check and got this output:

```
msimpson@r2d2:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

I will now run the envy program (last 2 times i ran this it rebooted in lowgraphics mode) and report the result.

Thanks for the help

---

### Post by msimpson3 on 2008-06-22
I rebooted after running the envy app and the same thing happened as described in my first post.  It booted in low graphics mode, and when I logged in it played the login sound then flashed black and white then i was back at the login screen.

does it have anything to do with me adding the compiz app in my session startup programs list?

---

### Post by Forlong on 2008-06-23
Why did you use Envy?
Did you try with the radeon driver first? After all, it said everything should be up and running.

---

### Post by msimpson3 on 2008-06-23
I will go through the process again and use the radeon install rather than envy this time.  will let you know.

---

### Post by msimpson3 on 2008-06-23
Okay, so I figured out a pretty vital detail - i'm lead to believe it is atleast:

I reinstalled using the radeon drivers and ran 

```
aticonfig --initial -f
```

then rebooted, and drivers were installed, display was beautiful and compiz worked it's magic amazingly :)

But, once i rebooted it went right back into low graphics mode so i changed the session to failsafe terminal and submitted 

```
sudo aticonfig --initial -f
```

Again then reboot and it rebooted logged in beatifully and compiz worked it's magic.

So what is happening between the gnome session and me rebooting that is making it not reboot properly?

the good news is that I have a work around whenever i need to reboot my computer so there's some faith in that.

any guidance?

Thanks,
Matt

---

