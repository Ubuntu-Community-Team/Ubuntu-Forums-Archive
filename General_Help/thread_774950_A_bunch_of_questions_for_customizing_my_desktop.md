---
title: "A bunch of questions for customizing my desktop"
date: 2008-04-29
forum: General Help
---

### Post by AWCADDET on 2008-04-29
Hello all.

I have a question about different theme engines and such.

When looking around on website, such as gnome-look I see a bunch of different types of theme, GTK2.0, Metacity, Compiz, Emerald and such. I have come to the point where I just don't know what is what anymore.

I have been trying to make my desktop nice, and so far all I have got working is Compiz, and the cube effects and such.

I tried skinning my desktop with Emerald, and that wouldn't work. I could install a skin, and see the preview in the application, but not actually apply it.

I have started trying to use GTK themes, and noticed some of them worked when dragging + dropping them into the "Appearance" tool. However there is this one theme I want
```
http://www.gnome-look.org/content/show.php/Neon+Aurora?content=79702
```

Which said I needed some kind of Aurora GTK engine. So I go and install that, and I still have no idea on how I am meant to apply that theme. Am I supposed to change it from the "Appearance" tool from Preferences? Or is there supposed to be another utility I use to apply such themes?


I am really getting confused about what each of these engines do, and how It should work when I have them installed.

Any help on the matter will be greatly appreciated.

Thanks

---

### Post by Shadius on 2008-04-29
Hello. I'm sorry, but I won't be able to help you here since I am just starting to use Ubuntu so I do not know much. Maybe you can help me learn about the Desktop Effects though since I would like to get my desktop to look nice as well. You mentioned you skinned your desktop, how did you do that and where did you get the skins? What is Emerald? What is GTK? Sorry for so many questions, I'm just trying to learn as much as I can.

---

### Post by AWCADDET on 2008-04-29
Well I don't exactly know what they are, or mean.

But I found that some GTK2.0 themes from **gnome-look.org** will work by

-downloading them
-extracting the theme, and then placing it into the **Appearance** utility, found in **System > Preference**

However some in that section require some kind of special engine, Aurora GTK, which I have no idea how to operate.

---

### Post by Moop on 2008-04-29
> **AWCADDET said:**
> Well I don't exactly know what they are, or mean.

But I found that some GTK2.0 themes from **gnome-look.org** will work by

-downloading them
-extracting the theme, and then placing it into the **Appearance** utility, found in **System > Preference**

However some in that section require some kind of special engine, Aurora GTK, which I have no idea how to operate.

You don't want to extract the themes before you install them or they won't work. To use emerald themes you will need to install emerald. It's available in Synaptic. You also might want to install gnome-art and the fusion-icon.

---

### Post by Shadius on 2008-04-29
My compiz fusion doesn't work, any help?

---

### Post by AWCADDET on 2008-04-29
Yeah I had emerald installed, and I figured out that it wasn't working unless I had the Compiz Fusion Icon installed.

So am I right in thinking, that for the mainstream customization (GUI Themes and such) then Compiz is the tool to manage it all? Because I see I can also change engines from this tool as well.


And does anyone know about the Aurora GTK engine, and how I get that working?

---

### Post by Shadius on 2008-04-29
> **AWCADDET said:**
> Yeah I had emerald installed, and I figured out that it wasn't working unless I had the Compiz Fusion Icon installed.

So am I right in thinking, that for the mainstream customization (GUI Themes and such) then Compiz is the tool to manage it all? Because I see I can also change engines from this tool as well.


And does anyone know about the Aurora GTK engine, and how I get that working?
Wait. First, I just want to get CCSM working first. Compiz Fusion controls alot of desktop effects. That's as much as I know. Hope that helps.

---

### Post by sowelie on 2008-04-29
To clarify:

GTK Themes are themes for the window controls (text boxes, radio buttons, check boxes, background colors / images, progress bars etc.).

Emerald themes are themes for the window borders if you are using emerald as your window decorator.  To use emerald you need to make sure it's installed and also that it's active.

```
sudo aptitude install emerald
```

If you installed emerald and it doesn't seem to be working, make sure you have the advanced desktop settings installed:

```
sudo aptitude install compizconfig-settings-manager
```

Then, go to system -> preferences -> advanced desktop settings.  Find "Window Decoration", and where it says "Command" make sure "/usr/bin/emerald" is there.  Then, I think you'll need to restart compiz to make it work:

```
compiz --replace
```

Metacity themes are themes for the default window decorator in GNOME, metacity.  If you're using compiz I'd recommend using emerald.

Compiz themes are actually emerald themes (same with beryl themes).  Although, some of the older ones may be fore the old compiz window decorator.

To install GTK themes, the best way to do it is to extract them to the /usr/share/themes folder, that way if you run an application as the administrator, you still get the theme.

```
sudo tar xzvf name-of-archive.tar.gz --directory=/usr/share/themes
```

If the archive is a tar.bz2 you'll need to change the tar xzvf to tar xjvf.

For icon themes, do the same except extract them to /usr/share/icons.

---

### Post by sowelie on 2008-04-29
As far as the engines go, like aurora, just make sure it's installed:

```
sudo aptitude install aurora
```

If you want to see all of the engines, run this:

```
sudo aptitude search gtk2-engines
```

And then the themes will work with my method above.

---

### Post by Shadius on 2008-04-29
> **sowelie said:**
> To clarify:

GTK Themes are themes for the window controls (text boxes, radio buttons, check boxes, background colors / images, progress bars etc.).

Emerald themes are themes for the window borders if you are using emerald as your window decorator.  To use emerald you need to make sure it's installed and also that it's active.

