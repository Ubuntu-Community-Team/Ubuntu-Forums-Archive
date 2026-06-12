---
title: "window size too big"
date: 2007-12-07
forum: General Help
---

### Post by jesse c on 2007-12-07
my main window is too big for the monitor screen.I had it adjusted correctly using the screen resolution window of system/preferences option,but it recently expanded so that the edges are offscreen and now the screen resolution wont allow any changes.When i page down to other screen resolutions and hit allow it stays the same size as it was.The problem showed up after update install but might not be related.I have GUTSY install with compiz set up.Anybody have suggestions? thanks  JESSE

---

### Post by mouseboyx on 2007-12-07
It is hard for me to understand what the problem is. Is your screen resolution set to high for the monitor? Can you explain it again. Try changing your monitor type to make the resolution lower.

---

### Post by windyweather on 2007-12-16
> **mouseboyx said:**
> It is hard for me to understand what the problem is. Is your screen resolution set to high for the monitor? Can you explain it again. Try changing your monitor type to make the resolution lower.

I had the same problem, I think, so let me try to explain.
[LIST]
[*]Installing from CD on a Compaq SR1920NX.
[*]My LCD monitor is native 1280x1024.
[*]I booted the U 7.10 install CD and the system came up and looked fine.
[*]But when I run the installer, the wizard buttons are off the bottom of the screen.
[*]The screen resolution is 800x600 and there are only two choices - 640x480 and 800x600 in screen resolution preferences.
[*]Looks like the installer is designed for 1024x768 minimum size of monitor, but the largest choice I get is 800x600.
[/LIST]

I was able to proceed by dragging the top and bottom "whatever you called them" task bars and status bars, and docking them to either side. That allowed me to see the top 1/2 of the wizard buttons. Whew.. Otherwise I'd be dead in the water for this install, in spite of how really cool it looks.

Looks like you guys need to look into the installer windows size, and the screen resolution choices and make them work somehow. If the installer screen window could scroll - so we could see it all on small screens, then all would be cool for smaller screens. But currently the installer screen cannot be made smaller and will not scroll since it's a fixed dialog. So I was nearly dead in the water for the install. Unless there is an obscure way to change the resolution to the native 1280x1024, or at least 1024x768, the installer cannot be easily seen. My workaround barely makes it possible to do the install.

The Installer Screen is too large for the screen resolutions provided.

Make sense?

Not sure why I didn't get better choices when my monitor and graphics [onboard graphics on a Compaq SR1920NX] allows much larger.

Let me know if this isn't clear to you.

Thanks,
-Windy

---

### Post by windyweather on 2007-12-16
Now that I have the system running, I see the System >> Administration >> Screens/Graphics.

And my monitor - NEC MultiSync1830 is in the list.

One small problem tho. When I choose it and then either Test or Logout and back in, the mouse cursor is gone. Makes it kind of hard to use the system... But the standard Linux / Unix fix applies. When you have a problem, reboot and it will go away.. Sure enough I have my mouse back.  :guitar:

Now I find out that I have to set both the System >> Admin >> Screens & Graphics resolution and the
System >> Preferences >> Screen Resolution to 1280x1024...

and now that I have, all is well...
So it looks like this is the fix for the installer too. I'll give that a try sometime, but the good news that I have my Ubuntu system running on my Compaq.

Cheers  :lolflag:

- windy

---

