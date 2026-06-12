---
title: "Messed up the X Server/GDM"
date: 2007-10-21
forum: General Help
---

### Post by cattleeyes on 2007-10-21
During an installation of Beryl, my X server got messed up and I've been left without a graphical interface.

It looks as though my problem should be solved by the various
sudo dpkg-reconfigure xserver-xorg options, but every time I do this, it gives me a message that files will be overwritten and absolutely nothing happens.

Restarting GDM doesn't seem to help anything without first fixing this problem.

I'm without a computer right now until this problem is solved (my cd rom drive is suddenly having its own troubles as well, so reinstallation has proven to be a real pain as well) so if anyone knows of any other possible way to fix this, please please please let me know.

---

### Post by phibit on 2007-10-21
What kind of graphics card do you have, and what drivers are you using?

Also, at what stage of the Beryl install did this start happening (after editing your xorg.conf ?)

---

### Post by cattleeyes on 2007-10-21
I think things got messed up after editing xorg.conf.  My problem now is that I've spent so many hours editing this file I'm not even sure what it looked like in the first place.
I actually don't know what graphics card I have.  How do I c heck?

Right now under "Device" I have:
NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] and the Driver as "Vesa," but only because of my most recent attempt at dpkg-reconfigure xserver-xorg.  I really have no clue what it was to begin with.

Now I've learned that after the dpkg-reconfigure process, if I run "startx" I can at least view and edit in a graphical interface which is handy since the text of prompts are no longer cut off, but the moment I restart (GDM or my system as a whole), the xserver still won't start.

Any ideas?

---

### Post by cattleeyes on 2007-10-21
DEVELOPMENT:

After quitting out of my "fake" X server screen, I'm getting tons of error messages saying:

"Error opening /dev/wacom" which is apparently listed as a driver.  I have no idea what that is or what it should be.

---

### Post by phibit on 2007-10-22
The wacom thing isn't much to worry about, I have those errors on both my laptop and desktop

Here's what I suggest you try, since it looks like you have a nvidia card.

If you can get a console, or a terminal or wtv, do the follwing

```
sudo nano /etc/X11/xorg.conf
```

Change the line that says VESA as a driver to

```
Section "Device"
        ....
        Driver          "nv"
        ... 
```
End Section

That's the default nvidia driver and should work. Also, look at the bottom of your xorg.conf file for 

```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```


And change Composite to Disable.


Cheers

---

### Post by cattleeyes on 2007-10-28
All of these settings are exactly what I have but the XServer still won't stick.

I guess I'm just really confused as to why I can run a safe mode-esque X Session with "startx" but can't get an X Session to run naturally at boot.

---

### Post by cattleeyes on 2007-10-28
All of these settings are exactly what I have but the XServer still won't stick.

I guess I'm just really confused as to why I can run a safe mode-esque X Session with "startx" but can't get an X Session to run naturally at boot.

---

