---
title: "problem with gtk???"
date: 2007-05-07
forum: General Help
---

### Post by Bashed on 2007-05-07
I don't know why this is, but can someone please explain the ugly interface that I am experiencing only on various areas (usually pop up dialog boxes and synaptic, firefox)

Firefox issue with default theme or custom theme, same problem. Firefox status bar for example, the beveled 
borders? This does not exist in Windows and its ugly here. I hope there is a solution.

---

### Post by Shadow503 on 2007-05-07
Can you post more screen shots? From what you've posted sofar, it looks like it simply might be an issue with the theme you choose in Firefox.

---

### Post by Bashed on 2007-05-07
> **Shadow503 said:**
> Can you post more screen shots? From what you've posted sofar, it looks like it simply might be an issue with the theme you choose in Firefox.

Please read my first post. I made it very clear, default firefox theme or custom - same results.

Here is more info, hopefully someone can help:

I'm struggling to get the best font quality possible in Ubuntu Feisty 7.04 here.

What I've done
- msttcorefonts [http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html](http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html)
- freetype [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)
- copy over all segoe*, calabra* and tahoma* fonts from Windows
- cloned firefox 2 font settings of Windows into here in Ubuntu
- I have gtk2-engines-pixbuf enabled by Ubuntu's default (double checked via synaptic)

My settings 

[IMG]http://img261.imageshack.us/img261/3284/snapshot4gs3.png[/IMG]
[IMG]http://img260.imageshack.us/img260/8281/snapshot5jy7.png[/IMG]

Firefox

[IMG]http://img120.imageshack.us/img120/4191/snapshot5zl8.png[/IMG]

---

### Post by Bashed on 2007-05-07
Comparison:

Linux

[IMG]http://img517.imageshack.us/img517/1829/snapshot1wj0.png[/IMG]

Windows

[IMG]http://img80.imageshack.us/img80/4571/fontsupportwindowshf6oq2.png[/IMG]

Linux 

[IMG]http://img359.imageshack.us/img359/6292/snapshot6yj2.png[/IMG]

Windows

[IMG]http://img382.imageshack.us/img382/2240/textfieldwindowsxt4er8.png[/IMG]

Linux

[IMG]http://img522.imageshack.us/img522/6021/snapshot2bo7.png[/IMG]

Windows
[IMG]http://img382.imageshack.us/img382/8665/tjhomewindowslc4rn5.png[/IMG]

Notice text is getting bolded too much and somehow larger?

Firefox linux:

[IMG]http://img263.imageshack.us/img263/7339/snapshot4ym3.png[/IMG]


No thick gray borders in windows like in linux

[[IMG]http://img368.imageshack.us/img368/9682/ffstatusbarwindowsum0.png[/IMG]]("http://imageshack.us")

---

### Post by Bashed on 2007-05-07
Maybe its the debian version of firefox specifically causing firefox issues?

Is it possible to download/install the regular 32bit or 64bit version of firefox to test?

i already downloaded i686 version from firefox.com, but I cannot seem to launch THAT version specifically because when I run firefox command in terminal, it opens the default installed 32bit version ([http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537))

---

### Post by Bashed on 2007-05-07
I just downloaded flock browser and ran "flock" via terminal, although it started up it gave a bunch of these errors:

(flock-bin:8092): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Bashed on 2007-05-08
Regarding firefox's interface (menu bar, status bar) I realized the default 64bit version does not show the tampered interface, but only in 32bit version (link I mentioned).

Anyone know why it is and how to fix this? I use 32bit for obvious reasons: plugins

Same issue with the light font.  It works fine in 64bit default, but not in 32bit

---

### Post by chrisccoulson on 2007-05-08
I had a problem similar to you too.

You're probably missing the 32-bit versions of the GTK engine you're using for your current theme. Check which GTK engines you currently have installed. You should have the following packages installed by default: gtk2-engines, gtk2-engines-pixbuf and gtk2-engines-ubuntulooks (I can't remember if any others are installedby default). You should also have ia32-libs-gtk installed, which will give you the 32 bit versions of the some of the default GTK engines, but not all of them. I think it misses pixbuf, and any additional GTK engines you have installed.

What you need to do is to download the i386 DEB's for the GTK engines that you are lacking, and then extract the contents of them to some temprary location. Navigate to /usr/lib/gtk-2.0/2.10.0/engines **within** the contents of the extracted package and copy the contents of that folder to /usr/lib32/gtk-2.0/2.10.0/engines. This should fix your problem.

This should fix it!

---

### Post by Bashed on 2007-05-08
I already have all these installed that you mentioned. 

What else to do?

---

### Post by chrisccoulson on 2007-05-08
Are you sure you've got the 32-bit pixbuf engine installed? It's not installed with ia32-libs-gtk and it doesn't seem to be installable via Synaptic on Feisty. What files have you got in /usr/lib32/gtk-2.0/2.10.0/engines? I had to manually extract the contents of the i386 deb to get themes to work properly on 32-bit apps.

---

