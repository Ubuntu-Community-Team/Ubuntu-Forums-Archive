---
title: "Can xfce4-screenshooter be run non-interactively?"
date: 2014-11-14
forum: General Help
---

### Post by vasa1 on 2014-11-14
I can use```
xfce4-screenshooter -s ~/Desktop -f
```or```
xfce4-screenshooter -s ~/Desktop -d 5 -f
```but even if the default name format is acceptable, I still have to press **enter** in a window to confirm the name and location. Can that be avoided?

---

### Post by Toz on 2014-11-14
Unfortunately no. It was available at one time but the developer removed it. See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-screenshooter/+bug/585478]("https://bugs.launchpad.net/ubuntu/+source/xfce4-screenshooter/+bug/585478").

However, the workaround listed in[ this thread]("http://forums.linuxmint.com/viewtopic.php?f=90&t=167208") by grizzler works fine.

---

### Post by vasa1 on 2014-11-14
> **Toz said:**
> Unfortunately no. It was available at one time but the developer removed it. See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-screenshooter/+bug/585478]("https://bugs.launchpad.net/ubuntu/+source/xfce4-screenshooter/+bug/585478").

However, the workaround listed in[ this thread]("http://forums.linuxmint.com/viewtopic.php?f=90&t=167208") by grizzler works fine.
That's brilliant! Instead of putting the script in */usr/local/bin*, I put it in *~/bin* and it seems to work from there as well.

Edit: another post in the same thread had links to various other ways of taking screenshots. [This one]("http://tips.webdesign10.com/how-to-take-a-screenshot-with-ubuntu-linux") looks at imagemagick's import.

---

### Post by Habitual on 2014-11-15
or (don't we love Linux for 'options'?)...
I mapped a command ```
**scrot -q 50 '/home/jj/Pictures/screenshots/PrintScreen_%m %d %T.png'**
``` to Print key

---

### Post by vasa1 on 2014-11-15
> **Habitual said:**
> or (don't we love Linux for 'options'?)...
I mapped a command ```
**scrot -q 50 '/home/jj/Pictures/screenshots/PrintScreen_%m %d %T.png'**
``` to Print key
[s]Scrot is the default tool in Lubuntu and I've been using scrot in Lubuntu 12.10, 13.04, 13.10, 14.04, and 14.10 very happily.

But, I replaced my 14.10 (in which scrot worked perfectly) with 14.04 (in which scrot had worked previously) by doing a clean install of 14.04. Then, when I ran scrot 
"nothing" happened
a few seconds later the RAM usage shot up from ~ 300-400 MB to ~ 3 GB
swap started being used
CPU was high in an erratic sort of way
everything else became sluggish
I could get out alive only by rebooting

This happened whether I ran scrot from my keyboard shortcuts set in Openbox rc.xml like this:
scrot -b ~/Desktop/%b%d::%H%M%S.png (plain PrntScrn)
or like this
scrot -u -b -d 5 ~/Desktop/%b%d::%H%M%S.png (Super+PrntScrn)

I figured *it's just me* and so I've reluctantly let scrot go for now.[/s]Scrot's working again.

---

### Post by pqwoerituytrueiwoq on 2014-11-15
> **vasa1 said:**
> That's brilliant! Instead of putting the script in */usr/local/bin*, I put it in *~/bin* and it seems to work from there as well.

Edit: another post in the same thread had links to various other ways of taking screenshots. [This one]("http://tips.webdesign10.com/how-to-take-a-screenshot-with-ubuntu-linux") looks at imagemagick's import./usr/local/bin exist for manual software installs
/bin exist for primary applications, ones essential for basic functionality, /usr/bin exist for install applications that were installed via deb files
while it will work in any of those locations that is the standard practice
on this note /sbin, /usr/sbin, and /usr/local/sbin all exist for the same reasons but are fore root user only applications

---

### Post by vasa1 on 2014-11-15
@pqwoerituytrueiwoq, true, but I put my stuff in ~/bin because there's only one folder to look after in terms of backing up and there's less chance of me damaging the system :)

---

### Post by HermanAB on 2014-11-16
I think the easiest way is with scrot and xbindkeys.

If you run scrot with no parameters, the result is time stamped screenshot file in the current directory, so you don't even have to read the man page of that one.

---

### Post by vasa1 on 2014-11-16
> **HermanAB said:**
> I think the easiest way is with scrot and xbindkeys.
...
Why xbindkeys? I've assigned an immediate screen capture to PrntScrn and a delayed one (of the active window) to Super+PrntScrn through rc.xml (Openbox).

BTW, I've reinstalled scrot and it's working just fine now!

---

### Post by HermanAB on 2014-11-16
rc.xml - Cool. Openbox is nice and simple.

---

