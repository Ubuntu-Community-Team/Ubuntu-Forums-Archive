---
title: "Nvidia graphics help"
date: 2008-04-22
forum: General Help
---

### Post by techuser on 2008-04-22
I am very confused over how ubuntu handles the video side. I have activated the nvidia restricted drivers and have tried to follow instructions to get compiz working.
After using ALT+F2 and typing : metacity --replace
then opening a terminal and typing: compiz replace 
evrything looks and runs great .
I then used Preferences>Apperance>Visual Effects to make the settings for desktop effect active.
When I try to use the NvidiaX-Server-Settings A message comes up stating:
"You do not apper to be using the Nvidia X Driver.
Please edit your X Configuration file (just run "nvidia-
xconfig as root) and start X server.
If I run nvidia-xconfig I get :
"Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered"

Any suggestions on where I am at ? What I should do? What these things are trying to tel me?

---

### Post by sdennie on 2008-04-22
It looks like you are using Xgl instead of nvidia for your Xserver.  At some point during setting up did you type something like "sudo apt-get install xserver-xgl"?  You could uninstall xserver-xgl and then re-run nvidia-xconfig and see if that helps.  Something like this should work:

```

sudo apt-get remove xserver-xgl
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig

```

After that, if you log off and then press Ctrl-Alt-Backspace (Backspace, not Delete), when you log back in you should be able to use nvidia-settings

---

### Post by Yudraciell on 2008-04-22
or if u really want it simple

look up ENVY in add/remove and use that program it will automatically do it for you

---

### Post by techuser on 2008-04-22
vor
Thanks for your assistance the advice you posted worked perfectly.
Nice when a plan comes together.
Thanks again

---

### Post by sdennie on 2008-04-22
Glad to have helped

---

