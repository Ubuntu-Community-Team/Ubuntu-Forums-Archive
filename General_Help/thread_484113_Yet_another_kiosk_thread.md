---
title: "Yet another kiosk thread"
date: 2007-06-25
forum: General Help
---

### Post by nipun_jain on 2007-06-25
Welcome to yet another kiosk post. I have gone through all the kiosk posts in the forums, and I assure you that I am going to ask new questions, and try not to repeat the old ones!

**Background**
I need to build a kiosk cd, running fullscreen firefox, with no other functionality (flash and java support would be nice, so would be the ability to configure one's internet connection)

**The Big Idea**
To make a lean distribution, based on XFCE, so that it runs easily on older machines. So I choose xubuntu, seeing how I am absolutely in love with Ubuntu (don't get any ideas, I meant that in a geeky way!)

**The Roadblock**
I was happy to discover that there existed tools like Ubuntu Customization Kit and Reconstructor for my purpose. Unfortunately, both didn't work with xubuntu. UCK asked for a selection of Window Manager between Gnome and KDE, while Reconstructor seemed to do nothing.

**Second Wind**
I got a second wind when I stumbled across the live cd customization page @ [https://help.ubuntu.com/community/LiveCDCustomization/](https://help.ubuntu.com/community/LiveCDCustomization/)

I proceeded via it and it seems to work.

**Finally, this is where I need the help**
1. What can I remove from the live cd, what applications, files, folders, anything that will reduce its size, without hampering the functionality required, namely fullscreen firefox.
2. How to install extensions to firefox on boot time? I am using 
```
/usr/bin/firefox -install-global-extension
```
in the xinitrc file, which doesnt seem to work. The extension I want to install is r-kiosk
3. How to install flash and java support in firefox.

I am sure I will run into more problems as I proceed, but let's handle them one at a time. ;)

Looking forward to any tips, code, links, opinions, or if you must, abuse for yet another kiosk thread! :(

---

### Post by kidders on 2007-06-26
Hi there,

I've never answered a kiosk-related question, but it seems to me that, if all you want to do is run a full-screen browser, there's very little point in having a window manager ... which should save you some space. Just for the sake of it, as a little experiment, I did...```
sudo X -ac :2
DISPLAY=:2 opera -fullscreen -kioskmode
```
(As you can see, I'm an Opera baby hehe.) How much space is your Xfce taking up?

As for your other questions, since you're going to the trouble of creating a custom LiveCD, it probably makes the most sense to pre-install any browser extensions/plugins you might want on it.

---

### Post by pointone on 2007-06-26
I completed an Ubuntu-based kiosk project not long ago for my university. 

Firstly, I'd strongly recommend you switch to the Opera web browser. While Firefox is nice and it is possible to hack a kiosk mode together with plugins and some manual labour, Opera comes with a built-in kiosk mode that is so much easier to configure and secure. There were some issues with Firefox where I was not able to completely block file system access, but it was a(lmost) piece of cake in Opera. Of course, security was a major issue with my project; I'm not sure if you need to take the same precautions.

Next, rather than tear down from a default desktop install (be it Ubuntu, Kubuntu or Xubuntu), I recommend you try building up from a minimal Ubuntu server installation. This will install the core operating system without any X server and unnecessary junk. You can then pick and choose what window manager, etc. to use and configure from scratch. I chose to use IceWM for my project. After you're doing configuring everything, you can remove a lot of the core tools like nano, vim, unneeded shells, man and info, etc. I found the debfoster tool really useful for this task: it'll go through each major package one by one and ask if you want to keep it or not. localepurge is another great tool for saving a bit more space. Finally, once you've go everything working great, you can remove the package management stuff and free up a LOT of space. ;)

Flash and Java support is as simple as downloading the Java runtime environment and Flash plugins. Check out:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
[http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)

As for installing extensions, you could try moving that command from xinitrc to a scrip that runs on boot (i.e. as root). Create a script, copy to /etc/init.d/ and run 'update-rc.d <scriptname> start 20 2 3 4 5 .'. I'm assuming it's not working because you're running as an underprivileged user.

I too tried a bunch of different options for building my kiosk on a CD. Remasting an existing Live CD proved to be unnecessarily complicated, and many of the other projects available to help with the task didn't allow the level of customizability I wanted. I ended up using a very nifty little package called bootcd. This package creates a bootable live CD based on the current distribution you're running. I installed and configured my system exactly as I wanted on a normal installation, ran the bootcd tools after everything was in order, and was left with a perfectly customized live CD. This allowed me to skip a lot of the hassle of remastering.

The major problems I ran into with this method were with configuring X.Org. Using the CD on different systems than the one I had built on required a bit of tweaking, but I managed to get a semi-automatic automatic configuration working in the end. Plus, from what I hear, future versions of X.Org will include much better hardware detection and configuration.

Oh, and kidders, I found I needed to use a window manager in order for popups to work correctly. I agree, it would be nice to skip the window manager altogether.

---

### Post by kidders on 2007-06-26
> **pointone said:**
> Oh, and kidders, I found I needed to use a window manager in order for popups to work correctly.Drat... you're right. I hadn't thought of that.

Thanks for mentioning it. :-)

---

### Post by nipun_jain on 2007-06-26
Thanks for the reply guys. Having no luck editing xubuntu, I took the ubuntu ISO and tried my luck by using UCK on that. Removed every darned package I thought I could, and the size is still 350 mb. I was looking for something smaller, something that can be fitted into a 256 mb USB drive. I am looking for alternatives, maybe x/k/ubuntu is not the distro to base a kiosk upon, I need something already stripped down (or rather never bloated up?). I am looking for alternatives.

If anyone could suggest a distro, small in size, with a graphical boot that is easy to rebrand, and an alternate window manager (for small size and for the sake of just running firefox and popups!), it would help a lot. I have almost tried every existing kiosk cd under the sun, and none's easy to remaster.

---

### Post by Iandefor on 2007-06-26
> **nipun_jain said:**
> Thanks for the reply guys. Having no luck editing xubuntu, I took the ubuntu ISO and tried my luck by using UCK on that. Removed every darned package I thought I could, and the size is still 350 mb. I was looking for something smaller, something that can be fitted into a 256 mb USB drive. I am looking for alternatives, maybe x/k/ubuntu is not the distro to base a kiosk upon, I need something already stripped down (or rather never bloated up?). I am looking for alternatives.

If anyone could suggest a distro, small in size, with a graphical boot that is easy to rebrand, and an alternate window manager (for small size and for the sake of just running firefox and popups!), it would help a lot. I have almost tried every existing kiosk cd under the sun, and none's easy to remaster. Try customizing Fedora using [Revisor]("http://revisor.fedoraunity.org/"). Uncheck every package except for the browser of your choice and a light window manager (if you need some ideas, ratpoison and ion would be good bets. You could also try a *box), and pull in any plugins. Dependency resolution will pull in all the dependencies for your browser and windowmanager (and, knowing rpm, a few completely unnecessary things, too). You're done.

---

### Post by pointone on 2007-06-26
> **nipun_jain said:**
> Removed every darned package I thought I could, and the size is still 350 mb. I was looking for something smaller, something that can be fitted into a 256 mb USB drive. I am looking for alternatives, maybe x/k/ubuntu is not the distro to base a kiosk upon, I need something already stripped down (or rather never bloated up?). I am looking for alternatives.

If anyone could suggest a distro, small in size, with a graphical boot that is easy to rebrand, and an alternate window manager (for small size and for the sake of just running firefox and popups!), it would help a lot. I have almost tried every existing kiosk cd under the sun, and none's easy to remaster.

I was able to get my Edgy Eft based kiosk down to 205 MB using the bootcd package I mentioned.

Have you looked at Damn Small Linux? Their use of extensions easily allows you to customize the CD without too much trouble, but this still requires some remastering skill. On the plus side, DSL uses Knoppix's hardware detection scripts, so you'll have no trouble porting it to other systems.

---

### Post by nipun_jain on 2007-06-27
> **Iandefor said:**
> Try customizing Fedora using [Revisor]("http://revisor.fedoraunity.org/"). Uncheck every package except for the browser of your choice and a light window manager (if you need some ideas, ratpoison and ion would be good bets. You could also try a *box), and pull in any plugins. Dependency resolution will pull in all the dependencies for your browser and windowmanager (and, knowing rpm, a few completely unnecessary things, too). You're done.

Thanks! Never heard of revisor before, maybe coz I have an aversion for fedora. I will look into revisor and see if I can get anything done.

I hope it runs on ubuntu. I would hate replacing ubuntu with fedora just for testing it out.

---

### Post by nipun_jain on 2007-06-27
> **pointone said:**
> I was able to get my Edgy Eft based kiosk down to 205 MB using the bootcd package I mentioned.

Have you looked at Damn Small Linux? Their use of extensions easily allows you to customize the CD without too much trouble, but this still requires some remastering skill. On the plus side, DSL uses Knoppix's hardware detection scripts, so you'll have no trouble porting it to other systems.

Yes I have. The problem basing my install on DSL is that it has a verbose mode boot, no upsplash, no graphical boot. And that's what I don't want. Seeing that my user base will be hardly computer literate, seeing the linux text scroll by will only serve to intimidate them. :(

And remastering DSL will be a pain in the ...
Bootsplash means kernel recompile, plus they have firefox 1, which I need to replace with FF 2.

So I was hoping to base it on ubuntu.

Could you provide some the link to the bootcd tools you are mentioning? And some tips, process, links (to tutorials which helped) etc which helped you make your kioskcd.

If you don't mind, I would  love to have a look at your kioskcd. I know it's old, but it will give me an idea about the level of customizability and remaster capability of the bootcd. I could give you an ftp to upload if you want.

---

### Post by pointone on 2007-06-27
Unfortunately, it was developed for use at my university and contains some somewhat sensitive information in the configuration files, but I've still got all the documentation I wrote for the project around somewhere including a step-by-step guide how to accomplish everything. I'll see if I can dig that up for you.

There's really no site for bootcd... just apt-get install bootcd and you're good to go! The documentation is all supplied with the package.

Run "bootcd-mkinitramfs" to regenerate a initrd image for booting from a CD, then run "bootcdwrite" to create an image of your currently running system. That's all there is to it!

As for tips and tutorials, I based my project on the original design described here:

[http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/LinuxKiosk](http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/LinuxKiosk)

But made some pretty significant changes. Everything else was touch-and-go, really. That link decribes how to remaster DSL, but I ran into some trouble and found the bootcd method much easier.

---

### Post by Iandefor on 2007-06-27
> **nipun_jain said:**
> Thanks! Never heard of revisor before, maybe coz I have an aversion for fedora. I will look into revisor and see if I can get anything done.

I hope it runs on ubuntu. I would hate replacing ubuntu with fedora just for testing it out. It was designed with Fedora 7 in mind as the host environment and I'm pretty certain it requires a working yum (last I checked, the yum in the Ubuntu repos was broken). Also, Fedora packages tend to bring in way more dependencies than they need to to actually work, so you might just have a lot more than you need.

I recommend checking out the latest source code if you intend to use it, by the way. It's under heavy development and the version in the Fedora repositories might not be the latest.

---

### Post by nipun_jain on 2007-06-27
> **pointone said:**
> Unfortunately, it was developed for use at my university and contains some somewhat sensitive information in the configuration files, but I've still got all the documentation I wrote for the project around somewhere including a step-by-step guide how to accomplish everything. I'll see if I can dig that up for you.

That would be really awesome. Do post here if you manage to find it, your guide will prove indispensable for me!

---

