---
title: "Crash After nVidia Driver Installation"
date: 2007-04-07
forum: General Help
---

### Post by Petester on 2007-04-07
Well, i finished installing nVidia Graphics drivers. The first reboot after the installation is fine, but then the second one, shows error message that X Server failed to start. Now I am in LiveCD hoping to get an answer.. Can someone please help? Thanks

---

### Post by Valstorm2323 on 2007-04-07
Write down the error message.

Did it say that your nvidia versions are different from each other?

Mine just crashed due to different modules and drivers of nvidia.

---

### Post by Petester on 2007-04-07
I remembered that it said
"It might because X files are not set correctly"
or similar

---

### Post by Maestro23 on 2007-04-07
Here's a guide that might help you guys: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Also, have you tried the Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Good luck.

---

### Post by Petester on 2007-04-08
Alright I clicked 'diagonise the problem' and i wrote down the whole thing.. can someone help me to fix it without reinstalling? I can go to terminal

Error API Mismatch: The NVIDIA Kernel module has the version 1.0-7184 but this X module has the version 1.0-9755. Please make sure that the kernel and all NVIDIA DRiver components have the same version.
(EE)NVIDIA(0) - Failed to initialize the NVIDIA Kernel module! Please ensure that there is a supported NVIDIA GPU in thie system and that the NVIDIA Device files have been created properly.

I ran sudo sh nvidia.run to install and id ont think there was a problem. I have 7600GT so i dont think i ahve a problem with that too...

---

### Post by Valstorm2323 on 2007-04-08
Okay when you get to terminal type this in>

wget [http://www.albertomilone.com/nvidia_scripts/Then](http://www.albertomilone.com/nvidia_scripts/Then) the name of the file you want to download.

I had to do that in order to get the file through the internet. If this isn't a problem for you then go next step.

I suggest simply installing that script and runnint UNSINSTALL driver because when I tried to install mine it still didn't work.

Now I have no nvidia kernel available or it can't find it, I'm guessing it's gone so I'll have to find it or reinstall it. You look like you have the exact same problem so that's my advice.

---

### Post by Petester on 2007-04-08
Well.. actually dont mind about it.. I just reinstalled before I saw your post... After I got the updates done im gonna install Envy...

Thanks anyway ^^

---

