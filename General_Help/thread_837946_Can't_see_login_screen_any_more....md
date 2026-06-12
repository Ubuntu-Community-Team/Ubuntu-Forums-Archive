---
title: "Can't see login screen any more..."
date: 2008-06-23
forum: General Help
---

### Post by Erik765 on 2008-06-23
Hey there!
I've just figured out how to get my monitor to handle 1280x1024 by running the good 'ol sudo dpkg-reconfigure -phigh xserver-xorg command and selecting that resolution from it. (I have a 32" monitor so, getting this was a challenge).
This monitor will only do that res at 60hz.

I've alwasy wondered why, in the monitor & display - system settings and other places, it says a completely different refresh rate than what it's actually pushing. I had to select something like 53hz or something, but my monitor is getting 60hz.

So, I need to get my login screen to show up at either 1024x768 again, or 1280x1024 at 60hz. I can't tell what it's getting at all.

How do I specify 60hz in xorg.conf when I don't really know if it's going to be 60hz because it's not in the gui setting that I chose.

I'm doing a blind login here.

I can post my before and after xorg.conf files if needed.

Any ideas?

---

### Post by fooman on 2008-06-23
have you tried using *startup manager*?  it has settings for changing the login screen's resolution...not sure about the refresh rate:

```
sudo apt-get install startupmanager
```

---

### Post by Zorael on 2008-06-23
You're using an Nvidia card, correct? There's a bug in their drivers that make them incorrectly report refresh rates if you haven't explicitly disabled TwinView support. If you could properly log in and everything worked before tinkering with your xorg.conf, just revert to your backup.

See if your monitor has some way of displaying the current refresh rate. Trust in its numbers, instead.

---

### Post by Erik765 on 2008-06-23
> have you tried using startup manager?

I just installed that and I didn't see anywhere to adjust login settings. Looks like it's mostly for grub?

> You're using an Nvidia card, correct?

Yes

> if you haven't explicitly disabled TwinView support.

So, is there a way I can do that then?

> If you could properly log in and everything worked before tinkering with your xorg.conf, just revert to your backup.

If I did that then I wouldn't have 1280x1024 any more!

---

### Post by Zorael on 2008-06-23
> **Erik765 said:**
> If I did that then I wouldn't have 1280x1024 any more!
Your post seemed to suggest that you'd done something; "can post before and after xorg.conf". :> For the sake of it, please post those.


> **Erik765 said:**
> So, is there a way I can *[disable TwinView]* then?
```
$ sudo nvidia-xconfig --no-twinview
```
TwinView is pretty nice, though, and I don't think this will fix your problems. It will/should make it correctly display your current refresh rate, but that is merely a display error to begin with. To revert:
```
$ sudo nvidia-xconfig --twinview
```

---

