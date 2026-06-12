---
title: "compiz problem. most likely an easy fix."
date: 2008-04-29
forum: General Help
---

### Post by valke on 2008-04-29
Okay, so I built a new computer, originally for use as a server, but, alas, I couldn't get the darn disc to work. But, that's not the problem. I need now to enable Compiz, (for various confusing reasons) and I don't know how. 

Here is the output of if I run compiz in terminal.

```
andi@helix:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

---

### Post by pjones0404 on 2008-04-29
i am not sure of the exact way to fix this but there is some more information that we need to see what is the issue.

what type of graphics card do you have?
have you installed any drivers for it?

You may also search synaptics for xgl. some people have better luck when they install xserver-xgl.

---

### Post by crash91 on 2008-04-29
In the tags you mentioned nvidia, so try going into add/remove software and installing the nvidia drivers for your card. After this is done, check your /etc/X11/xorg.conf and scroll to the "Device" Section, under that, you should see nvidia listed, if it is vesa or something else, try changing that line and press ctrl+alt+backspace to restart the x server. 

As mentioned above check if you have xserver-xgl installed.  Also see the below thread which solved my problem on my intel card, maybe itll help.
[http://ubuntuforums.org/showthread.php?t=770230](http://ubuntuforums.org/showthread.php?t=770230)

---

### Post by Zorael on 2008-04-29
If Nvidia, the following terminal command should set up your /etc/X11/xorg.conf. Just make a backup of it first, to be safe.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals
```

---

### Post by valke on 2008-04-29
@pjones0404 I went and installed Xgl. Thank you for that suggestion.

@crash91 I wasn't too sure how to edit the xorg.conf file as I'd been trying to when working on fixing the resolution, but it works now. I had my nVidia drivers installed, but thanks :)

@Zorael This did the trick, so thank you very much! :)

---

### Post by Zorael on 2008-04-29
> **valke said:**
> @pjones0404 I went and installed Xgl.
You may want to get rid of it since it'll slow down Compiz something fierce (software rendering).

Further, if you run Compiz via a script, add the --loose-binding argument for a considerable performance boost.
```
$ compiz --replace --loose-binding &
```

---

### Post by valke on 2008-04-29
Okay, so, my output looks like this if I run Compiz:

```
andi@helix:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

If I uninstall Xgl, it won't run will it?

---

### Post by Zorael on 2008-04-29
Should run, if you have xorg.conf setup with Driver "nvidia" (which the nvidia-xconfig command should've done).

---

### Post by valke on 2008-04-29
So here is my output now. How do I start Compiz at start up, and how to I fix this so if I close the terminal it doesn't stop running Compiz?

```
micah@helix:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

---

### Post by Zorael on 2008-04-29
Right, here goes.

You want to make a script to launch compiz with the arguments you want, and then place this script in ~/.kde/Autostart to make it run upon login. (or whatever your autostart folder is set to under System Settings, About Me, Paths)

Example. The argument in [color="Green"]green[/color] is an Nvidia tweak, so other users reading this can omit it if they have other cards. The argument in [color="DeepSkyBlue"]blue[/color] is the KDE tweak so you won't get 16x16 desktops in Compiz when you want 4x1 for your cube.
```
#!/bin/bash

# kill adept_notifier since it bugs out anyway
killall adept_notifier

compiz --replace [COLOR="Green"]--loose-binding[/COLOR] [COLOR="DeepSkyBlue"]--ignore-desktop-hints[/COLOR] ccp $@ &

# sleep for three seconds, then restart adept_notifier
sleep 3
adept_notifier &
```
Save this as /usr/local/bin/compiz.start. You need superuser permissions to write to that folder. To open up that file with Kate as root, enter '**kdesu "kate /usr/local/bin/compiz.start"**' in a run box (Alt+F2), or in a terminal. Then make it executable.
```
$ sudo chmod +x /usr/local/bin/compiz.start
```
Lastly, make a symbolic link to that script in your autostart folder mentioned earlier.
```
$ ln -s /usr/local/bin/compiz.start ~/.kde/Autostart/compiz.start
```
All done. It will be started upon login, or if you at any time run **compiz.start**, via run box or terminal. This wrapper script will leave terminal control to you, but do note: if you run it in a terminal (like Konsole) and you close it with the X button, compiz will close, too. So make a habit of closing terminals by entering **exit** instead.


**Instead of saving this script in /usr/local/bin/ and with superuser rights, you can just save it in your own autostart folder.** However, then it'd only be accessible from your user, and you wouldn't be able to run it on demand without supplying the location (it's not in the PATH variable). So the above example would save it in a place where everyone could access it, and then make a symbolic link to it in your autostart folder.

As for losing terminal control in general, this is normal for applications and commands that aren't designed to run in the background. You can add an ampersand (&) after any command to make it a child process of the terminal you entered it in. However, as mentioned earlier, child processes are closed too if you close the terminal the wrong way (X button).

---

