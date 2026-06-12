---
title: "ati video card driver problems"
date: 2008-03-24
forum: General Help
---

### Post by americano70e10 on 2008-03-24
Help me please!!! I got a little too ambicious last weekend and I tried to install (update) my ati video card driver following the instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (the manual way), but now when I try to login to ubuntu, the GDM login screen shows up, but after I type in my name and password and press enter, it goes into that light brown screen (the one that appear before the wallpaper) as if it was starting to load nautilus and that stuff, but it just stays in that screen and a short while later it sends me back to the GDM login screen, this happens when i try to login as root also...
anyone got any ideas?
I'm running ubuntu gutsy on a toshiba a215 series with amd turion x2 1.8ghz, 2gb ram, ati x1200 graphics
Thanks in advance...

---

### Post by s3a on 2008-03-24
Not that this is exactly what you want but if I were you, I'd boot into live cd back my data up to an external drive then wipe the hd clean and re-install Ubuntu.

---

### Post by americano70e10 on 2008-03-24
I have that in cosideration, but for educational purposes (I'd like to learn more of ubuntu) I want to try to fix this... Thanks anyway for your opinion...:)

---

### Post by pbpersson on 2008-03-24
I do not have the exact commands here - but when you boot into the hard drive there is a way to get into recovery mode - it is a text-only console.  From there you can enter a command to re-configure your XServer.  You will have to search for  it in other ATI posts.

I know all this because I went through this whole nightmare myself.

The XServer re-configure is all done through text-only screens that ask you what the settings should be.

If you have a mouse with a scroll wheel, answer NO to  the "emulate three button mouse" question

I have an ATI Radeon 9550 and the only way I could get it working is with Mint using Envy and it still is not quite right

Edit to add:  the command you need is **dpkg-reconfigure xserver-xorg**

---

### Post by americano70e10 on 2008-03-24
> **pbpersson said:**
> I do not have the exact commands here - but when you boot into the hard drive there is a way to get into recovery mode - it is a text-only console.  From there you can enter a command to re-configure your XServer.  You will have to search for  it in other ATI posts.

I know all this because I went through this whole nightmare myself.

The XServer re-configure is all done through text-only screens that ask you what the settings should be.

If you have a mouse with a scroll wheel, answer NO to  the "emulate three button mouse" question

I have an ATI Radeon 9550 and the only way I could get it working is with Mint using Envy and it still is not quite right

Edit to add:  the command you need is **dpkg-reconfigure xserver-xorg**

I already did that with no success, but I have an update (that I overlooked), I am able get into GNOME through the Safe Mode, but still got the same problem when I try to log in the normal way...
Maybe something wrong with my start-up scripts, anyone have any idea which and how I can alter them???

---

### Post by americano70e10 on 2008-03-24
So far this is what I got... at the GDM screen, there are 5 tipes of sessions to choose?
1. Last session (takes me back to the GDM screen)
2. Script Xclient (also takes me back to the GDM screen)
3. GNOME (also takes me back to the GDM screen)
4. GNOME Safe Mode (loads normaly but with out the startup scripts)
5. Safe Terminal (Just a terminal)

so something is wrong with my startup scripts, does anyone know where I can edit them???

---

### Post by alexforcefive on 2008-03-24
Try logging into safe mode, then editing /etc/X11/xorg.conf - the part where it says

```

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option 		"TexturedVideo" "off"
EndSection

```

change it to say:

```

Section "Device"
	Identifier  "aticonfig-Device[0]"
**	Driver      "vesa"**
	Option 		"TexturedVideo" "off"
EndSection

```

This will turn off the proprietary ati drivers, then you can uninstall them (there are instructions on the ati site, or just use envy) and try again. I had an absolute NIGHTMARE trying to get the ati driver to work, so good luck ;)

*edit* did you run ati-config --initial yet?

---

### Post by americano70e10 on 2008-03-24
Well, that worked, didn't install envy yet(will try that now), but I was able to get into gnome normaly... And yes, I did run aticonfig --initial
Thank you...
And did you have any luck Alex?

---

### Post by americano70e10 on 2008-03-25
Installing the driver through envy led me to the same problem, still can only log in on failsafe mode...

---

### Post by alexforcefive on 2008-03-25
> **americano70e10 said:**
> And did you have any luck Alex?

Yeah, I even have direct rendering working :D


> **americano70e10 said:**
> Installing the driver through envy led me to the same problem, still can only log in on failsafe mode...

Try just using Envy to uninstall the driver, and then install it again without Envy. Honestly, making ati drivers work is a dark art. Just make sure you do everything the wiki tells you to :)

---

### Post by americano70e10 on 2008-03-25
> **alexforcefive said:**
> 

Try just using Envy to uninstall the driver, and then install it again without Envy. Honestly, making ati drivers work is a dark art. Just make sure you do everything the wiki tells you to :)

I tried that (and some other stuff as well), but nothing works, it truly is a dark art...
And I've run out of ideas... Got any more???

---

### Post by americano70e10 on 2008-03-25
I gave up and reinstalled the driver "the easy way" (through restricted drivers manager) but now its worse than before, as if there was no card installed at all... I think I'm going to use gnome in failsafe mode till 8.04 arrives...

---

