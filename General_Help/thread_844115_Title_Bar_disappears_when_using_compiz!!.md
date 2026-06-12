---
title: "Title Bar disappears when using compiz!!"
date: 2008-06-29
forum: General Help
---

### Post by spraveenitpro on 2008-06-29
Hi 

Recently I installed compiz and enabled "The Cube" effect, ever since then the 'Title Bar' for most windows disappear. Only after setting the Visual effects to "None" , The "Title Bar" Reappears. Pls let me know how to fix this.

Praveen.

:popcorn:

---

### Post by Forlong on 2008-06-29
Post the ouput of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

As well as this command in a terminal:
```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by spraveenitpro on 2008-06-29
Thank you , Here it is :

**[COLOR="Red"]compiz-check :[/COLOR]**

```
praveen@praveen:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you won't be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y
praveen@praveen:~$ 
```

[B][COLOR="Red"]
The Output of dpkg -l | grep compiz  :[/COLOR][/B]

```

root@praveen:~# dpkg -l | grep compiz
ii  compiz                                     1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenCompositing for Com
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - GNOME window dec
ii  compiz-plugins                             1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - plugins
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Project
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                                     Compiz configuration settings manager
ii  desktop-effects-kde                        0.4                                                compiz setup tool for KDE
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                        0.7.4-0ubuntu1                                     Compiz configuration system bindings

```

Please let me know what can be done. thx alot!!

Praveen.
India.

---

### Post by Forlong on 2008-06-29
Please run ```
compiz
``` in a terminal.

Afterwards (if the title bars are missing) open another one and run ```
gtk-window-decorator --replace
```
Does it help?

Post both outputs here.

---

### Post by spraveenitpro on 2008-06-29
Hi 

Here it is :

[COLOR="Red"]**compiz :**[/COLOR]

```

praveen@praveen:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

The title bar disappeared and i typed 'gtk-window-decorator --replace' in the terminal, Nothing happend. This is the output :

```
praveen@praveen:~$ gtk-window-decorator  --replace

praveen@praveen:~$ sudo -s
[sudo] password for praveen: 
root@praveen:~# gtk-window-decorator --replace
```

Pls let me know what can be done.

Praveen

---

### Post by Forlong on 2008-06-29
Why are you running things as root that don't require it?
_Never_ do that!
You are messing with the permissions of your own home directory.

Run those commands (in a usual terminal!) to fix that:
```
sudo chown -R $USER:$USER $HOME
```
```
chmod -R u+rwX $HOME
```

---

### Post by spraveenitpro on 2008-06-29
Hi Forlong 

Thx , this is the output of the commands :
```

praveen@praveen:~$ sudo chown -R $USER:$USER $HOME
chown: cannot access '/home/praveen/.gvfs': Permission denied
praveen@praveen:~$ chmod -R u+rwX $HOME
praveen@praveen:~$
```

Praveen

---

### Post by Forlong on 2008-06-29
What's the output of this:
```
gconftool-2 -g /apps/compiz/general/allscreens/options/active_plugins
```

---

### Post by spraveenitpro on 2008-06-29
This is it :

```
praveen@praveen:~$ gconftool-2 -g /apps/compiz/general/allscreens/options/active_plugins

[core,dbus,place,move,resize,decoration,png,svg,imgjpeg,text,neg,video,wall,snap,animation,scale,expo,switcher,regex,resizeinfo,workarounds,ezoom,vpswitch,extrawm,fade,scaleaddon,scalefilter,session,shift,wobbly]
praveen@praveen:~$ 
```

Praveen

---

### Post by Forlong on 2008-06-29
Well, the decoration plugin is loaded.

Try running
```
compiz
```
and afterwards ```
gtk-window-decorate --replace
```
again. If it still doesn't work I guess it has to be something to do with your hardware and I'm sorry, I don't have any experience with intel chips.

---

### Post by spraveenitpro on 2008-06-29
Hi

when I type "compiz" , the "Title menu" disappears and get :

```
praveen@praveen:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

On typing gtk-window-decorate --replace :

```
praveen@praveen:~$ gtk-window-decorate  --replace
bash: gtk-window-decorate: command not found
praveen@praveen:~$
```

Praveen.

---

### Post by Forlong on 2008-06-29
Sorry, this is the correct command
```
gtk-window-decorator --replace
```

---

### Post by spraveenitpro on 2008-06-29
Compiz :

```
praveen@praveen:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

**gtk-window-decorator**

```

praveen@praveen:~$ gtk-window-decorator  --replace
```

Got no output for above command.

---

### Post by VitaminBB on 2008-11-26
Having the same problem and cant seem to solve it ...

I have added lines to xconf, ive added emerald to startup on login, nothing helps ...

---

### Post by Lnewb on 2009-02-09
> **spraveenitpro said:**
> Hi 

Recently I installed compiz and enabled "The Cube" effect, ever since then the 'Title Bar' for most windows disappear. Only after setting the Visual effects to "None" , The "Title Bar" Reappears. Pls let me know how to fix this.

Praveen.

:popcorn:

I don't know if you've solved this,but I have spent the last few days trying to solve the same problem.
Beeing a linux newbie I've tried every code I found on different forum sites and adding lines to xconfig and so on.
But the simple solution in my case was to open compiz fusion icon,right click the icon,choose "select windows decorator" and check off the GTK coice (I only have GTK),and that was all it took :)
Hope this can help you or others.

---

