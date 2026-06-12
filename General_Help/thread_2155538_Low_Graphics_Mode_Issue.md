---
title: "Low Graphics Mode Issue"
date: 2013-06-18
forum: General Help
---

### Post by macguges on 2013-06-18
Thanks, my Dad reports he's been able to login with a new password.  Can someone help him to fix booting into Ubuntu?

He wrote to me:
> 
I uninstalled any app that related to  Pulseaudio and to ALSA.*  I tried to restart the computer, but the  SHUTDOWN button in the upper right did not work.  So I thought I'd log  off.  When I did that a screen came up it was running in low resolution  graphics mode and a check box that worked with return on KB.  It went to  a following screen:What Would like to do.  There were four choices  including continue console login in low graphics mode screen but the  keyboard was now unresponsive.  I hooked up a regular keyboard thinking  the USB was the problem.  Then finally I rebooted by a powerdown on the  computer front.  I tried to restart Ubuntu, but immediately went to the same low graphics mode screen and same problems as discussed earlier.

Therefore, I cannot even start Ubuntu.   The only choice I would have is to reinstall, but you seemed reticent  on that option.  So, until you visit home again, (your birthday?) I will  not be using Ubuntu.

I could go to the Ubuntu forum via Firefox and ask about the reinstall of Ubuntu 12.10 in a repair mode.

*On Sunday we began troubleshooting the issue of no sound in Ubuntu.  That would be the next priority after correcting boot up.

---

### Post by zero2xiii on 2013-06-19
Hay,

> I uninstalled any app that related to Pulseaudio and to ALSA.

This was not smart, nor necessary to debug audio.
This would have uninstalled your DE and related stuff as well since that is also somewhat dependent on ASLA and pulse audio.

To fix this (I assume you are using gnome - Plain ubuntu) you need to boot to a console:
During grub screen, select the options with "Recovery mode" in brackets at the end.
Select the "Root Terminal" option.

Now either log in, or just continue, this depends on how the system was set up, on default root has no password set so this does not require a password to log in.

Now in terminal type:
```
sudo apt-get install gnome
```

This should re-install the complete gnome environment. After that has successfully completed:

```
sudo reboot now
```
or
```
sudo shutdown now
```

Then try booting the normal way. If the problem persists then it is likely something other than the actual environment and you should supply a lot more "technical" details for us to figure out exactly what is going on.

Cheers and good luck

EDIT:
See my signature for the "Help us help you" thread link, there is a link on how to debug audio under ubuntu, also a lot of stuff you can use to "help us help you" if this issue persist.

---

### Post by macguges on 2013-06-28
I'm reposting responses from my father to the forum because he hasn't learned how to post replies yet.> I was able to see the message you posted and  read the suggested procedure.  ...  I  don't even know how to boot into console mode.  The terminology is  confusing. Since I got the message I could not post to Ubuntu forums, I  don't know how to proceed to even thank this guy for his suggestions.

I asked my dad, "So tell me: what exactly do you see when you boot into Ubuntu?"  He replied:> A small window that says it is operating on reduced resolution.  A choice to continue on reduced resolution or make changes.

I  tried the reduced resolution choice and it led to a blank screen with  the cursor line blinking in the upper left corner.  That cursor is  unresponsive to typing on the keyboard.  I don't think it ever evens  starts up Ubuntu.

My inclination is to reinstall Ubuntu 12.10 using the CD I  have, but I am reluctant because it may erase all my personal files and  apps already installed.  One thing it has to do is reestablish my  resolution settings for the monitor since that seems to be the  problem..  So when I managed to log onto Ubuntu users group, I got the  message I could not submit messages due to the fact that I had no  history of having done so.  The perfect Catch 22.

From his reply, my intuition is the small window that says "operating on reduced resolution" is a message from Ubuntu's boot up sequence.  How would you recommend he get to a shell prompt from this point?  It's important that he have clear instructions he can print out from within Windows.

Have anyone written an introduction or cheat sheet for using the forums?  Perhaps if he had some extra help in that regard he could post his own reply next time.

Thanks in advance!

---

### Post by claracc on 2013-06-29
I think, this link [https://wiki.ubuntu.com/UbuntuForums](https://wiki.ubuntu.com/UbuntuForums) can help your dad to know about ubuntu forums and post in them

---

### Post by macguges on 2013-07-01
While visiting my dad we set up a chroot from the livecd and ran "apt-get install gnome".  That's now running.  We'll see when that's done if that corrects his installation.

....  Okay!  His desktop is functioning again.  He's still got other problems, but this issue stands resolved.

Before closing this thread, however, I did observe a problem with the  "operating on reduced resolution" menu.  On the first attempt I tested the first option, which led to the indefinite blank screen with flashing cursor.  On the following attempts there was no response from neither USB keyboard, PS/2 keyboard or the mouse, which is why we ended up using the liveCD.  It's fortunate I could demonstrate to my dad the technique of creating a chroot cage to repair a linux installation, but at the same time I wonder what the common user would be expected to do with that "reduced resolution" menu when all inputs stop working.  Perhaps it was just my dad's bad luck to have broken his system so badly that even the fail-safe maintenance menu would break.

---

