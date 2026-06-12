---
title: "[SOLVED] Which packages can I get rid of?"
date: 2008-06-04
forum: General Help
---

### Post by leetrefz on 2008-06-04
I only have a 4g drive. I want to delete as many useless packages as possible. I don't understand what many are for, so I'd like some advice! Which ones do no casual home PC user need? 

I only use Firefox, VLC, Transmission, Abiword, Pidgin, Ekiga, Brasero, Ristretto, bootcd & maybe Gimp.

I've cleaned up with deborphan, localepurge, '*sudo apt-get autoclean*,' and '*sudo apt-get autoremove*' but am interested how small Xubuntu can be pushed. Now using exactly 2 gigs (inc Google Earth) and I don't know anything Vista can do that I can't do (20 times faster).

I may use a printer in the future, worried if I take all that stuff away will be in for a headache later. Otherwise only have USB, PS2, VGA, DVI, LAN, ATA & SATA ports.

Many things I'd like to remove are depended on by the likes of xubuntu-desktop, the appended removal of which I assume will leave me with only a command prompt.

I figure there's lots there any non-guru will never use, hope we can get a list that many people will find useful!

---

### Post by bingoUV on 2008-06-04
I see that you don't need openoffice. You will gain an large amount of disk space by removing it.

Otherwise, try searching in "dpkg --list" for screensavers, wallpapers, help files, language packs, man pages etc. and remove them.

---

### Post by leetrefz on 2008-06-05
Trying to get through that list but most screensavers are depended on by xubuntu-desktop which I don't think i can remove. only have some library type packages from openoffice that are depended on by other non-openoffuce packages for some reason. will check more carefully for man packages etc see if i missed anything.

---

### Post by Xiong Chiamiov on 2008-06-05
Personally, I'd uninstall the xubuntu-desktop package and just install xfce by itself.  That will include xfce without all the extra crap that automatically comes with it.

---

### Post by leetrefz on 2008-06-05
Ok. Anyone know any spurious non gui programs hanging around that the average user will never use? I'm afraid if remove something I don't understand I'll lose some basic functionality.

Particularly, do I need: 

gcc-4.1
mcpp
xpmutils
python-xml 
linux-image-2.6.24-17-generic (since I have linux-generic)

---

### Post by drs305 on 2008-06-05
Another option if you really need space is to remove all the files in /var/cache/apt/archives  . These are all the deb files for apps installed on your computer. They are the current debs but are available for download if you should ever need them again. 

There is also an app called *aptoncd* that transfers these files to a cd so you can retrieve them without a lengthy download. 

From the man page:
```
 clean clears out the local repository of retrieved package files. It 
removes everything but the lock file from /var/cache/apt/archives/ and 
/var/cache/apt/archives/partial/. When APT is used as a dselect(8) method, 
clean is run automatically. Those who do not use dselect will likely want to 
run apt-get clean from time to time to free up disk space.

```

```
apt-get clean
```

---

### Post by cariboo on 2008-06-06
Instead of trying to figure out what is safe to remove, why not do a new installation using the Ubuntu minimal CD available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and just install what you want. I would suggest just install the cli and then search the forums here for what else to install.

Jim

---

### Post by heatblazer on 2008-06-06
So you want a compact ubuntu. Well. I`ll recommend you one thing, make sure you are uninstalling the old linux-kernels. They take a lot of HDD space. Keep one or 2 kernels. Personally I keep only the latest release. Another advice - OOfice, it`s huge; GIMP is huge too. Xubuntu must be smaller since it has xfce not the big GNOME.

---

### Post by leetrefz on 2008-06-06
After removing that old kernel and gimp I've got 140mb more free, totalling 1.77gigs free, compared to 2.2gigs before upgrading to Xubuntu 8.04. 

apt-get clean doesn't seem to do anything, maybe because I recently did apt-get autoclean. Wonder if aptoncd works with usb flash drives. Would do Ubuntu mini, but my box is working so well right now.

Can anyone tell me if I can safely remove the other packages mentioned in my last post?

---

