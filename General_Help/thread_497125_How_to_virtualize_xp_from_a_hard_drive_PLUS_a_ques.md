---
title: "How to virtualize xp from a hard drive PLUS a question about mouse detection"
date: 2007-07-09
forum: General Help
---

### Post by djrobthaman on 2007-07-09
Hi everyone.

I found this great HOWTO on booting up a copy of xp already installed on a local physical disk.  I've been looking for something that works and will share it with you in case anyone else was looking too.

[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")

Now, I followed the instructions in the original post and with no extra steps (except for getting a serial for vmwareserver from the site) have windows booting in ubuntu 99.9%good.  The only thing is I don't think vmwareserver is detecting my mouse correctly.  When I grab in My keyboard works fine buut there is no responce from the mouse (I have an IOGear mouse and keybourd that connect wirelessly to the same USB port).

I finally got an error message when I tried to make the window fullscreen where it said "Failed to autodetect the mouse type. Please set the mouse type and device using Virtual Machine Settings to enable full screen mode for your virtual machine.  Failed to switch to full screen VGA mode."

When I go the menu it suggests there is no "iogear" selection, so I'm not too sure how to go ahead.  I guess I could try them all but has anyone already encountered this problem and shed some light on the situation?

The options I haver are "autodetect" (This is what I have selected at the moment), "intellimouse explorer ps/x", "intellimouse ps/2", "Logitech mouseman+ ps/2", "microsoft serial", "mouse systems", "mouseman serial", "ps/2".  I can also select the exact location of the mouse in the dev folder.

What should I do?

Thanks for the help.

---

### Post by djrobthaman on 2007-07-09
OK,

So "Microsoft serial" worked.  Almost there.  Now It won't go to full screen and gives this error:

"Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.  Failed to switch to full screen SVGA mode."

How would I add this section (well, I guess I'd start up gedit and open up the file and edit it).  What would I add to this section?

Thanks again.

---

### Post by atlfalcons866 on 2007-07-09
try using virtualbox its free and runs great.

---

### Post by djrobthaman on 2007-07-09
I would if I knew how.

Can I just load the same virtualization file that vmware made?

By the way, Every time I switch from booting into windows and virtualizing I have to re-authenticate.  I followed an instruction in one of the comments of the howto where it said I should add "SMBIOS.reflectHost = TRUE" to the vmx file.

Of course this didn't work.  Do you know any other way I could get it to stop asking me to re-activate?

Thanks

---

### Post by CowzRule on 2007-07-09
> **djrobthaman said:**
> OK,

So "Microsoft serial" worked.  Almost there.  Now It won't go to full screen and gives this error:

"Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.  Failed to switch to full screen SVGA mode."

How would I add this section (well, I guess I'd start up gedit and open up the file and edit it).  What would I add to this section?

Thanks again.

Open xorg.conf```
gksudo gedit /etc/X11/xorg.conf
```Scroll down to the "Screen" section and add the screen mode, i.e. 800x600, that you want to have. Or change XP's screen mode to one of the modes listed in that section.

---

### Post by djrobthaman on 2007-07-10
Cowzrule,

I looked at the screen section and as far as I can see 1024x768 are in all display sections.  So I tried that res but it didn't work.  Do you know what else I could do or how I could edit the xorg?

PS Here is my screen section from the xorg file.

```

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "LM540"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

---

### Post by CowzRule on 2007-07-11
I read the manual at [vmware]("http://www.vmware.com/support/pubs/server_pubs.html") and that's where I learned about the screen modes in xorg.conf. At least that's how I understood it. The only thing I can think to do is to boot XP in window mode and be sure that your screen mode in XP is set to one of the modes in you xorg.conf. Since 1024x768 is one of your xorg modes, make sure XP is set the same. Other than that, I'm afraid I can't think of anything else, sorry.

---