```
sudo aptitude install emerald
```

If you installed emerald and it doesn't seem to be working, make sure you have the advanced desktop settings installed:

```
sudo aptitude install compizconfig-settings-manager
```

Then, go to system -> preferences -> advanced desktop settings.  Find "Window Decoration", and where it says "Command" make sure "/usr/bin/emerald" is there.  Then, I think you'll need to restart compiz to make it work:

```
compiz --replace
```

Metacity themes are themes for the default window decorator in GNOME, metacity.  If you're using compiz I'd recommend using emerald.

Compiz themes are actually emerald themes (same with beryl themes).  Although, some of the older ones may be fore the old compiz window decorator.

To install GTK themes, the best way to do it is to extract them to the /usr/share/themes folder, that way if you run an application as the administrator, you still get the theme.

```
sudo tar xzvf name-of-archive.tar.gz --directory=/usr/share/themes
```

If the archive is a tar.bz2 you'll need to change the tar xzvf to tar xjvf.

For icon themes, do the same except extract them to /usr/share/icons.
Okay, here's my problem, when I do "sudo apt-get install compizconfig-settings-manager" in terminal, I get errors, and CCSM isn't installed. How do I fix this?

---

### Post by sowelie on 2008-04-29
What's the error you get?

---

### Post by AWCADDET on 2008-04-29
Great! Thanks a lot pal on clarifying those up for me, and the last part about GTK and Icons was a great deal of help :D

Now I have a better understanding I will be more confident in making my desktop look like I want it.

Thanks a lot people for the support in this thread, you make me proud to have finally jumped onto the Ubuntu wagon :)

---

### Post by Moop on 2008-04-29
I went to that site and downloaded the theme and installed it no problem. I didn't need any special engine. To get the full effect of the theme use the fusion icon and select the window decorator as gtk.

---

### Post by AWCADDET on 2008-04-29
Yeah I see that I wasn't applying the themes right in the first place, and kept making a mess of everything. But it's fixed now :D

Thanks

---

### Post by Shadius on 2008-04-29
sshadius@shadius-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
shadius@shadius-desktop:~$


This is the error I get. What now?

---

### Post by Shadius on 2008-04-29
Hey, how does your desktop look now with all that GTK stuff. LoL. Could you take a screenshot and post it? I'd like to see.

---

### Post by AWCADDET on 2008-04-29
I will take a screenshot and upload it later, when I have finally finished it :D

Currently it looks like a construction site because I have loads of panels floating around :)

And good luck with your ccsm matey

---

### Post by sowelie on 2008-04-29
> **Shadius said:**
> sshadius@shadius-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
shadius@shadius-desktop:~$


This is the error I get. What now?

Sounds like the package wasn't fully installed.  Run this:

```
sudo apt-get -f install
```

---

### Post by Shadius on 2008-04-29
> **sowelie said:**
> Sounds like the package wasn't fully installed.  Run this:

```
sudo apt-get -f install
```
shadius@shadius-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
shadius@shadius-desktop:~$ 


This is what I get.

---

### Post by sowelie on 2008-04-29
I'm not sure what your issues are being caused by.  Did you do anything funky with python installs?  I would search around for those pythoncentral errors you're getting.

---

### Post by Shadius on 2008-04-29
> **sowelie said:**
> I'm not sure what your issues are being caused by.  Did you do anything funky with python installs?  I would search around for those pythoncentral errors you're getting.
Well, before I got these errors, I ran a script from this forum. Compiz-git.
[http://ubuntuforums.org/showthread.php?t=763829&page=7](http://ubuntuforums.org/showthread.php?t=763829&page=7)

Okay, I think I solved the problem with getting Compiz Fusion back, but when I try to enable Desktop Effects. It tells me that it cannot be enabled. Huh? What's going on now?????????????????????????

---

### Post by AWCADDET on 2008-04-29
Oh, I just tried putting those Themes/Icons into that folder, and I get this error

```
christianalder@christianalder-laptop:~$ sudo tar xzvf black-white_2-Style.tar.gz --directory=/usr/share/icons
tar: black-white_2-Style.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
christianalder@christianalder-laptop:~$ 

```

I checked the spelling, and it was fine, any idea what the problem is, and how to fix it?

Thanks

---

### Post by VraiChevalier on 2008-04-29
> **Shadius said:**
> Well, before I got these errors, I ran a script from this forum. Compiz-git.
[http://ubuntuforums.org/showthread.php?t=763829&page=7](http://ubuntuforums.org/showthread.php?t=763829&page=7)

Okay, I think I solved the problem with getting Compiz Fusion back, but when I try to enable Desktop Effects. It tells me that it cannot be enabled. Huh? What's going on now?????????????????????????

You may need to install and/or enable Restricted drivers for your graphics card. You can find them under System>Administration>Hardware Drivers.

---

### Post by Shadius on 2008-04-29
It says the driver is already in use. This sux.

---

### Post by Shadius on 2008-04-29
Okay, how do I go back to 7.10 from 8.04??

---

### Post by sujoy on 2008-04-30
if you have a separate /home partition, then i would say, just reinstall

---

### Post by sowelie on 2008-04-30
Hah, also ignore my comment about sudo aptitude install aurora, I forgot I built a deb package for that on my own.  It's not in the repo.

---

### Post by Shadius on 2008-04-30
> **sujoy said:**
> if you have a separate /home partition, then i would say, just reinstall
I'm dual-booting, Windows & Ubuntu. Mannnnnnnnnn, this suxxxxxxxxxxxxxxxxxx!!!!!!!!!!!

---

