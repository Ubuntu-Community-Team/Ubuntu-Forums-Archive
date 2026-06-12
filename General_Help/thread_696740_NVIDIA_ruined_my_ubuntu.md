---
title: "NVIDIA ruined my ubuntu"
date: 2008-02-14
forum: General Help
---

### Post by StOoZ on 2008-02-14
I need help, I cant install my 6600GT drivers.
I tried to install the 169 drivers that are on the nvidia site,now ubuntu runs on low graphics mode,which now he cant detect the proper drivers,what should i do?

I installed them (the 169 drivers) by closing the x server,pressing ctrl+alt+f1 and then making that command:
sudo sh "the driver file name here"
and installed it..now all is wrong..what to do?

10x

---

### Post by Therion on 2008-02-14
Try running [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by StOoZ on 2008-02-14
well it requires to have the ubuntu disk,I dont have it...
any other way?

and by the way,why did it happen??
thanks for the help

---

### Post by chalewa on 2008-02-14
take the ubuntu cd out of your repository lists, and try to install envy again, that will be your best bet.

---

### Post by StOoZ on 2008-02-14
well im dowloading the disk from this site now.. will burn it and try again.

Why did it happen? the nvidia drivers are bad?

---

### Post by PmDematagoda on 2008-02-14
Boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as "nvidia" and any other options you may want, after that is done reboot Ubuntu using:-
```
sudo reboot
```

---

### Post by chalewa on 2008-02-14
no i mean graphix drivers are just strange...

there are a billion different graphic drivers out there. for the future tho, it is probably a good idea to take the ubuntu cd out of your repository list (or at least comment it out) so that you aren't constantly having to load the cd.

---

### Post by PmDematagoda on 2008-02-14
> **StOoZ said:**
> well im dowloading the disk from this site now.. will burn it and try again.

Why did it happen? the nvidia drivers are bad?

No, it might either be because of the X-Server is improperly configured or due to conflicting packages or modules.

---

### Post by StOoZ on 2008-02-14
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as "nvidia" and any other options you may want, after that is done reboot Ubuntu using:-
```
sudo reboot
```

well that doesnt work, I select my card and then..press exit (After the gfx section is over)  all over the mouse,keyboard etc configuration until it exits...reboot..and nothing

---

### Post by PmDematagoda on 2008-02-14
Ok, boot Ubuntu in Recovery Mode again and try this:-

1) Open a modules file using:-
```
sudo nano /etc/default/linux-restricted-modules-common 
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"

```

3) Save the file and reboot Ubuntu again to see if the problem is solved.

---

### Post by StOoZ on 2008-02-14
stupid me, I think I know why it didnt work....
I wasnt in recovery mode....
im now downloaing the ubuntu disk,in case I'll have to use envy

---

### Post by PmDematagoda on 2008-02-14
> **StOoZ said:**
> stupid me, I think I know why it didnt work....
I wasnt in recovery mode....
im now downloaing the ubuntu disk,in case I'll have to use envy

It does not really matter if you were in Recovery Mode or not.

---

### Post by StOoZ on 2008-02-14
> **PmDematagoda said:**
> It does not really matter if you were in Recovery Mode or not.


grrr..... ok so i'll wait for envy to be downloaddd.
and I'll never....never!!!!!!!!!!!!!!!!!!!!!!!!!!! try to update the nvidia driver again.
:(

---

### Post by PmDematagoda on 2008-02-14
> **StOoZ said:**
> grrr..... ok so i'll wait for envy to be downloaddd.
and I'll never....never!!!!!!!!!!!!!!!!!!!!!!!!!!! try to update the nvidia driver again.
:(

Actually it is good to update the Nvidia driver when it is required in order to fix bugs and get improvements, but to do that you need to know the steps.

Just refer the Nvidia Manual [here]("https://help.ubuntu.com/community/NvidiaManual") and you should understand more about how to install the Nvidia driver on Ubuntu manually.

---

### Post by danwood76 on 2008-02-14
There is an nvidia auto Xorg configure which will sort you out I would expect.

```

sudo nvidia-xconfig

```

Installed a 5600 on a work computer today and installed the latest drivers, ran this command and rebooted and it was configured correctly.

---

### Post by EXCiD3 on 2008-02-14
Go to System->Administration->Software Sources and make sure the Ubuntu CD is unchecked on the list. Try installing Envy again. This will download the required packages instead of having you install them from the CD. Save you some time ;) You should use the officially supported ways of installing the graphics driver anyways. Envy is **NOT** officially supported and will require you to reinstall the graphics driver every time the kernel is updated. Install using the Restriced Drivers Manager if you can.

---

### Post by StOoZ on 2008-02-14
well folks, thanks for the help.
envy solved my problem... its amazing,not only that,it fixed my previous issues with the resolutions & refresh rates.

im only two weeks with ubuntu,and linux (new to linux) , and I hope that one day,I could do what envy did by myself trough the console....

---

### Post by Therion on 2008-02-14
> **EXCiD3 said:**
> 
... Envy is **NOT** officially supported and will require you to reinstall the graphics driver every time the kernel is updated. 
It may not be officially supported, but it's hard to argue with what works.  Envy has pulled my butt out of the flames numerous times where the RDM has left me scratching my head trying to get [*insert just about any GPU-related video setting here*] squared away.  Sometimes I get tired of battling the same config files over and over and getting nowhere.  Supported or not, Envy just works for me.

> **StOoZ said:**
> 
envy solved my problem... its amazing, not only that, it fixed my previous issues with the resolutions & refresh rates.
Yup.

---

