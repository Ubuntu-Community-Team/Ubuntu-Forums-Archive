---
title: "Ubuntu 10.04.4 - What Happens When Support Ends"
date: 2013-02-14
forum: General Help
---

### Post by Infamous Blob on 2013-02-14
Hi,
I'm an Ubuntu 10.04 user, and have been for the past year on/off (I started with Ubuntu 11.10, started using 10.04, switched to Fedora 17 for a bit, went back to 10.04 and then tried 12.04 but neither quite offered me what I wanted).
I've got very comfortable with my Gnome 2.30 desktop, Compiz 0.8.something e.c.t. and really don't want to upgrade to anything newer - 10.04 just works, nothing has ever broken or gone wrong and I think I can honestly say it's the best version of Ubuntu or indeed any distro I've ever used. I've also got it set up exactly as I like it which is another reason I don't want to switch.
Admittedly I'd be happier if I could get Steam to work and have a few newer bits and pieces, but to be honest they aren't really essential - I've got Windows for gaming.
Now with support ending in two months, I'm a little bit concerned, mainly because I don't know what going to happen? Will I still be able to access the software in the software centre without getting updates for that software, will I still get some updates (for Firefox for example)? I'm not against switching to third party ppas to get updates for important bits of software (like Firefox) or indeed just individually installing .debs.
So yeah, all guidance on what to do to lessen the impact of the end of support (whatever it may be) appreciated :) Updating to 12.04 is out of the question, although I wouldn't mind switching to MATE under the condition there's a fully compatible and integrated version of compiz (0.8) to go along with it (Compiz is a very important part of my work-flow).
Thanks

---

### Post by Bufeu on 2013-02-14
Read here: [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

---

### Post by Warren Hill on 2013-02-14
When 10.04 **desktop** support ends in a few weeks time (April) there will be no more development or bug fixes.  I do not think the repositories will be moved for some time as the **server** edition is still supported until 2015 and it uses the same repositories.

I would definitely recommend you either upgrade to 12.04 or switch to another distribution.

You may want to consider Xubuntu 12.04 it is a fully  supported version of Ubuntu, support till April 2017,  but has a lighter desktop so runs better on older hardware.  The download is here : [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

You can try the Xubuntu from a CD/DVD or USB stick before installing to see if you like it first,

Another option assuming **Unity **is the reason you don't want to upgrade to 12.04 would be to upgrade to 12.04 then change the desktop to Gnome Classic which feels a lot like Ubuntu was in 10.04; though not quite identical.

To do this open a terminal and enter

```
sudo apt-get install -y gnome-panel
```

Log out, select the circular icon next to the password entry box.  This allows you to change the desktop select "Gnome Classic" or "Gnome Classic (No Effects)" and log back in.

The Ubuntu download is here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by |{urse on 2013-02-14
The entire universe will explode!

---

### Post by snowpine on 2013-02-14
I predict it will take about 1 week for you to see Unity's superiority over the outdated Gnome 2 "desktop metaphor." A lot of people struggle with Unity because they simply haven't learned the keyboard shortcuts yet, here they are: [http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html](http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html)

Anyway if you've given Unity a fair shake and still prefer Gnome 2 (different strokes for different folks ;)), I can highly recommend Fuduntu: [http://www.fuduntu.org/](http://www.fuduntu.org/)

---

### Post by aspergerian on 2013-02-14
I too liked Ubuntu 10.04, tried 12.04 Unity, retreated to and am happy with Xubuntu 12.04.1. I even achieved a 10.04-like desktop [here]("http://ubuntuforums.org/showthread.php?t=2098800"), which fits my brain and my netbook quite nicely.

---

### Post by Yellow Pasque on 2013-02-14
> **snowpine said:**
> I predict it will take about 1 week for you to see Unity's superiority over the outdated Gnome 2 "desktop metaphor."

[RANT]Probably not. Some people ("desktop" users) don't like using an environment where a lot of design choices are made to accommodate for those with 100x100 pixel screens, especially when those choices make the environment unintuitive and more difficult to learn in the first place. Example: why do I need to memorize keyboard shortcuts for things I used to have inituitive GUI options for and that I could do faster with the mouse?[/RANT]

> will I still get some updates (for Firefox for example)? 
Technically, Lucid/10.04 Server will be supported for another two years, so it's possible (but I wouldn't hold my breath for anything other than serious bug/security fixes).

>  Will I still be able to access the software in the software center without getting updates for that software?
Yes.

So you really like Gnome2 and want compiz 0.8? I'm pretty sure that you can find distros that will allow you to use MATE with compiz 0.8 (check out Mint 12). I use Debian sid (AKA "unstable" even though it's surprisingly stable) and the xfce desktop. Debian sid still has compiz 0.8 in the repo and although I don't use compiz, I just installed compiz and it ran fine on xfce with a simple compiz --replace command.

---

