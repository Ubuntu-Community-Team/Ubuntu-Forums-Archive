---
title: "Ubuntu 13.10 - Installing Latest NVIDIA Drivers"
date: 2014-03-03
forum: General Help
---

### Post by MrBean355 on 2014-03-03
Hello guys,

I am trying to install the latest NVIDIA drivers on Ubuntu 13.10 (I have a GeForce GT 520M card). I have searched a lot but haven't found a working solution yet.

_**My ultimate goal is to have OpenGL 4.2 support**_, because it is required for my university graphics course.

I have tried downloading the 331.49 driver (.run format) from the NVIDIA site and installing it, but I get a black screen when trying to log in.
I tried deleting "*xorg.conf*" because there wasn't one initially. That still didn't work.
Then I tried running **nvidia-xconfig**, which didn't work either.

What is the best way to install the NVIDIA driver? Perhaps through the console?
Any help with this issue will be greatly appreciated. I am starting to get desperate as I have been trying to get it working for weeks.

Thanks,

***Mr_Bean***

---

### Post by monkeybrain20122 on 2014-03-03
It is a bad idea to try to install from the .run file from Nvidia site.
Get rid of every remnant from your blotched install and then isntall it from  
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by MrBean355 on 2014-03-03
Thanks for the reply.

I will give that a try.
Would I just run **sudo apt-get install nvidia-current**? Or something more?

---

### Post by monkeybrain20122 on 2014-03-03
You have to first add the xorg-edger repository to your sources list, then update the sources, upgrade the packages and then install. The package is not called "nvidia-current", but                  nvidia-graphics-drivers-331               

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-graphics-drivers-331 ppa-purge
```

All this is easy if you have synpatic
```
sudo apt-get install synpatic

```
Then open Settings> Repositories > Other Software
and add
> ppa:mad:org-edgers/ppa
close the drop down
Reload synaptic 
Then you can search for nvidia in quick search and see what  packages are available and you don't have to know their exact names like with the commands.

The smiley is actually a colon, somehow it shows up as a smiley.

**Warnings:** 
1. ppa-purge is installed in case anything goes wrong you can reverse the change.
2.There was a packaging bug in that when you install nvidia-driver from xorg-edgers it somehow install bumblebee and primus, these are for optimus laptops. If you don't have optimus you will boot into a blackscreen because bumblebee blacklists the nvidia driver, assuming that there is an intel card for fallback. I don't know if that has been fixed or not. So after you install, make sure that bumblebee is not installed and if it is remove it before you run nvidia-xconfig and reboot. synaptic is very handy for this
3. If everything works, disable the xorg-edgers ppa so that you don't get frequent updates that may be unstable (easy to do in synaptic, go to Settings > Repositories > Other Software and uncheck the box)

---

### Post by Yellow Pasque on 2014-03-03
In all likelihood, this is actually an Optimus setup. See output of lspci:
```
lspci | grep -i graph
```

The best thing to do in that case:
1. Run the Nvidia .run file again with --uninstall option
2. Get rid of xorg-edgers (at least for the moment). The 319.xx drivers in the Saucy repo will probably work just fine.
3. [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
4. Check output of:
```
optirun glxinfo
```

---

### Post by pbrane on 2014-03-03
My bad, here is one possible solution: [http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271]("http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271")

---

### Post by Yellow Pasque on 2014-03-03
^That's hardly ideal and it's gross violation of Debian policy, even on systems with only Nvidia graphics. I'm not saying it doesn't work, but please don't advise others to do it. If this is an Optimus laptop (all laptops with Nvidia 5xxM and later are Optimus configurations IIRC), you just broke the user's system...

Sorry if that's a bit harsh, but be more careful in the future.

---

