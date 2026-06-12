---
title: "Nvidia Driver Install Fail"
date: 2020-05-29
forum: General Help
---

### Post by UserJB on 2020-05-29
Hi,  I'm running Ubuntu 16.  I installed latest Nvidia drivers and rebooted.  Fail.  I only see a flashing cursor.  What do I do next?

Nvidia install scripts claim to save a copy of the xorg.conf file.  When I look at that file, it's empty:

    -rw-r--r--   1 root root     0 May 29 14:15 xorg.conf.nvidia-xconfig-original

Can I boot without the X server and somehow uninstall the latest Nvidia driver?

Any other options?

---

### Post by CelticWarrior on 2020-05-29
> **UserJB said:**
> Can I boot without the X server and somehow uninstall the latest Nvidia driver?


Sure. You can and should do that. Then install the recommended version from the official repositories, not with the Nvidia scripts.

---

### Post by UserJB on 2020-05-29
Okay.  A) How do I boot without the X Server?  B) What official repositories are you talking about?

---

### Post by UserJB on 2020-05-29
Oh, wait.  I get it.  I have to ask a separate question on how to boot without the X Server.

---

### Post by CelticWarrior on 2020-05-29
With Ubuntu 16.04 (Unity) you can press CTRL+ALT+F1 to obtain a TTY (CLI). Login and run the script again with the argument to uninstall.

The official repositories are the ones by default in Ubuntu from where we install software and updates. Nvidia drivers are there already, properly packaged and tested for the specific release. If your Nvidia card is newer and requires a newer driver version then you should add the Graphics Drivers PPA to get that newer version. Never run the binaries/scripts downloaded from Nvidia. Use their website only to check which driver version to install as not all versions support all hardware, quite the opposite, older hardware will be supported only by a long term support version up to the point that version is still compatiblem with newer kernels.

---

### Post by Autodave on 2020-05-29
You may have trouble seeing as how you are running a 4 year old release.  If possible, and it were my machine, I would do a clean install of 20.04.

---

### Post by UserJB on 2020-05-29
CTRL+ALT+F1 did not work for me (probably because the machine did not fully boot properly).  I instead booted into runlevel 3 and ran the original Nvidia install script with the --uninstall command-line option.  That worked for me.  Thanks for you help.

---

### Post by deadflowr on 2020-05-29
> **UserJB said:**
> CTRL+ALT+F1 did not work.

Then try F2 through F6.

Edit:
Seems you edited your post as I was typing.

---

### Post by monkeybrain20122 on 2020-05-29
Which Nvidia driver are you trying to install? If the driver is in the repo or the graphic driver ppa then you can save the trouble of installing from .run file. For 16.04 the newest driver is 430 in the graphic driver ppa (but 32 bit support is apparently missing) My work machine is still on 16.04 since too much trouble to reinstall 20.04 and retest everything that I already know working, it has driver 418.56 from the graphic driver ppa.

---

### Post by oldfred on 2020-05-29
If you installed the .run version you will have issues with every kernel update.
You in effect have to reinstall the driver into the kernel every time. 
The Ubuntu versions automatically handle that.

But do not install a new/different driver without uninstalling all old drivers. Otherwise you get conflicts and bigger issues.
A new driver does not uninstall an older driver.

We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work.
And if you have a very new nVidia card, and need a driver newer than in default repository, there is a ppa with all the new versions pre-configured.

Uninstall the .run nVidia driver.
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by UserJB on 2020-05-29
I was trying to install the 440 driver.  I have since uninstalled it.

---

### Post by UserJB on 2020-05-29
Okay, don't install the Nvidia driver from the Nvidia .run file.  Lesson learned.  If I look at the output of 'apt list' the lastest Nvidia driver seems to be 384.  I will look into PPAs and the graphic driver PPA.

---

### Post by Bashing-om on 2020-05-29
UserJB; Hello -

Just a word of warning:
Make sure that the driver selected is compatible with the graphic's card:
 [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
is my goto to see what the latest -supported - driver is.
compare to:
```

sudo ubuntu-drivers devices

```
Then to have the system install the version it thinks best - from what it has to choose from:
```

sudo ubuntu-drivers autoinstall

```

easy peasy
[INDENT][INDENT]no fuss, no muss[/INDENT][/INDENT]

---

