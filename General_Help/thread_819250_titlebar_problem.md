---
title: "titlebar problem"
date: 2008-06-05
forum: General Help
---

### Post by birdySi on 2008-06-05
Hi,

when window is deselected, titlebar is little strange (enclosed Screenshot.png). Does anybody knows how to solve the problem.

Tnx

---

### Post by talktoari on 2008-06-05
I also have noticed this thing in my machine. However, I feel this is the way it is designed.

Somehow this look appears to be nice to me.

---

### Post by mrMango on 2008-06-05
That looks like it has something to do with your graphics card and desktop effects. Does the problem go away when you turn all desktop effects off? (System -> Preferences -> Appearence -> Visual Effects)

---

### Post by Muflon on 2008-06-05
What exactly is 'strange' about it?

---

### Post by mrMango on 2008-06-05
Shouldn't it look more like this?

---

### Post by birdySi on 2008-06-05
It is definitly something wrong with compiz. When I disable efect it seems everything ok. But when I start compiz again I get:

gorazd@gkkista:~$ compiz &
[1] 6763
gorazd@gkkista:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

**Update edit:** funny thing is that path /apps/compiz/plugins/scale/allscreens/options/initiate_edge doesn't exist....

---

### Post by mrMango on 2008-06-05
Interesting. Starting compiz on my end also gives me the GConf error, but not the compiz.real ABI errors. It looks almost if compiz is improperly installed.

```
sudo apt-get install --reinstall compiz
```

That work?

---

### Post by danwood76 on 2008-06-05
Its actually to do with the window decorator.
Are you using emerald or metacity?

---

### Post by birdySi on 2008-06-05
Nope. There is obviously some problem with nvidia driver... After command

sudo apt-get install --reinstall compiz 

I got folowing output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-17-generic linux-headers-2.6.24-17
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 reinstalled, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/34.6kB of archives.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 161475 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/libwfb.so' with
  different file `/usr/lib/nvidia/libwfb.so.xserver-xorg-core', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

Few minutes before that I downloaded NVIDIA-Linux-x86-173.14.05-pkg1.run from nvidia and installed. Before that compiz wouldn't run.

---

### Post by mrMango on 2008-06-05
Ah. Synaptic can install nvidia drivers for you; you shouldn't need to get them from nvidia. However, we can force dpkg to remove nvidia-glx:

```
sudo dpkg --remove --force-overwrite --force-depends nvidia-glx
```

I would then reinstall compiz and install nvidia-glx-new.

---

### Post by birdySi on 2008-06-05
> **danwood76 said:**
> Its actually to do with the window decorator.
Are you using emerald or metacity?

I'm using metacity. Emerald is not installed

---

### Post by birdySi on 2008-06-05
> **mrMango said:**
> Ah. Synaptic can install nvidia drivers for you; you shouldn't need to get them from nvidia. However, we can force dpkg to remove nvidia-glx:

```
sudo dpkg --remove --force-overwrite --force-depends nvidia-glx
```

I would then reinstall compiz and install nvidia-glx-new.

Uuups, when I'm trying to remove nvidia-glx I've got error:

(Reading database ... 161475 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/libwfb.so' with
  different file `/usr/lib/nvidia/libwfb.so.xserver-xorg-core', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx

---

### Post by birdySi on 2008-06-05
I removed manualy libwfb.so link and I was able to remove nvidia-glx, reinstall compiz and install nvidia-glx-new.

After restart (can't perform yet) I'll see if it's ok. At first look works fine. 

Thanks to all

---

### Post by birdySi on 2008-06-06
> **birdySi said:**
> I removed manualy libwfb.so link and I was able to remove nvidia-glx, reinstall compiz and install nvidia-glx-new.

After restart (can't perform yet) I'll see if it's ok. At first look works fine. 

Thanks to all

Ok, my response was too quick! Obviously I have problem with my nvidia drivers. I deinstalled nvidia-glx, nvidia-glx-new. I reinstalled nvidia-glx-new. Nothing better. Then I decided to remove again nvidia-glx-new and reinstall NVIDIA-Linux-x86-173.14.05-pkg1 driver from nvidia. Nothing better. Then I used command:

sudo dpkg-reconfigure -phigh xserver-xorg

This helepd me to arrange resolution. But I now I cant't run compiz any more. I even reinstalled nvidia-glx-new driver. But after running compiz I got message:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Does anybody nows how to solve the problem. Tnx.

---

### Post by danwood76 on 2008-06-06
Can you post your xorg.conf?

```

cat /etc/X11/xorg.conf

```
It may be that your not using the new drivers

---

### Post by birdySi on 2008-06-06
Meanwhile I removed nvidia-glx-new and reinstall nvidia-glx driver. The result is, that resolution is now ok, but still I can't run compiz (same error).

Here is my xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by birdySi on 2008-06-06
Hopfully in finaly I managed to work graphics & compiz like they should. From Synaptic Manager I uninstalled everything named "nvidia". Then I reinstalled nvidia-glx & linux-restricted-modules-2.6.24-18-386. Then I went to System > Administration > Hardware Drivers where I enabled NVIDIA driver. Then I followed steps from thread [http://ubuntuforums.org/showthread.php?t=651096](http://ubuntuforums.org/showthread.php?t=651096)

basicly:

```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

And wow! Finally worked properly (hope that would work on next reboot too :) )

But there goes new side efect problem: suddenly sound won't work. After simple command

```
aplay -l
```

I've got [B]aplay: device_list:205: no soundcards found...
[/B]
Ooops I removed to much so I reinstalled linux-386

```
sudo apt-get install linux-386
```

And now I'm finally using compiz with sound with graphics  :)

Tnx everybody in thread for help

---

