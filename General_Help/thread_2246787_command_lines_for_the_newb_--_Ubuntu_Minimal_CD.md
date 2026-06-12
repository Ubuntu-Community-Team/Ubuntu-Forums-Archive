---
title: "command lines for the newb -- Ubuntu Minimal CD"
date: 2014-10-03
forum: General Help
---

### Post by wog on 2014-10-03
For a lack of media, I was forced to use a CD to install with. 
The only CD-size install of Ubuntu I could find was Ubuntu Minimal CD.

I am installing on an old Inspiron 6000. 

The installation process completed, but instead of getting a window manager or GUI, I got a command line, and I'm just not all that familiar with apt-get. Worse, 'sudo apt-get install xfce' gets me 'E: Unable to locate package xfce'.

How do I install a window manager or environment, and then, how do I start it from the command line? 
Even better, how do I set it up so the machine goes directly to the window manager without going to the command line first?

Thanks in advance!

---

### Post by slickymaster on 2014-10-03
A minimal installation is a command-line only system, but it does include networking and apt-get. You can use apt-get to install whatever else you need. It will automatically access the Internet if you plug it into a wired Ethernet network providing an Internet connection. If you use wireless, you'll probably have to configure that manually. If you're able to use a wired connection until you have your GUI installed, that might save you some hassle.

With networking working, you should first update all the packages on your command-line system:```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then you can install a GUI, and afterwards a window manager, which must be present for any GUI otherwise application windows pop up and cannot be moved, hidden, switched between, resized, and so forth.

---

### Post by buzzingrobot on 2014-10-03
The rather unobvious command "apt-cache search  xxxx" will search the package list.  E.g., "apt-cache search xfce" will display a list of packages with "xfce" in their name.  (I don't see anything called simply "xfce".)

 Searching on "XFCE" will return a few dozen items. The Xubuntu distribution is the Ubuntu family's treatment of XFCE, and it's much more presentable and useful than the retrograde look of a default XFCE install. It's available as "xubuntu-desktop".

Assuming you use the mini.iso image (essentially, it's a network install) during the minimal install procedure, you are asked to select software to be installed. Xubuntu is also listed there as an option.

Installing xubuntu-desktop will pull in all the other needed dependencies.  You'll boot straight into X, the graphical display.

---

### Post by slickymaster on 2014-10-03
Sorry, forgot the about installing the desktop manager and the windows manager. :(
If you want a fully-featured GUI as though you'd installed regular Ubuntu, Xubuntu, Kubuntu, or Lubuntu, but without the applications that come with them, then you can install one of these packages with the **--no-install-recommends** flag:```

sudo apt-get --no-install-recommends install ubuntu-desktop
sudo apt-get --no-install-recommends install xubuntu-desktop
sudo apt-get --no-install-recommends install kubuntu-desktop
sudo apt-get --no-install-recommends install lubuntu-desktop
```
If you want something more minimal, you can install the X server xorg (which must be present for any GUI on Ubuntu):```
sudo apt-get install xorg
```
Then install the window manager.

---

### Post by ian-weisser on 2014-10-03
EDIT:  Slickymaster said it better than I did.

---

### Post by elysian2 on 2014-10-03
```

apt-get install tasksel

```

Then enter tasksel to install any desktop.

---

### Post by grahammechanical on 2014-10-03
I recently installed a full Ubuntu desktop using the mini ISO image. And I could have chosen other desktop environments if I wanted to. This mini ISO image is less than 40 MB in size and everything has to be downloaded from the internet.

The basic install is Linux, which is a command line OS. I would say that it is assumed that everything else will be installed from the command line. It is possible to work our way through the text menu layers to get where we can select desktop environments but it is not obvious how it should be done. I had to back out and start again more than once. I would not like to be tasked with writing a tutorial for this as there are a confusing array of options.

Regards.

---

### Post by wog on 2014-10-03
When I used Minimal CD it offered various packages to install. I picked Xubuntu, but I guess it didn't work.
Apparently I also chose the wrong keyboard, because I can't type the pipe symbol now. I get an accented 'a' instead.

Anyone know how to change the keyboard, perchance? :)

---

### Post by slickymaster on 2014-10-03
> **wog said:**
> When I used Minimal CD it offered various packages to install. I picked Xubuntu, but I guess it didn't work.
Apparently I also chose the wrong keyboard, because I can't type the pipe symbol now. I get an accented 'a' instead.

Anyone know how to change the keyboard, perchance? :)
Please try the following command:```
sudo dpkg-reconfigure console-data
```If it says you don't have the package, then install console-data with:```
sudo apt-get install console-data
```After running the **sudo dpkg-reconfigure console-data** command, the configuration dialog is displayed, choose to select a keymap from the "arch list". The most tipical keyboard layout is "qwerty" (look at the first row of letters in your keyboard) so choose this unless you have something different. Next, select a keyboard layout.

You might have a read at [https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by wog on 2014-10-06
I think as soon as I installed console-data, the installer ran it automagically. This means I have my pipe symbol again.

I went with lubuntu, and frankly, it's sort of sold me on installing it on my other machines as well. I like it much better than Unity. 
Is lxde as lightweight as xfce, or is that question a religious war waiting to happen? 

Thank you, Elysian2, I didn't know about tasksel. 

Thank you, Slickymaster. I guess it's time to start making notes about Linux again, starting with these. :)

---

### Post by slickymaster on 2014-10-07
> **wog said:**
> I think as soon as I installed console-data, the installer ran it automagically. This means I have my pipe symbol again.

I went with lubuntu, and frankly, it's sort of sold me on installing it on my other machines as well. I like it much better than Unity. 
Is lxde as lightweight as xfce, or is that question a religious war waiting to happen? 

Thank you, Elysian2, I didn't know about tasksel. 

Thank you, Slickymaster. I guess it's time to start making notes about Linux again, starting with these. :)

You're welcome wog.

Lxde is definitely lighter/faster than Xfce, but it has less features.

You can have a read on the subject at: [Comparison between LXDE and Xfce]("http://wiki.lxde.org/en/Comparison_between_LXDE_and_Xfce")

Happy *buntuing.

---