### Post by kpkeerthi on 2008-06-06
You may uninstall these two packages if you are not going to compile and build applications from source in your system:

**linux-headers-generic**
**build-essential**

* If you remove build-essential, gcc will also be removed. gcc is a C compiler.
* Do not remove linux-image-****-generic. Thats your kernel.

---

### Post by kpkeerthi on 2008-06-06
The latest kernel version Hardy has is linux-image-2.6.24-**18**-generic. If everything works well in 18, you may uninstall linux-image-2.6.24-**17**-generic

See this post to remove your kernel the right way:
[http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3)

---

### Post by kpkeerthi on 2008-06-06
As for the other package, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/). Use the search feature at the bottom of the page to find more information about a package. That should help you decide if you would need a package or not.

Or use this command to know more about a package:
```
aptitude show <package-name>
```

E.g.: ```
aptitude show xpmutils
```

---

### Post by leetrefz on 2008-06-06
removed linux-headers-generic but didn't have build-essential so took out gcc and it's 4.1 base. Wasn't huge, but every little bit counts.

How about linux-headers-2.6.24-18-generic?
already lacking ...17 kernel.

What's taking up so much more space than xubuntu 7.10?

---

### Post by leetrefz on 2008-06-07
My largest package is openoffice.org-core, even though I don't have ooffice. The basic english support depends on this 114mb pack. hard to believe it's really necessary, no alternative? 

Is everything in /usr/share/app-install/ really necessary?

---

### Post by kpkeerthi on 2008-06-09
> **leetrefz said:**
> removed linux-headers-generic but didn't have build-essential so took out gcc and it's 4.1 base. Wasn't huge, but every little bit counts.

How about linux-headers-2.6.24-18-generic?
already lacking ...17 kernel.

What's taking up so much more space than xubuntu 7.10?

Yes you can like I told you in one of my previous posts. Uninstall using ```
sudo aptitude purge linux-headers-generic
```

---

### Post by kpkeerthi on 2008-06-09
> **leetrefz said:**
> My largest package is openoffice.org-core, even though I don't have ooffice. The basic english support depends on this 114mb pack. hard to believe it's really necessary, no alternative? 


You may try abiword (for word processing) and gnumeric (for spreadsheets)

---

### Post by stu1978 on 2008-06-09
I got rid of office and used google docs online.  Saves space having no program installed, and your files are stored online. (space saver and already backed up if you need to reinstall)

---

### Post by leetrefz on 2008-06-09
Ya on Xubuntu which only comes with abiword. Can't see why I need Openoffice.org-core, 7 other ooffice packs & a number of other sizable ones for the mozilla locale and language-support-en when no Ooffice programs have ever been installed. I can only assume that the Ubuntu developers reasonably assumed everyone would use Ooffice so borrowed their files for Ubuntu's English support to save space, while the xubuntu developers didnt include ooffice & weren't as zealous as they could've been about readiness for low resource systems, xfce's main market. As far as I know they could have found a smaller alternative to openoffice.org-core, after all abiword doesn't need it, why should xubuntu? Openoffice.org-core is the largest pack, twice the size of the next.

---

### Post by jocko on 2008-06-09
> **leetrefz said:**
> Can't see why I need Openoffice.org-core, 7 other ooffice packs & a number of other sizable ones for the mozilla locale and language-support-en when no Ooffice programs have ever been installed.

I don't think you need to keep "language-support-en" it's just a meta package which is dependent on a bunch of language packs.
Removing the meta package will not remove the installed dependencies. So removing "openoffice.org-core" should be absolutely safe. Do it with synaptic and check the files that are marked for removal before you apply, and you'll see that the only real packages that will be removed are related to openoffice.

---

### Post by kpkeerthi on 2008-06-09
I found some additional tips here:
[http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)

Hope it is useful for you.

---

### Post by leetrefz on 2008-06-09
These last 2 posts are incredibly good news. My ignorance of Linux is melting away. I now use 1.1 gig. deborphan is indispensable especially now that I understand metapacks etc. Thank you all.

---

