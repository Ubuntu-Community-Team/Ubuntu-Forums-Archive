---
title: "Intel Linux Graphic Drivers on ubuntu"
date: 2014-05-25
forum: General Help
---

### Post by sameermw on 2014-05-25
I asked help for installing **linux intel graphic drives** on my **dell inspiron n4050** laptop and i got an answer like this. _*"[SIZE=3][COLOR=#ff0000][FONT=UbuntuRegular][/FONT][FONT=UbuntuRegular]It should be using the Intel drivers by default[/FONT][/COLOR][/SIZE][COLOR=#444444][FONT=UbuntuRegular]."[/FONT][/COLOR]*_*[COLOR=#444444][FONT=UbuntuRegular][/FONT][/COLOR]*[COLOR=#444444][FONT=UbuntuRegular] But when i surf the internet i found this.

[/FONT][/COLOR]wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -  

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

[COLOR=#333333][FONT=UbuntuRegular]Then retry[/FONT][/COLOR]

sudo apt-get update
sudo apt-get --reinstall install intel-linux-graphics-installer
[COLOR=#333333][FONT=UbuntuRegular]Then run the installer again

[http://www.webupd8.org/2013/08/official-intel-linux-graphics-installer.html](http://www.webupd8.org/2013/08/official-intel-linux-graphics-installer.html)

what is the real solution ? please help me, i can't understand it. thanks.[/FONT][/COLOR]

---

### Post by LastDino on 2014-05-25
Ubuntu installs free drivers by default, not proprietary one and Intel graphic drivers are open sourced. As far as what you're posting, I'm pretty sure it is applicable for 13.04 and maybe 13.10, and it is meant to get the latest version of those drivers by adding PPA to source list.

If you're not facing any particular problem, I suggest staying with what is working rather than adding this.

Also, read this really old page, especially part under Intel

[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

---

### Post by jeremy31 on 2014-05-25
> **sameermw said:**
> I asked help for installing **linux intel graphic drives** on my **dell inspiron n4050** laptop and i got an answer like this. _*"[SIZE=3][COLOR=#ff0000][FONT=UbuntuRegular]It should be using the Intel drivers by default[/FONT][/COLOR][/SIZE][COLOR=#444444][FONT=UbuntuRegular]."[/FONT][/COLOR]*_[COLOR=#444444][FONT=UbuntuRegular] But when i surf the internet i found this.

[/FONT][/COLOR]wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -  

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

[COLOR=#333333][FONT=UbuntuRegular]Then retry[/FONT][/COLOR]

sudo apt-get update
sudo apt-get --reinstall install intel-linux-graphics-installer
[COLOR=#333333][FONT=UbuntuRegular]Then run the installer again

[http://www.webupd8.org/2013/08/official-intel-linux-graphics-installer.html](http://www.webupd8.org/2013/08/official-intel-linux-graphics-installer.html)

what is the real solution ? please help me, i can't understand it. thanks.[/FONT][/COLOR]

What version of Ubuntu are you using?  If you are not having issues with your video/graphics/backlight, I wouldn't bother updating

---

### Post by Yellow Pasque on 2014-05-25
You're following an outdated link (the one from webupd8).

Also, is this your thread? [http://ubuntuforums.org/showthread.php?t=2225976](http://ubuntuforums.org/showthread.php?t=2225976)
If it is, please don't cross-post.

---

### Post by sameermw on 2014-05-25
@LastDino Thanks you so much for your comment the link.  No i don't have any problem and i was little bit curious to find out this thing.
@jeremy31 i'm using Ubuntu 14.04 and thank you too.
@Temujin It's not my thread,may be some one like me. This is my first post, thanks

---

### Post by grahammechanical on 2014-05-25
The developers of video drivers are always working on the next version. They post these "latest" versions on their web sites. Some people like to download them and install them because they think that the latest must also be the greatest. That is not always the case.

The Ubuntu developers do not rush to make the very latest drivers available through Additional Drivers because they are aware of the possibility that these "latest and greatest" video drivers will break the OS. Ubuntu will always install with the most stable and tested version of the driver.

The same situation exists with other software in Ubuntu. Some people complain that the latest version of Firefox or Libreoffice is available in some web site but it is not yet in Ubuntu. It is for exactly the same reason.

Regards.

---

### Post by jeremy31 on 2014-05-25
> **grahammechanical said:**
> The developers of video drivers are always working on the next version. They post these "latest" versions on their web sites. Some people like to download them and install them because they think that the latest must also be the greatest. That is not always the case.

The Ubuntu developers do not rush to make the very latest drivers available through Additional Drivers because they are aware of the possibility that these "latest and greatest" video drivers will break the OS. Ubuntu will always install with the most stable and tested version of the driver.

The same situation exists with other software in Ubuntu. Some people complain that the latest version of Firefox or Libreoffice is available in some web site but it is not yet in Ubuntu. It is for exactly the same reason.

Regards.

The same issue exists with the Linux stable kernel releases, some may cause more problems than they solve as some drivers and patches are included.  It seems to be a PC world that revolves around Windows and Linux has to keep up.  That is a difficult task considering all the different hardware configs and some PC manufacturers updating their BIOS just to compensate for a windows issue or change.

Is there a real difference between using a download.01.org repo vs using the intel-linux-graphics-installer?  I would rather update my kernel than update drivers with intel-linux-graphics-installer as it is easier to go back to using an older kernel but that is just my opinion

---

### Post by monkeybrain20122 on 2014-05-25
Depending on your card, you may have some performance gain with the latest driver. here is where you can get the latest intel driver. [https://launchpad.net/~oibaf/+archive/graphics-drivers/+index?field.series_filter=](https://launchpad.net/~oibaf/+archive/graphics-drivers/+index?field.series_filter=)

It performs better on my machine (core i5 ironlake) than the stock Ubuntu driver. The only set back is that [http://3d.si.edu/](http://3d.si.edu/) no longer works (works with stock Ubuntu driver) and shows a black image for the 3d models.

I suggest you try it out and decide if it works better for your case. I don't buy the Ubuntu dev know best idea and be stuck with buggy or non performant software just because it is 'supported'. Look at 12.04 now, the 'supported' version of everything is so old that it is like centuries behind (mesa 8, gimp 2.6, LibreOffice 3.x) The latest may not be better, but in itself it is not an argument that old is better, if that is the case why bother doing any development?

 If you know what you are doing it doesn't hurt to experiment a bit to find what works best for you.

---

