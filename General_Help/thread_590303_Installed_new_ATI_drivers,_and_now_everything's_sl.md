---
title: "Installed new ATI drivers, and now everything's slooow"
date: 2007-10-24
forum: General Help
---

### Post by Kymus on 2007-10-24
Now this is strange... 

Ok, I installed the new ATI drivers the other day, and everything was great. Compiz was working fine and everything was good. Well, I noticed I was getting an error when I tried to run the ATI Catalyst Control Center. So, I decided to look at the restricted drivers and it said it wasn't in use... alright, whatever... don't care.

Well, I tried running *winecfg* and Wine was giving me an error message a mile long. I look at it for a minute before I posted for help, and I saw that it was complaining about something with the ATI drivers. Ok, I figured I would enable the restricted driver and see if that works. 

It did, and wine didn't complain, but then later I misunderstood something and reinstalled the new ATI Drivers as well as enabling xserver-xgl (I believe that's it.. somewhere else I read someone was having problems getting compiz to work.. that's what got me to do that). I do all that and restart, try to log in and.... it's taking forever...I restart again, log in, and it's taking a while, and then the screen goes black (first it's half of the screen, then the other half), then things load.... but now, it's sloooooow.... 

Uhh, ok, so I disable all the eye candy. Nope, it's still slow. When I would scroll in firefox, it looked like it does in windows safe mode... Ok, so I uncheck the restricted driver, reboot, log in and..... it's taking forever.. then it goes black, and goes back to the login screen.

When I login using the failsafe session, it all loads, and it's at normal speed. And now, I am puzzled. :confused::confused:

---

### Post by Kymus on 2007-10-24
I should probably mention another issue while I'm at it..

my CD/DVD-ROM drive.. yeah, being funky too. It'll show up, but when I try to read from it, I get this error:

> Unable to mount media
there is probably no media in the drive 

I've tried different disks, and each time it's the same. I just used it in windoze this morning, so as far as I know, there are no problems with the hardware itself.

**edit:** in my desperation and absent mindedness, I created a separate thread dealing with this issue [here]("http://ubuntuforums.org/showthread.php?t=592299"). More information about the problem has been collected there.

---

### Post by Kymus on 2007-10-25
Ok here's an update.

I poked around on the forum some more and found [this site]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support"). I did up to step #4, rebooted, and crossed my fingers......

Logging back in, there was no slowdown issue! So then I do the rest of the steps, reboot, and well, I wasn't so lucky this time. It booted to the terminal, then displayed that schpeel about how gnome is in safe mode. I selected my monitor from the list, and it had my video card correct (ATI Radeon X800 GTO), and it goes into gnome.

I perform steps 1-4 again, reboot, and this time I log in fine, and there's no slow down, but fo course the restricted drivers are disabled (which I assume means that my card is basically crippled if I want to do anything high-end?).

I just gotta figure out how to go back to how things were.... drivers installed, and no slow down.. it was like that before.... perhaps if I don't mess with the xorg.conf like the how-to says?

I'm still trying to find a solution to my CD/DVD-ROM

---

### Post by Kymus on 2007-10-26
Well, I've narrowed things down and have come full circle.

I decided to hold my breath and re-enable the restricted drivers. Rebooted, and everything was good... except, no desktop effects (though now CD's and DVD's were being recognized!). I kept getting the error "the composite extension is not available" or some nonsense.. I then search the forum and found [this thread]("http://ubuntuforums.org/showthread.php?t=576624"). I followed the instructions, and I edited xorg.conf so that composite was on. Then, I installed xserver-xgl, did a 3 finger salute and.... yeah, back to square 1: sloooooow mooooooo

So it seems that **xserver-xgl** is causing this.

..some help?

---

### Post by poofyyoda on 2007-11-15
I have exactly the same problems as you have.  (apart from the CD/DVD drive)
After I finally installing the ATI driver, following guides, I rebooted and the system just goes too slow.  Even dragging a selection box on the desktop lags a lot.  Compiz also doesn't work.

---

### Post by Colro on 2007-11-15
> I just gotta figure out how to go back to how things were.... drivers installed, and no slow down.. it was like that before.... perhaps if I don't mess with the xorg.conf like the how-to says?

The newest ATI driver was pretty terrible for me, as well. Sadly, Ubuntu doesn't have a native way to revert your drivers, I hope it's implemented eventually.

The good news, though, is that you're not screwed. Envy is able to install 8.40.7, which is very stable for me and doesn't slow down one bit with xserver-xgl installed and compiz on full blast.

```
sudo apt-get install envy
```

Once it's installed, open it from Applications -> System tools. Then just click 'Install ATI driver', click apply, and let it do its thing.

---

### Post by Kymus on 2007-11-19
Well, today I tried fiddling with the ATI Drivers again, this time installing through envy. While that had its own problems (*ugh*), the slow-down issue seems to have vanished, for now.

---

