---
title: "Need HELP! X Server Failed To Load!"
date: 2006-07-21
forum: General Help
---

### Post by kane_666 on 2006-07-21
Heres whats happening. Everything starts up fine until i get to whats supposed to be the login screen. What i get instead is an error saying that 

"X Server failed to load (GUI) its likely its not configured correctly. View server output to diagnose problem?"

then after pressing 'ok' on the errors, i get to the command line login. so after logining in, i viewed the config file and nothing seemed to be out of place so i tried re-building it using the command:
sudo dpkg-reconfigure -phigh xserver.xorg

then when i tried restarting gdm, i get the same error. so then i viewed the x server log file and heres the 2 errors i found:

1) GARTInit: Unable to open /dev/agpgart (no such file or direcroty)
2) AGP GART support not available: make sure kernal supports it...
3) Screen(S) found, but none have usable configuration file
4) Fatel server error: No screens found!

I dont know how to edit / view / rebuild the screens config file so i assume thats where i need your help. also i only have 1 screen and i haven't edited any of those system files to cause any errors.. :S so any ideas?

thanks

---

### Post by Malac on 2006-07-21
Try: ```
sudo dpkg-reconfigure xserver-xorg
``` this should reconfigure the whole xserver system.
The -phigh option doesn't always catch everything display related.

Hope this helps.

---

### Post by kane_666 on 2006-07-21
thanks for the help but i have a feeling that i did more bad then good.. i didn't quite no what to put for some things so i just hit enter :S 

but im still getting the same errors, no screens found etc..

---

### Post by Malac on 2006-07-21
One of the options is "Do you want to Auto Detect Screen" the default is No so if you hit Enter it wouldn't. Try changing it to Yes and see if it finds your screen.

Hope this helps.

---

### Post by kane_666 on 2006-07-21
well i tried reconfiguring it again, and no luck. same errors.

any help? im stuck without a gui and its starting to annoy me :P

thanks

---

### Post by kane_666 on 2006-07-21
/bump

come on guys/girls :P
i need to get my gdm back :)

---

### Post by hellocharlie on 2006-07-21
I'm having similar difficulties and as Linux initiate, I'm pretty lost.

What is your system?

My graphics card is an ATI X600SE and is detected properly by xorg as is my monitor, a Dell 1907FP. Another detail to this is that during install, I had to switch from my typical DVI setup to VGA for the installer to display.

Would this be related to xorg failing to start?

Any advice is appreciated. Thanks.

---

### Post by kane_666 on 2006-07-21
well when i ran the xserver reconfigure tool, it detected my onboard graphics card (intel 810 or something like that) but i had to specify how much memory it could use (i said 8mb because thats what it was on windows) and it detected my monitor, but it still doesn't start the x server, i get the same errors that i mentioned in my first post.

---

### Post by kane_666 on 2006-07-21
bump

---

### Post by 3rdalbum on 2006-07-21
Both posters: Do the sudo dpkg-reconfigure xserver-xorg again.

When it asks you if you want to auto-detect your video card, say No. When it asks you which driver you want to use, select "vesa". When it asks how much video memory it has, just leave that blank (X-org should detect the memory anyway).

When asked if you want to auto-detect the monitor, again say No. Use the "Simple" setting and then select the size of your monitor.

Any other settings that you don't understand, just leave at their defaults.

When the process is finished, type "startx" at the prompt and press Return, and hopefully everything should be okay.

---

