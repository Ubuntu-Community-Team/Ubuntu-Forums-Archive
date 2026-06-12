---
title: "Migrate from 18.04 to xfce?"
date: 2020-02-08
forum: General Help
---

### Post by Dan_Bowser on 2020-02-08
Hello,

I have ubuntu installed now (18.04) but I'd like to use xfce (xubuntu?) instead.

Since I just blew up my OS by following random instructions on websites the other day I thought I should ask about a good way to do this before I do it.

I want to just add a PPA and upgrade into the desktop environment (I think that was how I did it before but that was a few years ago.)

I can just run,

```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.15
sudo apt-get update
sudo apt-get dist-upgrade
```

Regards,

---

### Post by Frogs Hair on 2020-02-08
When I used xfce I added the ppa after the desktop environment. This will give you two file managers and I suggest you use thunar because nautilus handles the desktop differently. 

```
sudo apt install xfce4
``` ```
sudo apt update 
``` If you want some extras. ```
sudo apt install xfce4-goodies
```

---

### Post by Impavidus on 2020-02-08
There's no need for PPAs as all Xubuntu stuff is in the official repositories. Make sure the universe repository is enabled. Then install the package. For the basic xfce stuff install the package xfce4. If you want the full xubuntu desktop, install xubuntu-desktop. That will however give you a lot of duplicate stuff and it's hard to clean that up, so in that case a clean install of xubuntu might be better. Log out, select the xfce session and log back in.

---

### Post by vanadium on 2020-02-08
I ran Ubuntu Desktop and Xubuntu desktop besides each other without any problems, i.e., installing the full xubuntu-desktop on an Ubuntu. I subsequently removed Xubuntu again, but kept the Plymouth boot screen of Xubuntu because I find it a lot nicer than the bright pink of Ubuntu :) Avoid using third party repositories, especially for your base system.

---

### Post by Dan_Bowser on 2020-02-09
I ran,

```
sudo apt install xfce4
sudo apt update
sudo apt install xfce4-goodies









```

and restarted the PC.

The desktop environment is unchanged.

All that seems to have happened is it took longer to boot.

I fished around the log-in screen for a setting to toggle but I found none.

---

### Post by hk42 on 2020-02-09
The option to choose the desktop manager is not offered at first boot.
But when I logout from gnome I can choose:
To log in as another user
To change manager between :
Ubuntu
Ubuntu on wayland
Kodi
XFCE
The menu is rather ugly I have to click on a quite small icon.
Beware if you have ubuntu as default when you try to install something in XFCE 
you are not asked for your password and it doesn't work.

---

### Post by Frogs Hair on 2020-02-09
> **Dan_Bowser said:**
> I ran,

```
sudo apt install xfce4
sudo apt update
sudo apt install xfce4-goodies


```

and restarted the PC.

The desktop environment is unchanged.

All that seems to have happened is it took longer to boot.

I fished around the log-in screen for a setting to toggle but I found none.

It could because gnome uses GDM instead of Light DM. The entire Xubuntu Desktop environment installation would have offered that option , but includes many more packages.

---

### Post by Dan_Bowser on 2020-02-09
O.K. there's a gear in the log-in screen if you click on it there's a toggle you can set to swap between environments.

It didn't install all the accessories it had before. There should be a media player and a picture viewer/manager.

Also, there's no whisker menu... It looks like the version is older(?); it says I've 4.12 and the current version is 4.15.

Ah,  it would have been better to just install xubuntu at the start I think, too bad I couldn't get the iso file to boot from USB.

Is there an easy way to fix this?

---

### Post by mörgæs on 2020-02-09
If you consider a clean install of Xubuntu I recommend 19.10 over 18.04. 

How did you create the USB stick?

---

### Post by Impavidus on 2020-02-09
> **Dan_Bowser said:**
> 
Also, there's no whisker menu... It looks like the version is older(?); it says I've 4.12 and the current version is 4.15.

4.12 is the right version for 18.04. Xubuntu 19.10 uses xfce 4.14. For most software the version is frozen shortly before release of Ubuntu/Xubuntu. There are some exceptions and you do get the important bugfixes backported. I don't think xfce development is so fast that you should care.

---

### Post by Dan_Bowser on 2020-02-09
I used the rufas program that the ubuntu install section recommended

---

### Post by Dan_Bowser on 2020-02-09
I did,

```
sudo apt-get remove xfce4
```

Someone suggested using xubuntu-desktop so I ran,

```
sudo apt-get install xubuntu-desktop^
```

(I got the specific code from [https://askubuntu.com/questions/65861/how-to-i-change-from-ubuntu-to-xubuntu](https://askubuntu.com/questions/65861/how-to-i-change-from-ubuntu-to-xubuntu))

The install is asking me if I want gdm3 or lightdm. I should pick lightdm?

---

### Post by Frogs Hair on 2020-02-09
> [COLOR=#000000]I should pick lightdm?[/COLOR]



Yes, that will give you a session selection.

---

### Post by Holger_Gehrke on 2020-02-09
The whisker-menu is a plugin that gets installed as a dependency of xfce4-goodies. The default configuration of the xfce4 package sets up the older applications-menu while the xubuntu-desktop comes with a configuration that does set up the whisker-menu. You can add the whisker-menu and remove the old menu in the panel settings (right-click on the panel, select panel, panel settings).

Holger

---

### Post by Dan_Bowser on 2020-02-09
O.K. it looks like everything's set up pretty good. 

It looks like I can force the OS to upgrade to 19.10 if I want. What kind of reason is there to do that though? Also is there a down side? I guess other than I'll have to upgrade a new version sooner than if I use the LTS version I've got now.

---

### Post by mörgæs on 2020-02-10
If you have 18.04 in good shape you could also keep it. Security related bugs are fixed but except from the browser all software packages (Gimp, Libreoffice, mediaplayers, ...) are around two years old.

Don't upgrade. When you some day want a new version (19.10 or 20.04) it's better to do a fresh install.

---

### Post by dustyt on 2020-02-10
I also used Rufus to make all my usb's to test drive a bunch of distros and flavors of distros.

I had no issue booting the Xubuntu live usb.

As someone else suggested, I too prefer a fresh install to messing around. I think I had Ubuntu once a long time ago that I added KDE to so I could play around with that environment, because I liked it, but at the time I had read some rumors it could be buggy. Otherwise I have always preferred to test drive things via live and then do a fresh install vs adding or upgrading.

With this in mind, since my daughter's laptop had a huge drive, upon install I decided to make another partition /storage and thought I would test that as one of multiple places to save another copy of things she would want to keep and have on her fresh install next time like documents and so forth. I'm going to copy them elsewhere too. I'll do a clean install and then mount that partition again as /storage and see how that goes. If the drive were twice the size I might would have left some space for trying a clean install of the next version while keeping the old one around for a while just in case...

Too bad laptops don't come with multiple internal drive bays. I was just saying this the other day when I was talking to someone about how most laptops don't have a cd/dvd writer anymore, too bad that space isn't an extra drive bay lol...

---

