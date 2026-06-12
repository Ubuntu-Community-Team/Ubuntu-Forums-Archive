---
title: "Log in to Gnome then it logs me right back out"
date: 2007-12-31
forum: General Help
---

### Post by vanndrage on 2007-12-31
hello, i just replaced my video card from an ATI to an Nvidia because of video playback issues. Got the driver loaded and all for the new nvidia card but the only thing is i can only log in to Gnome Failsafe session. When I try to log in normally to Gnome I enter my un/pw and it takes it then shows the default tan background and my mouse cursor for around 10 seconds or so then it takes me right back to the log in screen. Doesnt give any errors or anything. My hard drive is not full as some other posts suggested. Any help would be greatly appreciated.

---

### Post by -grubby on 2007-12-31
maybe this will help you: enter 
```
gksudo nvidia-settings
```
into the terminal and (after it loads) look around at the parameters to see if your screen resolution or something goes over what is possible with your video card

---

### Post by avik on 2007-12-31
Are you running Compiz on log-in?

---

### Post by lswest on 2007-12-31
did you change the entry for the nvidia driver in xorg.conf?  might want to either edit it using ```
 sudo vim /etc/X11/xorg.conf
``` in a tty screen (get there by ctrl+alt+F1) or by running ```
sudo dpkg-reconfigure xserver-xorg
``` (i think that is the command, not sure, anyone can feel free to correct me.)

btw, happy new year guys!

---

### Post by -grubby on 2007-12-31
> **lswest said:**
> did you change the entry for the nvidia driver in xorg.conf?  might want to either edit it using ```
 sudo vim /etc/X11/xorg.conf
``` in a tty screen (get there by ctrl+alt+F1) or by running ```
sudo dpkg-reconfigure xserver-xorg
``` (i think that is the command, not sure, anyone can feel free to correct me.)

btw, happy new year guys!

that is the command to redo the whole xserver (including keyboard, mouse,etc) but:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` is just for the video section

---

### Post by vanndrage on 2007-12-31
hi, I really appreciate all the very quick replies, i tried doing gksudo nvidia-settings and it lists my resolution and monitor correctly, i did change the refresh rate from auto to 60 but that still did not help my problem. i also attempted sudo dpkg-reconfigure xserver-xorg before even loading the drivers because i didnt have any video at all before doing this, then after i did that it at least brought me to the GUI login so i could get in and enable the restricted nvidia driver. i also loaded the nvidia driver using Envy but this had the same effects as the restricted driver. 

I have not tried this yet though: sudo dpkg-reconfigure -phigh xserver-xorg

will give it a shot and let you know, any other suggestions are appreciated. Thanks!

---

### Post by vanndrage on 2007-12-31
> **avik said:**
> Are you running Compiz on log-in?
yes, i am compiz at login.

i did the reconfigure thing that nathangrubb suggested, this looked like what i already did so i just escaped out of it, then i attempted to log in to normal gnome and it kicked me out again but then i noticed my resolution went to a bigger resolution so i tried it again and now i am in normal mode. my compiz or anything is not working though like it was prior to installed the nvidia card.

---

### Post by vanndrage on 2007-12-31
ok, after doing the reconfigure and escaping it, it must have disabled my nvidia driver and that is why i was able to get in. after i went into the restricted drivers again and re-enabled the nvidia driver and rebooted now it does the same exact thing as before, starts to log in, shows the tan background then kicks me right back to the login screen.

---

### Post by lswest on 2008-01-01
ok, thanks for correcting me nathangrubb, i knew i was missing something:P  maybe it would be best to stick with the drivers that let you log in?  and, what card exactly is this?  and what driver are you using? (legacy/new?)

---

### Post by vanndrage on 2008-01-01
> **lswest said:**
> ok, thanks for correcting me nathangrubb, i knew i was missing something:P  maybe it would be best to stick with the drivers that let you log in?  and, what card exactly is this?  and what driver are you using? (legacy/new?)
hello, i cant really use the ones that let me log in because those are just the VESA drivers i believe which i definately dont want. i have tried using both the restricted driver that is provided w/ ubuntu and then i have also tried installing the actual nvidia driver via the Envy automated driver install. the card i have is a Geforce Ti 4600 128MB, its not a new card but it works a lot better than the ATI card did for any kind of video playback and hopefully better for compiz (which i havent got to see yet)

so just to recap i can only get into normal gnome mode when i go back thru the reconfigure and select VESA, then i can log in normally but only until installing the nvidia drivers. Is it possible there are still traces of the ATI driver and it is conflicting? i did uninstall the ATI driver thru Envy which is automated. Any other suggestions would be greatly appreciated.

---

### Post by vanndrage on 2008-01-04
any other ideas for me to try?

---

### Post by vanndrage on 2008-01-04
got the problem fixed from the help of this other thread [http://ubuntuforums.org/showthread.php?t=583642](http://ubuntuforums.org/showthread.php?t=583642)

just had to remove xserver-xgl by running the following command:

apt-get remove xserver-xgl

after doing this and logging out, then logging back into regular gnome it lets me in, and compiz is back to working also.

only thing that i havent seen before is when it is logging in my panel bar and icons show up for a few seconds then they disappear and i just see my background for about 5 seconds or so then it all comes back and everything is usable.

---

