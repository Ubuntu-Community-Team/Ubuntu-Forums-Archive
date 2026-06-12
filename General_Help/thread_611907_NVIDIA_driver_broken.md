---
title: "NVIDIA driver broken?"
date: 2007-11-13
forum: General Help
---

### Post by Fittersman on 2007-11-13
my nvidia driver doesnt work anymore for some reason, i cannot figure out why. The only thing i can think of that may have caused the problem was the latest batch of updates released today. I tried reinstalling ubuntu 7.10 even, and even after doing a fresh install i still have the same problem. I did nothing that may have caused problems other than the update. 

is there anyway i can roll back my system and undo the updates? (although arent those uninstalled when i did hte reinstall? or are the updates stored on the /home because i have a separate partition for /home)

---

### Post by dabl on 2007-11-13
Did you install a kernel upgrade?  That will break the proprietary driver installation every time.

If you used the Envy script installer from [[COLOR="SeaGreen"]**here**[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) then you would only have to log in at the text prompt and enter ```
sudo envy -t
``` to reinstall it.

To get some kind of GUI running, so you can go get Envy, you can configure a VESA display by running ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "NO" at the first prompt, and choose "VESA" as the display type, and then take the defaults until you get to the monitor.  Choose a comfortable resolution like 1280 x 1024, and refresh rates that your monitor can handle.  When you finish, it will dump you back to the command line, and you can enter ```
startx
``` to get your GUI running.

To install Envy, download the file "envy_0.9.8-0ubuntu13_all.deb" which is about halfway down the page linked above, right-click it and "install with Gdebi". It will put an icon in your System folder, and as stated above, it will run in text mode as well.

:)

---

### Post by Fittersman on 2007-11-13
there was no kernel upgrade (even if there was though i tried reinstalling the driver) and i didnt use envy to install the driver (i installed the nvidia driver myself)

when i tried to install envy i get this error:
Error: Dependency is not satisfiable: xserver-xorg-dev

so, i went to symnatec to see if i could find that package and there is not xserver-xorg-dev package. All other packages that have xserver-xorg as the prefix are installed however.

I also tried 'sudo apt-get install xserver-xorg-dev' but that package was not found

Thats about all i can think of..

---

### Post by Genisis X on 2007-11-13
I'm having the same problem. After rebooting my system tells me that it cannot detect my video hardware  and will boot using safe graphics mode.

Then the screen goes blank, the light on it starts blinking which means that it is not getting any signal.

I was configuring my keyboard in xorg.conf so I rolled back to the backup but it still happens so I  think it was the nvidia update.

Also: Envy doesn't work with Gutsy yet, unfortunately.

So I'd really ike to know if Ubuntu has a rollback feature like Windows XP. Really!

I'm fed up with it atm but later tonight I might try and reconfig my x server to boot with VESA like you said dabl.

I only installed it on the weekend and just had everything customised to the way I like it. Grrr!

System:
Leadtek GeForce 8800GTS 640mb
Athlon x2 x64 3800+ (2.0ghz)
1.5 gbRam
ASUS A8N5X

-X

---

### Post by Fittersman on 2007-11-13
yah, there must have been a problem, but i dont understand why doing a complete reinstall didnt do anything to fix it :S

i got my resolution and stuff working with either the vesa or nv driver (i dont remember which one im using right now) but its a little laggier than it should be so i am eagerly awaiting a fix for this...

---

### Post by Genisis X on 2007-11-13
Yea, its a bit strange that a reinstall didn't fix it.

I might try to roll back the new drivers via aptitude remove nvidia-glx-new and aptitude install nvidia-glx but I don't hold much hope for that course of action.

Hope this gets resolved pretty quickly as well. :(

-X

---

### Post by dabl on 2007-11-14
> **Genisis X said:**
> 

Also: Envy doesn't work with Gutsy yet, unfortunately.



That's not correct today -- Gutsy (32-bit and 64-bit) are at the top of his "supported OS" list:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Completely reinstalling the OS is unlikely to remediate an X server/video driver issue, unless there's evidence that the underlying OS has something broken.

Envy will automatically remove nvidia-glx-new or any other driver package, AFAIK.  If you're not sure, you can always first configure a VESA display:

```
sudo dpkg-reconfigure xserver-xorg
``` choose "NO" to autodetect and then next choose "VESA" as the display type, and when you're done with the script, and it dumps you back to the CLI, do ```
startx
``` and then you can run your browser and get Envy and use that to install the proprietary driver.

:)

---

### Post by Damanther on 2007-11-14
I had the same problem with the updates a couple of days ago.

Running envy -t at the command prompt fixed it right up.

---

### Post by Zorael on 2007-11-14
If packages that *should* be satisfiable (xserver-xorg, for instance) aren't, you need to check your repositories. Enable all of them and try again, then remove them again if you feel it conflicts with your ideologies. :>

---

### Post by Fittersman on 2007-11-14
got envy to work and its all good now, thanks for the help :)

---

### Post by Genisis X on 2007-11-14
Got envy up and running and all is now well. Problem solved.

Thanks guys.

-X

---

