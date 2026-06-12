---
title: "Sorting out my Screen Resolution"
date: 2007-12-04
forum: General Help
---

### Post by gunner_uk2000 on 2007-12-04
When I goto System -> Preference -> Screen resoultion

it doesn't allow me to chose 1440x900 for my LCD screen

So I'm now trying to get some updated drivers from NVIDIA, so I have the pkg2.run file i got from NVIDIA. I tried to run it and it wanted me to shut down X windows.

so I put:

sudo init 1

into the terminal and ran the installer, which now complained about needing to be in init 3. According to the readme files init 3 for most systems will shut down X windows and leave networking services running.

How ever on Unbuntu when I put it into init 3 X Windows is still running.

So How would I go about getting a decent resolution for my moinitor and getting the drivers for my graphics cards installed?

Thanks for any help.

---

### Post by -grubby on 2007-12-04
```
sudo apt-get install nvidia-glx-new
``` and then open a terminal 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```       and choose "nvidia". after that's done do ctrl-alt-backspace and you're set. If something isn't working right you can always:

```
gksudo nvidia-settings
```

---

### Post by gunner_uk2000 on 2007-12-04
> **nathangrubb said:**
> ```
sudo apt-get install nvidia-glx-new
``` and then open a terminal 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```       and choose "nvidia". after that's done do ctrl-alt-backspace and you're set. If something isn't working right you can always:

```
gksudo nvidia-settings
```
Ok,

I entered the two commands after the second one there was no option to 'chose Nvidia' and when I pressed  ctrl +alt +backspace.

I was sent back to the login screen when I login I get a garblled desktop, and when I try to change session the select session dialog garblles so I can't get the failsafe gfx up.

When using the failsafe terminal all it seems to do is respond to the exit commnad. ie ls does nothing just gives me another prompt.

Any ideas?

Thanks for any help.

---

### Post by pedro_orange on 2007-12-04
Check out Envy, it will download and install the most suitable nVidia driver for you.
You just sit there and have a cup of tea.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Make sure your VDU can handle your desired resolution & away u go.

You may wish to try "sudo dpkg-reconfigure -phigh xserver-xorg" to configure all ur video settings and so on.

---

### Post by gunner_uk2000 on 2007-12-04
sudo dpkg-reconfigure -phigh xserver-xorg

So will the above command get me back to default graphical settings so I can use my desktop if I enter it into the failsafe terminal?

Thanks.

---

