---
title: "Deleted My nVidia drivers?"
date: 2007-03-21
forum: General Help
---

### Post by Sontra on 2007-03-21
Heyo.

I was going to come here asking for help upgrading to edgy, but that problem seems to be moot now. =)

I'm a definite new user to Ubuntu, so I'm still learning what I can do and what I can't. Or should and shouldn't. Anyway.

I was messing around (I'm learning that just gets me in trouble with Ubuntu. heh) and I was trying to update my nVidia drivers (because I still haven't gotten 3d acceleration working properly). After a reboot (that I had to manually reboot in the end because it froze), I got a message (and a lovely blue screen).

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly."

"The X server is now disabled. Restart GDM when it is configured correctly."

And then I'm taken to a .. (bash?) terminal where I can login.

I'm not quite sure exactly how to fix my mistake using only terminal. (Damn my dependence on graphical interfaces. I really should learn terminal commands to a point where I can actually use them).

Thanks!

---

### Post by kpkeerthi on 2007-03-21
Login to terminal and then type sudo nano /etc/X11/xorg.conf 
Search for the string "nvidia" in Device section and change it to nv.
Save & Exit and Reboot.

That should atleast get you to a graphical environment.
And then you may follow [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) to reinstall it properly.

---

### Post by Sontra on 2007-03-22
Well, I can successfully get to /ect/X11/xorg.conf, but I run into a problem where the document is completely empty.

I know that this is because I don't have access. So the document exists, I just don't have the permissions to read it. But I don't know how to change that. I had some access problems on this box with my initial user account and, after a lot of trying, I couldn't return permissions to it. I was able to create a new admin account and then delete the other.

But, from the looks of it, maybe I didn't do that properly?

---

### Post by tommcd on 2007-03-22
Boot to recovery mode (from the grub menu when you first boot up, if you don't see the grub menu when you boot then hit Esc key when you start up the PC). 
Then type <sudo dpkg-reconfigure xserver-xorg>. You can answer the default options for all questions if you don't know the answers. At the end of it select "medium" or "advanced" to set up your monitor. Medium will ask you the resolutions for your monitor, which you select with the space bar. Advanced will ask for the horizontal and vertical refresh rates as well, so use that if you know them.
When finished reboot or type <sudo /etc/init.d/gdm start> to boot to the GUI.
You will then have to reinstall the nvidia driver, but backup xorg.conf first:
<sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak>. This will allow you to replace your xorg.conf with a working one if it gets screwed up again by doing <sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf>.
Hope this helps.

---

### Post by fragos on 2007-03-22
When you run sudo dpkg-reconfigure xserver-xorg it will set your parameters but also set the driver to nv requireing you to edit xorg.conf.  I assume you got your self into trouble by not instaling the nvidia-glx package with Synaptic.  Frequently not getting into X is occurs after an improper install of an nvidia driver.  Synaptic and the Ubuntu repositories are the first place and safest to go foe installs.

---

### Post by Sontra on 2007-03-22
Alrighty, I'm gunna run off to try 'er out.

Now I know you're saying the repositories are the best place to go for the drivers, but it doesn't set up 3D Rendering by default (unless I'm mistaken). So how else am I supposed to get 3D rendering setup to play with beryl and such, without installing the nVidia drivers myself?

Cheers!

---

### Post by Sontra on 2007-03-23
Well darn.

I went off and attempted to reconfigure the file. I even got all the way through, but upon reboot I got the same error message. Unpleasant, to say the least. Any other ideas?

Perhaps it would be easier (although I would learn less tricks) for me to attempt a format instead? (Which raises a question of it's own. If I was to format, would I  be able to leave my /home partition alone, keep the files, and just change the OS partition? If that sentence makes any sense at all)

---

### Post by tommcd on 2007-03-23
If you have a seperate /home partition you can just reinstall ubuntu to /root and select "do not format" for the home partition and your files in /home will stay intact. 
I don't know why you can't get a GUI after reconfiguring xorg. Try it again and select defaults for all. If the don't work, try editing xorg.conf (sudo nano -w /etc/X11/xorg.conf) and make sure the driver is set to "nv". If you can't boot with that then change the driver to "vesa".

---

### Post by Sontra on 2007-03-23
I just ran through the process again (third time trying "nv"). Went strictly on defaults. No avail.

And I ran into the same problem as before, regarding editting the file manually in that it shows up blank as if I don't have permission to read the file itself.

So I tried again with "vesa". Same problem.

Any last thoughts before I just blow away my /root and start this game over? =D

---

### Post by tommcd on 2007-03-23
I'm running out of ideas. You should be able to edit the file with sudo, and you should be able to see the contents of it even if you can't edit it. Try <ls -al /etc/X11/xorg.conf> to see what the file permissions are. It should belong to root, and root should be able to read and write to it. This will be seen as -rw-r---r---  (I think that is what the permissions should be, I'm at work now so I can't check my own). 
If you do reinstall back up your xorg.conf before installing any drivers or editing the file. Also try the nvidia-glx from synaptic first. You should get 3D rendering with that.

---

### Post by Sontra on 2007-03-23
Thanks tommcd for all your attempts. I guess I just buggered the machine a bit more than is easy to repair.

Not a problem though, a quick format did the trick. And since I've got the time now, I'll just upgrade the box to Edgy. =)

Thanks again, muchos appreciated!

---

### Post by Sontra on 2007-03-24
Thanks for the attempts, tommcd. I guess I just borked things too much to be easily fixed. (Or I'm horrible at following instructions :D)

Reformatting went just fine. So did upgrading to Edgy. I guess I'm all set to go mess it up again. :) Thanks again!

---

