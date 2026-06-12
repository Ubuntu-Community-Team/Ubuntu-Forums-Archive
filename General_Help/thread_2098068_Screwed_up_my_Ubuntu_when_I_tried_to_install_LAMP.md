---
title: "Screwed up my Ubuntu when I tried to install LAMP"
date: 2012-12-25
forum: General Help
---

### Post by HunterDX77M on 2012-12-25
I was trying to install Lamp so that I could practice PHP on Ubuntu. I went to this site:

[Install lamp in one command]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/")

I only made it up to the second step or so. When I ran tasksel, I *only* selected Lamp from the menu and continued. While it was installing stuff, I noticed that it began uninstalling things like my games and my browser. I thought that it was about uninstall everything and only have Lamp installed so I panicked and did a hard shutdown in the middle of the setup. **Now when I try to run Ubuntu from the boot menu, all I get is a black screen.**

I am dual booting 12.04 and Windows XP. Windows seems to work just fine.

Is there anyway to recover my Ubuntu? I can still access the command line on the blank screen (Ctrl + Alt + F2) so I still do command line things, but I'm not sure what I can do. As far as I can see, my documents are still there.

Can anyone help me out here?

---

### Post by steeldriver on 2012-12-25
Oh dear :(

I guess you didn't read ANY of the comments on that link which basically tell you NOT to use tasksel (I'd suggest using [FONT=Courier New]sudo apt-get install lamp^[/FONT] instead - it worked painlessly for me on a recent 12.04 Server install)

> Tasksel will wipe out  critical components if you are not careful and the UI is a bit confusing  (e.g., unchecking a box means marking the component for removal).However if you can login at the virtual terminal (Ctrl + Alt + F2) then I *think* you should be able to get the desktop back with

```
sudo apt-get install --reinstall ubuntu-desktop
```

Alternatively, you should be able to run tasksel in curses mode either from the VT (using sudo) or from the recovery console - I just tried it on an old laptop that I have a homebrew Debian / Enlightenment setup - and reselect the packages you deselected previously

Good luck and let us know how it goes!

---

### Post by Mopar1973Man on 2012-12-25
I typically use Synaptic package manager to do my installing. 

As for fixing I would wait for grub and the try recovery mode.

---

### Post by HunterDX77M on 2012-12-25
> **steeldriver said:**
> 
However if you can login at the virtual terminal (Ctrl + Alt + F2) then I *think* you should be able to get the desktop back with

```
sudo apt-get install --reinstall ubuntu-desktop
```Good luck and let us know how it goes!

THANKS!!! I was able to log back into Ubuntu and all my things are still here (mostly). It looks like I'll have to re-install a few programs before I'm back to normal.

One problem I'm still having though is that the splash menu (when it's loading Ubuntu) is still completely black. **How can I get the old boot splash screen back **(or a new one):

[Here's an image of a splash screen if you're not sure what I'm talking about.]("http://1.bp.blogspot.com/_4B7ZWQHqMpk/TMcEEwqP88I/AAAAAAAAAEc/uVUzQyc32Ik/s1600/boot1.png")

If I'm anything, it's a positive thinker. This experience has really opened my eyes to my own stupidity and at least I've learned a few new things that I didn't know before.

---

### Post by steeldriver on 2012-12-26
Hmm... well sorry it didn't get everything back

FWIW I found this blog that suggests it's a problem with recommend packages - I can't say I really understand it, I guess the point is that 'dependencies' has a special meaning for a meta-package like ubuntu-desktop **IF YOU WANT TO GIVE THIS A TRY I STRONGLY ADVISE YOU TO BACK UP ANY IMPORTANT DATA FIRST**

[http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/ ]("http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/")

To test it, I tried to recreate your situation on a 'disposable' 12.04 Server box by first installing (using apt-get) ubuntu-desktop, then deselecting it (using tasksel), then reinstalling it (apt-get install --reinstall ubuntu-desktop). I then ran a slightly different version of the command suggested in the blog (basically just a more modern syntax):

```
$ while read -r pkg; do [ -z "$pkg" ] || sudo apt-get install --reinstall --install-recommends --yes "$pkg"; done < <(apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}')
```Nothing bad seemed to happen, as far as I can tell it basically just reinstalled all the desktop packages including any recommended ones - but use at your own risk!

---

