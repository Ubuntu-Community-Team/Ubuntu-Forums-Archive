---
title: "ctrl+alt+fn doesn't bring up a console"
date: 2016-03-22
forum: General Help
---

### Post by a-you on 2016-03-22
When I do  ctrl+alt+Fn it just goes to a blank screen. Actually it goes to a washed out white  screen. Ctrl+alt+F7 does get me back to the GUI though.

How can I get to those other tty consoles?? Or it may be that it's a display issue, that they simply don't display, though I wouldn't know why? Or do I have to enable this feature somehow? I have looked at my BIOS and there isn't any mention of anything relating to this there.

Thanks for any help!!

ubuntu studio 14.4 64 bit on a sony vaio vpcf116fx

To forum admin people: I initially posted this in the ubuntu studio forum but didn't receive any answers. I'm thinking it may be more general so I thought to move it here, but moving it didn't seem to be an option, so I'm asking here now. Sorry if that was the wrong way to go about that. Please delete the question from the ubuntu studio forum if you think that would be appropriate.

---

### Post by jimmy-frydkaer on 2016-03-22
ctrl+alt+t bring up the terminal

---

### Post by dragonfly41 on 2016-03-22
Perhaps you are looking for Ctrl+Alt+**F1** and not Ctrl+Alt+Fn ?

---

### Post by ajgreeny on 2016-03-22
In your other (now closed and removed thread) you talk about using the Ctrl+Alt+Fn (is that Function key or do you mean on F1-6 keys along the top of the keyboard?

Can you please confirm which keys you are pressing to avoid any confusion; I suspect you do mean the F1-6 keys but would like to be sure.

---

### Post by grahammechanical on 2016-03-22
That laptop requires the user to press an Fn key in order to get the use of the 12 function keys. The sequence Crtl+Alt puts the OS (Ubuntu) into a mode to accept the press of a function key (F1 - F12) but the sequence Ctrl+Alt+Fn is putting the OS in the mode to accepct the press of a function key and the keyboard into the function key mode but the number key that corresponds to a function key is not being pressed. So, no switch to a Linux console.

Ctrl+Alt+Fn+1 or Ctrl+Alt+Fn+2 and so on. Or, Fn+Ctrl+Alt+1. Look at what is printed on the numeric keys.

Check out page 33 of the laptop's user guide.

[https://docs.sony.com/release//VPCF110_series.pdf](https://docs.sony.com/release//VPCF110_series.pdf)

Notice the way that Ctrl+Alt+F7 gets the user back to the desktop. That is happening because the FN key has already been pressed and so the key that doubles or trebles as F7 works as F7 in that instance.

Regards.

---

### Post by ajgreeny on 2016-03-22
Wow!  What a palaver just to get to a TTY command-line.

---

### Post by a-you on 2016-03-22
Oh I'm sorry I just realized why that was unclear: yes there is an Fn key as well, but I didn't mean that. And I didn't mean that I was pressing that Fn key plus one of the numbered function keys, because doing that invokes a special vaio function, like muting the audio for example or adjusting the brightness. (And @jimmy-frydkaer: control+alt+t doesn't invoke a terminal. I don't mind that because I  have a launcher in the panel, but the console issue is a drag.)

I meant that pressing control+alt+F1 through F6 doesn't lead to a console, instead it goes to a washed out white screen. Actually that washed out screen also appears briefly when I shut down sometimes, so I'm wondering if it might have something to do with the fact that I'm using the nvidia driver.

I'm going to try switching to the nouveau driver and see if that fixes it... I'll report back shortly. Thanks everybody for your thoughts!! It's still not clear why this doesn't work!

Well, switching to the nouveau driver did in fact allow me to switch to a console by pressing control+alt+function key 1-6. Unfortunately it introduced a different problem: the only resolution available is 640 x 480 so all icons, panels, etc are huge. Also the refresh rate is different from what nvidia had it as and I think nvidia is probably correct (59.9Hz). I recall dealing with this when I started using the nvidia driver but the only setting I recall changing was setting a custom DPI of 96. Maybe the only way to go back to nouveau would be to purge nvidia but I'm not in the mood to do that.

Or if there's an nvidia setting that allows me to get to the consoles. It seems likely that the console feature is actually working, just that they're not being displayed.

If anybody has any ideas---either about nvidia settings or about nouveau settings that would work---I'd appreciate it. Thanks again in advance.

---

### Post by a-you on 2016-03-23
After a lot more searching it appears that this is a fairly common issue when using an nvidia driver. Probably the only way to fix it is to purge nvidia and start fresh with nouveau. Since I'm using 14.4 I'm thinking to just wait until 16.4 is out then go back to using nouveau.

---

