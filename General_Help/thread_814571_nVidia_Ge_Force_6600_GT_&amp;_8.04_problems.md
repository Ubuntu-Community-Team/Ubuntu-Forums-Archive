---
title: "nVidia Ge Force 6600 GT &amp; 8.04 problems"
date: 2008-05-31
forum: General Help
---

### Post by chaplanger on 2008-05-31
I recently upgraded to Ubuntu 8.04 -- 7.10 was working perfectly.  Now my graphics card is not recognized.  It is an nVidia GeForce 6600 GT card.  In my earlier versions of Ubuntu I was running the 'nv' driver -- but I cannot find this driver in 8.04.

Currently I am locked into a screen resolution of 640x480 at 61 Hz.  This card can be run at 1280x1024 as well as 1152x864, 1024x768 and 800x600.  How do I get my screen resolution back and get this card fully recognized.

Thanks for any assistance you can give.

---

### Post by Cresho on 2008-05-31
this is directly from my notes.  It varies from time to time so not as accurate at times but it does work for me.

********************************************************************************
Nvidia**************************************************************************
********************************************************************************
New and updated
setting up your ubuntu first of all:fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
1. sudo aptitude remove automake1.4
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. grub into recovery mode and hit root. cd into the directory where you downloaded the NVIDIA-Linux-x86-169.09-pkg1.run and sh NVIDIA-Linux-x86-169.09-pkg1.run in terminal. (this one is 32bit version)
4. ignore the question or say no to kernel download during instal and have nvidia xconfig update the x
5. if screen is not proper, continue and once booted, open synaptic package manager and remove nvidia kernel common. then repeat top process if to ensure all is installed again.
6. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
7. reboot and your good to go.

repeat this process if you update the ubuntu and reverts you back to the old vesa drivers.  other notes!  kernel source if asked can be accomodated by these in the bottom

sudo dpkg-reconfigure linux-restricted-modules-2.6.24-16-generic
sudo dpkg-reconfigure nvidia-glx-new


it is really easy...really!  Not sure how fancy you are with the terminal and other stuff.

---

### Post by chaplanger on 2008-05-31
> **Cresho said:**
> this is directly from my notes.  It varies from time to time so not as accurate at times but it does work for me.

********************************************************************************
Nvidia**************************************************************************
********************************************************************************
New and updated
setting up your ubuntu first of all:fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
1. sudo aptitude remove automake1.4
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. grub into recovery mode and hit root. cd into the directory where you downloaded the NVIDIA-Linux-x86-169.09-pkg1.run and sh NVIDIA-Linux-x86-169.09-pkg1.run in terminal. (this one is 32bit version)
4. ignore the question or say no to kernel download during instal and have nvidia xconfig update the x
5. if screen is not proper, continue and once booted, open synaptic package manager and remove nvidia kernel common. then repeat top process if to ensure all is installed again.
6. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
7. reboot and your good to go.

repeat this process if you update the ubuntu and reverts you back to the old vesa drivers.  other notes!  kernel source if asked can be accomodated by these in the bottom

sudo dpkg-reconfigure linux-restricted-modules-2.6.24-16-generic
sudo dpkg-reconfigure nvidia-glx-new


it is really easy...really!  Not sure how fancy you are with the terminal and other stuff.



OK -- I appreciate the help -- but will need your patience and indulgence.  I've been away from Ubuntu for nearly a year now -- so I'm a bit rusty.

After getting into: Administration->Software Sources.
I changed the server to "Main Server"
I believe I updated the resources 
All my third party areas were for previous releases . . . do I check these or leave them alone?

I didn't see anything resembling "add/remove programs" -- where is this?

Step 2: Are all three lines a single copy and paste command?  

How do I get into recovery mode?  (I've been away from Ubunto for a while now)

Step 6 -- I an unsure on as well. . . perhaps when I get to that point it will make more sense.

Thanks for your help here.

---

### Post by Cresho on 2008-05-31
for part one, just forget about the add-remove portion because it is not necessery.  to update the sources, "sudo apt-get update" in the terminal.  This will update your sources.

second part is single line paste command.

to get into recovery mode, just boot up and when you see the list of operating systems, choose Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) or what ever looks like recovery mode.  Then it will take you into or you choose the console portion.  you will then cd into your desktop and launch the nvidia drivers to install.

When Ever I have problems, i just re-use this method, especially after a kernel update because it defaults the nvidia card, and then everything is fine.

---

### Post by buntunub on 2008-05-31
Did you try from shell, 

```
$sudo dpkg-reconfigure xserver-xorg
```

??

You stated that on Gutsy you were running on the nv driver, so if your not interested in using the Nvidia blob, then just run the above command from shell or safe mode and that should fix your xorg issues using the open source driver.

---

### Post by Cresho on 2008-05-31
What I'm thinking is that he has a new kernel.  So it needs to be done from the bottom up as I posted.  Maybee reconfiguring xorg can work. :popcorn: curious.

---

### Post by buntunub on 2008-06-01
If your using the Nvidia blob and you did a manual kernel upgrade, then yes, you would have to use your method to reinstall the driver, but the open source xorg driver does not require this.

---

### Post by grss1982 on 2008-08-08
> **chaplanger said:**
> I recently upgraded to Ubuntu 8.04 -- 7.10 was working perfectly.  Now my graphics card is not recognized.  It is an nVidia GeForce 6600 GT card.  In my earlier versions of Ubuntu I was running the 'nv' driver -- but I cannot find this driver in 8.04.

Currently I am locked into a screen resolution of 640x480 at 61 Hz.  This card can be run at 1280x1024 as well as 1152x864, 1024x768 and 800x600.  How do I get my screen resolution back and get this card fully recognized.

Thanks for any assistance you can give.

Just curious did you try Envy?

LINK: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I used the CLI method of installing and it has worked for me on the following hardware:

Geforce MX-4000 (AGP)

Geforce 7300GT (PCIE)

Nvidia 7050 (Built-in VGA)

Hope that helps. :)

---

