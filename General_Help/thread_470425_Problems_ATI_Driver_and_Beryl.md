---
title: "Problems ATI Driver and Beryl"
date: 2007-06-11
forum: General Help
---

### Post by melenor on 2007-06-11
Yah i have looked all over though old topics and posts and i see no where, that helps me. i tried to install beryl but that doesn't work and when i tried to enable the restricted drivers it wasn't there yet i had already downloaded it, and i tried all that terminal stuff and it got me no where when i do a "fglrxinfo" i get it comes up with
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
I have no idea what this means, i have started moving completly to ubuntu, with XP and Vista for games only and in case i need it for other things, i saw beryl and thought that would be nice but i tried it with no luck than i looked up on the internet how to fix the problems and they pointed me to the ubuntu wiki and i followed the directions but i am still stuck.

Thank you for your help.

---

### Post by Inspire1997 on 2007-06-11
Which ATI card do you have? I have a x1600 and basically anyone with the 1000 series cards are screwed.

---

### Post by mifi on 2007-06-11
> **Inspire1997 said:**
> Which ATI card do you have? I have a x1600 and basically anyone with the 1000 series cards are screwed.I had an X1300. I did a quick try, but on reading the comments in this group about the ATI driver XGL etc.  I decided to save myself lots of time and frustrations and bought an nVidia 7300 instead. It is not very expensive, runs well and has saved me a lot if troubles.

mifi

---

### Post by melenor on 2007-06-11
i really think buying another card is out of the question right now i have an X1800 and i read somewhere that i had to enable the restricted drivers and i did expect nothing changed expect for the fact that now it says "The composite extension is not available" when i try to access the Desktop effects.

---

### Post by mifi on 2007-06-11
> **melenor said:**
> i really think buying another card is out of the question right now i have an X1800 and i read somewhere that i had to enable the restricted drivers and i did expect nothing changed expect for the fact that now it says "The composite extension is not available" when i try to access the Desktop effects.
With nVidia this would be enough. However, with the ATI proprietary driver, there is more to it.

Have you seen this thread: [http://ubuntuforums.org/showthread.php?t=462823&highlight=ATI+X1300]("http://ubuntuforums.org/showthread.php?t=462823&highlight=ATI+X1300")

mifi

---

### Post by KitChy on 2007-06-11
> **melenor said:**
> i really think buying another card is out of the question right now i have an X1800 and i read somewhere that i had to enable the restricted drivers and i did expect nothing changed expect for the fact that now it says "The composite extension is not available" when i try to access the Desktop effects.

I have the same card and beryl works fine here for me :D

EDIT: This is the guide that I followed:[Clicky]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by melenor on 2007-06-11
altright i went though the guide an now when i put in fglrxinfo it comes up with My card X1800 however whenever i try to enable the desktop effects it comes up with composite extension not available.

---

### Post by weblordpepe on 2007-06-11
The following needs to be a sticky:
The official ATi drivers will not allow you to use Beryl/Compiz.
The open-source drivers will allow you to use Beryl/Compiz, but graphics in general aren't as fast & some games like Doom3 don't render correctly.

---

### Post by melenor on 2007-06-11
but how do i make sure that the open-source drivers are installed and not the official ATI drivers, because i want to enable beryl on my computer that is where my problem is.

---

### Post by mifi on 2007-06-12
> **weblordpepe said:**
> The following needs to be a sticky:
The official ATi drivers will not allow you to use Beryl/Compiz.
The open-source drivers will allow you to use Beryl/Compiz, but graphics in general aren't as fast & some games like Doom3 don't render correctly.
And the open source drivers do not support, appearantly, all resolutions. Correct me if I am wrong, but I do not think 1680x1050 on a wide screen is supported.

m

---

### Post by maestrobwh1 on 2007-06-14
Not that it matters, but I use the standard ATI driver that comes with kubuntu 7.04 and I have beryl installed.  I have a older radeon 7200 with 128 MB.

It does work pretty well, but does flaky things from time to time.  Example, sometimes the highlight on selected items just stops working.  I just drop back to kwin for that session.  I guess I could do things to make it more "stable"

I also never had any luck with the ati fglrx driver.  On dapper, on edgy, on feisty.  It would always "install" with adept by putting a pretty icon in the k menu, but when launched, it would give some goop about not having all of its parts working and was using mesa instead.  It was a pretty pop up screen that looked cool, but with no settings, obviously I had to actually do some crazy thing with xorg,conf.  Always got me not being able to start x if I forced it, even with good "directions."  No kde for me.  Just an ugly shell.  Of course, I just copied my old file back over my "this has to work this time" effort.  Back to the "standard and usable" driver.

Word to the wise for all those venturesome spirits.  Clonezilla.org  Do it first!

---

### Post by weblordpepe on 2007-06-15
> **mifi said:**
> And the open source drivers do not support, appearantly, all resolutions. Correct me if I am wrong, but I do not think 1680x1050 on a wide screen is supported.

I'm using it right now dude. I know that it puts the entry in the screen resolutions list in Gnome but doesn't work correctly. The solutions an easy one though.

You just need to add it to your xorg.conf manually. This is my "screen" section:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		**"1680x1050"**	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

That bit in bold is the bit I put in. I just guessed really and it worked. I am on a Dell Insipron 8600 laptop.

---

### Post by mifi on 2007-06-15
> **weblordpepe said:**
> I'm using it right now dude. I know that it puts the entry in the screen resolutions list in Gnome but doesn't work correctly. The solutions an easy one though.

I did what you explain here, but it still refused to go to 1680x1050.
Perhaps I gave up too quickly.

m

---

### Post by weblordpepe on 2007-06-15
Maybe you should hit the Enter key harder. :P
Heck Im not sure.  Be sure to seperate the entries by tabs and not spaces. Or even just copy-paste that section maybe? I only added the 1680 resolution for 24 bit colour cos anything else sux.

And why doesnt Linux ever have 32 bit colour?

---

