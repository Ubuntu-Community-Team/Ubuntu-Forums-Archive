---
title: "Nvidia Drivers Not Working"
date: 2014-05-18
forum: General Help
---

### Post by imzack2 on 2014-05-18
I am real new to the Ubuntu world and I just tried to install the Nvidia drivers for my laptop.

I did a reboot and I saw the following screen...

[ATTACH=CONFIG]253275[/ATTACH]

I got this to go away by deleting/moving a file, as directed on anther forum.

Now I am still left with the computer having a messed up/ huge resolution display.

[ATTACH=CONFIG]253276[/ATTACH]

And after I log in, I cannot do anything, nothing works.

[ATTACH=CONFIG]253277[/ATTACH]

I even have tried to right click to see if I could make a text file or something, but that doesn't work either...

Any suggestions?

Thanks,

Zack

---

### Post by fatriff on 2014-05-18
Where did you install the driver from? The additional drivers tab in software & updates?

Does your laptop have dual graphics?

---

### Post by imzack2 on 2014-05-18
I have a 870M Nvidia card, just for a laptop, so shouldn't be dual graphics.

I also installed it from command line in the terminal, "sudo apt-get install nvidia-current"

---

### Post by pqwoerituytrueiwoq on 2014-05-18
laptops are most known for dual graphics, it is callled nvidia optimus
run 
```
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-331-updates
sudo reboot
sudo nvidia-xconfig
sudo reboot
```

---

### Post by imzack2 on 2014-05-18
Everything was looking good until I ran "sudo nvidia-xconfig"
After I ran that, the screen resolution went back to what it looked like before (Huge)

I also got this when I ran that line...

[ATTACH=CONFIG]253278[/ATTACH]

---

### Post by imzack2 on 2014-05-18
I have re-ran the 

sudo apt-get purge nvidia-*
sudo apt-get install nvidia-331-updates
sudo reboot

and everything looks good, the resolution is fine, I can actually do stuff on the computer in the graphics interface... but...

but when I run the code,

sudo nvidia-xconfig
sudo reboot

then everything goes back to the way it was (huge and cant do anything)

---

### Post by imzack2 on 2014-05-18
bump

---

### Post by pqwoerituytrueiwoq on 2014-05-18
if those last 2 commands messed it up run [FONT=courier new]sudo rm /etc/X11/xorg.conf[/FONT] then reboot

---

### Post by imzack2 on 2014-05-18
should i remove that file, and then re-run those two commands?
Or just remove that file?

---

### Post by pqwoerituytrueiwoq on 2014-05-18
just deleteing the file and restarting lightdm should do it

---

### Post by imzack2 on 2014-05-18
Awesome!
Thank you soooo much.
You are my hero!

---

### Post by QIII on 2014-05-18
Hello, imzack2!

Please do not paste large images in your post.  Some users have limited bandwidth or monthly bandwidth restrictions and such large images will be slow to download or may cause them to use up their quotas.

Instead of pasting the images, please use the attachment functionality by clicking the "paper clip" button above the text entry area.

Thanks,


QIII

---

