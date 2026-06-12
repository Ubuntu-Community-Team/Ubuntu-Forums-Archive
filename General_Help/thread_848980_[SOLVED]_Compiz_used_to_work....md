---
title: "[SOLVED] Compiz used to work..."
date: 2008-07-04
forum: General Help
---

### Post by diablo75 on 2008-07-04
I have a Dell Inspiron 1300 that has (according to lspci) an Intel 915GM/GMS/910GML express graphics controller (rev 03).  This is actually a friends laptop and I'm not sure what he did to cause this to stop working.

What's the best way to troubleshoot this?

---

### Post by diablo75 on 2008-07-05
Bump.  Also, I attempted to run compiz in a terminal window and this is the output I got:

```
user@user-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

What can I do?

---

### Post by sayakb on 2008-07-05
Get Compiz-check: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)
Run the script and see what happens.

---

### Post by diablo75 on 2008-07-05
> **LinuxIsInnovation said:**
> Get Compiz-check: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)
Run the script and see what happens.

Here's what it gave me:

```
user@user-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

---

### Post by sayakb on 2008-07-05
```
sudo apt-get install xserver-xgl
```
And then restart X.

---

### Post by diablo75 on 2008-07-05
> **LinuxIsInnovation said:**
> ```
sudo apt-get install xserver-xgl
```
And then restart X.

I'll have to do this in about an hour (the laptop is on a slow internet connection right now, getting updates).

However, I'm pretty sure that package is already installed.  I came across a thread in here that went about 15 pages deep or more, and a number of people seemed to get their compiz to run after installing that package.  But it didn't seem to work for me.  I'll see if anything works suddenly after these updates and report back in an hour or two.

---

### Post by diablo75 on 2008-07-05
I was right.  The xserver-xgl package was already installed.  Compiz check still produces the same output, as does compiz itself, both basicly stating that XGL is not present (even though it appears to be installed).

What can I try now?

---

### Post by sayakb on 2008-07-05
At a terminal, do:
```
sudo dpkg-configure -phigh xserver-xorg
```

---

### Post by diablo75 on 2008-07-05
It says "sudo: dpkg-configure: command not found".

---

### Post by sayakb on 2008-07-05
Sorry for the typo.. it is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by diablo75 on 2008-07-05
> **LinuxIsInnovation said:**
> Sorry for the typo.. it is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Ok, it appears to have created a new xorg, and tossed a backup along side for kicks....

I restarted the whole system and ran compiz check again, but the same error (no rendering method) is shown.  And running "compiz" at the terminal shows the same output as before...

:(

---

### Post by sayakb on 2008-07-05
Do you have CCSM installed? Otherwise, 
```
sudo apt-get install compizconfig-settings-manager
```Run CCSM (System->Preferences->Advanced desktop effects settings)
Goto General Options->Display Settings
**Uncheck** *Detect Outputs*.
Edit the resolution in **Outputs** and change it to your monitor's resolution.

---

### Post by diablo75 on 2008-07-05
> **LinuxIsInnovation said:**
> Do you have CCSM installed? Otherwise, 
```
sudo apt-get install compizconfig-settings-manager
```Run CCSM (System->Preferences->Advanced desktop effects settings)
Goto General Options->Display Settings
**Uncheck** *Detect Outputs*.
Edit the resolution in **Outputs** and change it to your monitor's resolution.

After doing this, I restarted X and then attempted to enable effects.  No go.  "compiz" also shows the same "Xgl: not present" error too.

---

### Post by isaacj87 on 2008-07-05
Okay, now bear with me here...Please run this command in terminal. Another user, also using an intel chipset, killed his CF by installing the nvidia drivers on his comp. I only ask you to do this because I see a similar output after you run compiz-check. 

```
dpkg -l | grep nvidia
```

If you get results like this: 

```
ii  nvidia-glx-new                             169.12+2.6.24.13-19.42             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                  NVIDIA binary kernel module common files
```

Please remove the nvidia driver...

I have the exact same card. So, if it's something else, I'm sure we can fix it. CF runs like a charm with the i915.

---

### Post by diablo75 on 2008-07-05
> **isaacj87 said:**
> Okay, now bear with me here...Please run this command in terminal. Another user, also using an intel chipset, killed his CF by installing the nvidia drivers on his comp. I only ask you to do this because I see a similar output after you run compiz-check. 

```
dpkg -l | grep nvidia
```

If you get results like this: 

```
ii  nvidia-glx-new                             169.12+2.6.24.13-19.42             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                  NVIDIA binary kernel module common files
```

Please remove the nvidia driver...

I have the exact same card. So, if it's something else, I'm sure we can fix it. CF runs like a charm with the i915.

Looks like this is what my friend did to his laptop.  I just pulled the driver package out.... the kernel header package doesn't want to be pulled without several other restrict modules going along with it... so I'm going to leave that for now.  Waiting on the computer to reboot....

That got it!  Although the performance is horrible (I know this laptop can do better with compiz; it has before).  Is there a way to reset all of Compiz's config to its original defaults?

---

### Post by isaacj87 on 2008-07-05
Yeah, I think so...

I might be wrong, but you should be able to go in to CCSM, click on the button "Preferences" and there's a "Reset to Default" option.

---

### Post by diablo75 on 2008-07-05
Reseting the defaults didn't aid performance any.  I'm going to start a new thread about that...

Thanks a lot for helping me get Compiz up and running again!

---

