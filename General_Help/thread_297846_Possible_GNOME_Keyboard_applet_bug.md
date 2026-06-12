---
title: "Possible GNOME Keyboard applet bug?"
date: 2006-11-11
forum: General Help
---

### Post by LxP on 2006-11-11
Hi all,

If I open up the **Keyboard** applet from the **System** > **Preferences** menu, I get this (expected):

[ATTACH]19191[/ATTACH]

If I then click the **Add** button I move to the **Choose a Layout** dialogue, however notice the extra pair of **OK** and **Cancel** buttons (which aren't clickable) where a picture of the selected layout should appear:

[ATTACH]19192[/ATTACH]

This seems to be buggy behaviour even if no keyboard layout is actually selected.  If I then actually select a keyboard layout, the result isn't much better:

[ATTACH]19193[/ATTACH]

Take a look at what happens to the dialogue if I shrink and then expand it in size:

[ATTACH]19194[/ATTACH]

Where should buggy behaviour like this be reported?  I considered posting to [the GNOME Bug Tracking System]("http://bugzilla.gnome.org/") but I'm not convinced that it's a GNOME-specific problem (i.e. I believe something Ubuntu-specific is breaking it).

More importantly, can anyone else reproduce this behaviour?  I almost suspect that only my machine may be doing this (as I have copped a face load of bugs since installing Edgy), but there were no installation errors or anything else to suggest that the installation failed somehow.

---

### Post by komuta on 2006-11-12
Look at this thread:
[http://www.ubuntuforums.org/forumdisplay.php?f=132](http://www.ubuntuforums.org/forumdisplay.php?f=132)
It seems xlib has been broken. A patch is available, but it won't be included  in Edgy because we're already in stable state.

---

### Post by LxP on 2006-11-12
Thanks for your attention.

> **komuta said:**
> Look at this thread:
[http://www.ubuntuforums.org/forumdisplay.php?f=132](http://www.ubuntuforums.org/forumdisplay.php?f=132)

This link may not be what you intended to post (it doesn't lead to a specific thread).  If you still have the link to the thread that you mention (or can easily locate it), could you please post it again?

---

### Post by dpm on 2006-11-12
> **LxP said:**
> Where should buggy behaviour like this be reported?  I considered posting to [the GNOME Bug Tracking System]("http://bugzilla.gnome.org/") but I'm not convinced that it's a GNOME-specific problem (i.e. I believe something Ubuntu-specific is breaking it).

More importantly, can anyone else reproduce this behaviour?  I almost suspect that only my machine may be doing this (as I have copped a face load of bugs since installing Edgy), but there were no installation errors or anything else to suggest that the installation failed somehow.

You can either report it upstream (GNOME Bug Tracking System) if you think it is a GNOME issue or "downstream" on Launchpad ([https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)) if you think it is a distribution (ubuntu) specific issue. In my experience, it is better to report it on Launchpad, since you usually get a quicker response and if it is a non-distro specific bug it will be forwarded upstream anyway. For the problem you are describing, I would file a bug at:

[https://launchpad.net/distros/ubuntu/+source/control-center/+filebug](https://launchpad.net/distros/ubuntu/+source/control-center/+filebug)

BTW, I can confirm at least part of what you are describing on my system, and I do believe it is a bug.

Cheers.

---

### Post by leech on 2006-11-12
I just stumbled upon this bug as well.

I tend to think the reason it's there is due to the gswitchit plugins not being in the gnome-applets package.  Gswitchit is the original program, that was then integrated into the Gnome Desktop Environment.  For some reason the Ubuntu packages don't have the files for these.  It's also broken when you open up the keyboard indicator applet, and tell it to show current layout.  It just shows a blank dialog with a Help and Close button.

Leech

---

### Post by leech on 2006-11-12
Stupid double post.

Leech

---

### Post by LxP on 2006-11-13
> **desp said:**
> I would file a bug at:
[https://launchpad.net/distros/ubuntu/+source/control-center/+filebug](https://launchpad.net/distros/ubuntu/+source/control-center/+filebug)

BTW, I can confirm at least part of what you are describing on my system, and I do believe it is a bug.

Thanks desp; I have [filed a report]("https://launchpad.net/distros/ubuntu/+source/control-center/+bug/71615") for this at that location.

---

### Post by fakie_flip on 2007-03-03
i would also like to know about the plugins for the keyboard-indicator. this program is included with ubuntu (System>Admin>Keyboard Indicator Plugins), so there should be some help on how to get plugins for it. i tried that help button, and that wasn't any help.

---

### Post by Ubimad on 2007-03-22
I have a similar problem, my swiss german/turkish keyboard settings on Edgy 6.10 are not working, 
It displays wired sings when turkish letters should be printed. The keybord switcher in the gnome panel shows the right keybord layout Che/Tur
Strange on the live-cd 6.10 everthing works,  can switch between the different keyboard layouts, swiss german/turkish but not when I have installed Edgy 6.10
Language support for turkish installed.

---

