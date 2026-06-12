---
title: "Switch back to Edgy"
date: 2007-04-23
forum: General Help
---

### Post by Arun985 on 2007-04-23
Hey, is it at all possible to downgrade from Feisty to Edgy? If it is, how would I go about doing this? I ask because I have been working in Feisty since its release, and haven't got answers to a lot of my problems. If I can get some answers, i'll stick with Feisty. Here are my problems (in no particular order):

1.) Audio doesn't work on the Internet, but it does otherwise.
2.) my nVidia card doesn't work in Feisty, but it did in Edgy.
3.) Beryl suddenly stopped working.
4.)Can't write to USB flash drive.

I would appreciate any help to any of my above mention problems.

---

### Post by chrisccoulson on 2007-04-23
1) What browser are you using? What sort of embedded objects does the audio not work for?

2) Which NVIDIA card are you using?

3) Probably doesn't work because of 2.

4) Do you get any messages when you try to write to your flash drive?

---

### Post by Arun985 on 2007-04-23
1.) I'm using Firefox, and my internet audio mysteriously fixed itself about a 1/2 hr ago. The thing is, my internet audio was working yesterday around this time too. I watched a few vids on youtube, and everything was fine. But sometime after 7 pm my audio just stopped working. Is there some type of timer or something that turns of audio at specific times?

2.) My card is a nVidia GeForce 6200, and I still haven't solved the problem of running Feisty on it. I've tried installing nvidia-glx-new, but when i reboot, x-server doesn't load. I get the blue screen

3.) you're prol'ly rite

4.) It seems like I only have read access to my flash drive. If I delete something, the icon will disappear, but I don't get back any more space, so obviously the file is still there. When I go into its properties and try to change the "Read-Only" access to "Read/Write" access, I get an error saying I don't have permission to do that, and I'm the only registered user on my computer. 

I hope this helps, so you or someone can help me. Thnx

---

### Post by chrisccoulson on 2007-04-23
What error are you presented with when the X Server doesn't start? Can you post the contents of /etc/X11/xorg.conf and /var/log/Xorg.0.log? Did you install the NVIDIA drivers via Synaptic, or did you let the Restricted Drivers manager handle it? Have you tried the nvidia-glx package as opposed to nvidia-glx-new? The restricted drivers manager automatically installed nvidia-glx for my 7900GT and it works fine.

For the USB drive, are you deleting files in Nautilus? If so, then the files are being moved to trash, which is stored in a hidden folder on your USB drive (hence why the space isn't freed up). Have you tried emptying the trash? You can do this the usual way or unhide the files on your USB stick and navigate to the hidden '.Trash-<user_name>' folder to remove the files from the device.

---

### Post by Arun985 on 2007-04-23
Hi, when I install the nVidia driver and reboot my machine, Ubuntu gets stuck at the "Loading Hardware Device" stage. So, to get things running again I reconfigure X-Server and reboot again and switch to my onboard graphics. I've attached the files you wanted to look at. You'll notice that my nVidia card isn't listed in my xorg.conf. This is because my x-server has been reconfigured since I last installed the driver. When I did install it, I used Synaptic, because it wasn't listed in my restricted drivers manager.

And about my flash drive. I'll try what you said the next time I use it. Thanks for the advice.

---

### Post by chrisccoulson on 2007-04-23
What errors do you get though when you enable the NVIDIA driver? I'm surprised that the restricted drivers manager didn't pick up the 6200.

I think you enable the NVIDIA driver by typing sudo nvidia-xconfig in to a terminal. Then can you post the contents of /etc/X11/xorg.conf and /var/log/Xorg.0.log with the error?

---

### Post by Arun985 on 2007-04-23
No errors, really. Everything seems fine until I reboot, and then my system hangs on the loading screen with the Ubuntu logo and loading bar. I just enabled the nvidia driver the way you said and attached my new xorg files.

---

