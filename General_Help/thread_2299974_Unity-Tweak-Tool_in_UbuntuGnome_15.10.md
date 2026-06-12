---
title: "Unity-Tweak-Tool in UbuntuGnome 15.10"
date: 2015-10-22
forum: General Help
---

### Post by Aydos on 2015-10-22
If you go to the Ubuntu Software Center and install Unity-Tweak-Tool it will say that it is finished and show it as installed.

However, you can not find it in your apps and if you go to command line and type unity-tweak-tool it will respond with a windows that says The following schema is missing com.canonical.notify-osd.

If you if you sudo apt-get install notify-osd and try again you will be greeted with another missing schema. Before I dove down the rabbit whole of installing these missing files I wanted to know if there was a better way to take care of this.

I had the same issue on the last release candidate that I tried. I did not test any other beta versions.

Any ideas?

---

### Post by mc4man on 2015-10-22
> **Aydos said:**
> If you go to the Ubuntu Software Center and install Unity-Tweak-Tool it will say that it is finished and show it as installed.

However, you can not find it in your apps and if you go to command line and type unity-tweak-tool it will respond with a windows that says The following schema is missing com.canonical.notify-osd.

If you if you sudo apt-get install notify-osd and try again you will be greeted with another missing schema. Before I dove down the rabbit whole of installing these missing files I wanted to know if there was a better way to take care of this.

I had the same issue on the last release candidate that I tried. I did not test any other beta versions.

Any ideas?
Why do you want unity-tweak-tool in Ubuntu-Gnome?
It won't show in a gnome session because it has no value & this line in it's .desktop
OnlyShowIn=Unity;

Use gnome-tweak-tool for gnome sessions

---

### Post by Aydos on 2015-10-22
I have always been able to use gnome-tweak-tool for the Gnome specific things and unity-tweak-tool for Ubuntu specific  things.

The installers are useful. 

For example I am having an issue after installing Google Chrome that apparently is resolved if you install it with Unity Tweak Tool instead of straight from Google.

---

### Post by buzzingrobot on 2015-10-22
Gnome Shell is not Unity, and Unity is not Gnome Shell  (also not built on Gnome Shell.) 

I'd guess that resolving the package's dependencies would simply install a lot of clutter... maybe all of Unity. And then most if it probably still wouldn't work because Unity depends on Compiz which does not exist in  -- and is incompatible with -- Gnome Shell.

As the man said, use Gnome Tweak Tool. I think it's installed by default in 15.10.

---

### Post by Aydos on 2015-10-22
I am using Gnome Tweak Tool for most of my stuff.

Also, I am not an idiot I know that Gnome and Unity are different.

There are things in Unity Tweak Tool that work for parts of Ubuntu completely independent of Unity. Kind of like Fedy in Fedora.

You could easily install Unity Tweak Tool in Ubuntu Gnome all the way up to and including Ubuntu Gnome 15.04.

I know, because the Ubuntu machine is one I have  been trying to get my wife use to using instead of my Arch machine.

I guess they removed some code from 15.04 to 15.10.

---

### Post by mc4man on 2015-10-22
> **Aydos said:**
> 
The installers are useful. 

For example I am having an issue after installing Google Chrome that apparently is resolved if you install it with Unity Tweak Tool instead of straight from Google.
Wasn't aware you can install packages from unity-tweak-tool, took a look & still am unaware.

You want it to show in a gnome session?,  then edit the .desktop
sudo -H gedit /usr/share/applications/unity-tweak-tool.desktop
edit the OnlyShowIn= line to 
OnlyShowIn=Unity;GNOME;
or get rid of the line altogether

---

### Post by Aydos on 2015-10-22
I will give this a try in a bit and report back.

I know on the RC that I was on after installing the osd package and making a desktop file it kicked back yet another schema error, but I decided to post here before messing with things today.

I did a clean install from the RC to the live version today.

---

