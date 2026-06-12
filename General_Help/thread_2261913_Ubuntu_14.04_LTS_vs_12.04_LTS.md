---
title: "Ubuntu 14.04 LTS vs 12.04 LTS?"
date: 2015-01-21
forum: General Help
---

### Post by ChaoticFlounder on 2015-01-21
All,

I am considering reinstalling my current Ubuntu OS (14.04 LTS) due to the fact that I may have damaged it beyond repair??? in the process of learning the OS and command line.  Anyways, before I do this I was wondering if I might should use 12.04 LTS instead?  I wanted to ask the many, many knowledgeable individuals on here what their opinions were, and maybe if I should use something completely outside the Ubuntu family?

Thanks for the help,

C

---

### Post by sammiev on 2015-01-21
If you had no issues with 14.04 I would stay with it but you may want to try 12.04 on a USB live to see if it works with your hardware.

---

### Post by monkeybrain20122 on 2015-01-22
Unless you have very old hardware use 14.04. !2.04 is very outdated by now.

---

### Post by mastablasta on 2015-01-22
presumably you are happy with ubuntu, so stay with it.

you can safely leanr command line by installing for example Ubuntu minimal install (barebones) iso in virtualbox. you can then create a snapshot, messup the whole OS in virtualbox and then just restore the snapshot. CLI only interface will run fast and doesn't need more than 256MB or maybe 348 MB ram.

how to install inside virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
how to install minimal iso: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

you can also get premade images, so you don't need to mess with install. if you look at Bitnami stack (Ubutnu based) or Turnkey linux (Debian based). but there are alo sites like this: [http://www.osboxes.org/ubuntu/](http://www.osboxes.org/ubuntu/)
that provide ready made images.

---

### Post by ChaoticFlounder on 2015-01-22
Wonderful.  My PC is a custom machine and not really lacking (relatively speaking) on hardware power.  i5-3570k, GTX680, 16GB RAM, ... etc.  So hardware isn't a constraint but still i'm a mechanical engineer and typically a no frills kind of guy.  I will definitely go with 14.04 LTS per your recommendation.  Would any of you suggest Xubuntu or Kubuntu instead of standard Ubuntu?

Thanks again,

C

---

### Post by pfeiffep on 2015-01-22
> **ChaoticFlounder said:**
>   Would any of you suggest Xubuntu or Kubuntu instead of standard Ubuntu?

Thanks again, I suspect your hardware runs mainstream Ubuntu just fine, some of the differences in K or X will be desktop environments. 
If you didn't particularly enjoy Unity then mainstream Ubuntu with gnome flashback might be right up your alley. 

If you are unsure I suggest you try them out on a live flash drive or DVD before actual install.

---

### Post by ChaoticFlounder on 2015-01-22
Yea, Ubuntu seems to be no problem.  However, I wasn't crazy about Unity so I'll give some different DE's a shot.  Will a quick search in the Desktop Environment forum give me all the info I need to know about putting gnome flashback on an Ubuntu 14.04 LTS installation?  Also, would you recommend the KDE or ... what's the one for Xubuntu?

Thanks,

C

---

### Post by sammiev on 2015-01-22
You can download each on on try them live on a DVD/USB. I prefer the USB myself, less chance of errors.

---

### Post by coldraven on 2015-01-22
You can get them all here. After choosing one scroll down for different download options. I usually use the torrent option because it is faster.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by ChaoticFlounder on 2015-01-22
Please forgive my ignorance ... can you download a "vanilla" version of Ubuntu 14.04 LTS .iso and install it and **then **add the DE you want or does the Desktop Environment you desire have to be in the .iso image when you go to install the OS?  Or, say I wanted the KDE desktop environment (<- is that redundant?), is it best to download Kubuntu or go the route above with downloading a "vanilla" version and then adding the desired DE?

C

---

### Post by mastablasta on 2015-01-23
> **ChaoticFlounder said:**
> Please forgive my ignorance ... can you download a "vanilla" version of Ubuntu 14.04 LTS .iso and install it and **then **add the DE you want or does the Desktop Environment you desire have to be in the .iso image when you go to install the OS?  Or, say I wanted the KDE desktop environment (<- is that redundant?), is it best to download Kubuntu or go the route above with downloading a "vanilla" version and then adding the desired DE?

C

you can. you can have multiple desktops installed at the same time. you select which one you want on login screen (which is actually called desktop manager).

however you should know that desktop is not just how it looks and feels. it's not just a theme. it's a whole concept. it includes specific libraries (e.g. KDE USES QT, Gnome uses GTK), it has a windows manager (e.g. KDE has Kwin, Gnome has Mutter..), it also has a collection of programs designed to fit well into the desktop (e.g. network manager, office suite...).

so for example you have standard Ubuntu and then decide to add Kubuntu desktop. a lot will be loaded. so you will end up with two network managers, two desktop manager, two calendars etc. you get the point. ofcourse the way around this is to add just KDE package, which should pull in much less.

you can mix and match programs from various desktops. the software manager will pull everything they need along with them. so if you have "pure" Ubuntu and then decide to add a good KDE program like for example k3b it will pull a lot of staff from KDE. anyway disk is not such an issue these days.

My personal preference is KDE (Kubuntu) - it can easily be setup they way one want it. It has GUI for many things (which I like) and in my opinion it has many very good native applications. It also uses traditional desktop as premise (though there exists a touch and small-screen/netbook version). On slower PCs I usually use XFCE - also very easy to configure but much lighter on system resources. Has a touch too much Gnome philosophy in it to be my no1. but you just need to try them out see what fits you best.

when I have time (not often these days) I learn and play with i3. it's a tabbed windows manager. low resources and once you learn the shortcuts it's really fast. there are many windows managers (like for example jWM) that have super low memory and CPU footprint (a few MB of ram is what is needed). good for those really old PC.

try it live form USB see what you like and then install. you can use multiboot such a yumi to install multiple version on one USB then just try them out.

---

### Post by coldraven on 2015-01-23
You can easily make a bootable USB stick or SD card and try out the different versions before installing (It is called a Live USB or Live CD/DVD if you want to burn discs)
Recent versions of Ubuntu are now too big to fit on a CD so burning to USB media is cheaper. Other varieties like Xubuntu will still fit on a CD.

I use Unetbootin to make my Live USB sticks. Unetbootin will run on Windows/Mac/Linux.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

As mentioned above, having multiple DEs is possible but you will end up with a confusing amount of clutter and redundant programs.

---

### Post by ChaoticFlounder on 2015-01-25
All,

Thanks for the help here.  I have installed Kubuntu 14.04 over my "vanilla" Ubuntu 14.04 installation and hopefully will never have to go back.  So far, it has absolutely blown me away.  Anyways, just wanted to say thank you for everyone's help on this and being patient with me and all my questions! :)

C

---

