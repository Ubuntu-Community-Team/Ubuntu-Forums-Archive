---
title: "No sound."
date: 2006-11-27
forum: General Help
---

### Post by tehhaxorr on 2006-11-27
After update from Dapper to Edgy i have no sound while logged in to Gnome. I have the startup sounds when i initially log in, but nothing after that.

My sound card is onboard an intel and it seems to be detected correctly.

If you need more info about my system just tell me the commands.

---

### Post by ReaderRat on 2006-11-27
Desktop or laptop (mobile)? Intel AC'97 or ICH6?

---

### Post by ReaderRat on 2006-11-27
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)

---

### Post by tehhaxorr on 2006-11-28
No luck with thoes guides. I found out some more about my problem though. When i start ubuntu sound is working, but only in the Right speaker (works with both in windows) and as soon as i open Volume Control sound ceases to function. I have no sound after that point using either OSS or ALSA options in "Sound devices" under Volume Control.


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ReaderRat on 2006-11-28
Well, AD198x sound is ICH7 (Intel). Do you have the alsa drivers installed?

---

### Post by tehhaxorr on 2006-11-28
> **ReaderRat said:**
> Well, AD198x sound is ICH7 (Intel). Do you have the alsa drivers installed?

Yes, i installed heaps of Alsa packages to make sure it was working. According to the Asus website (my motherboard manufacturer) it is a realtek soundcard. Maybe linux has detected the wrong card?

Asus sais it's an: ALC880/882/883

---

### Post by ReaderRat on 2006-11-28
> Maybe linux has detected the wrong card?
Do you have more than one sound card? 
I have the same sound on my laptop, and I had to use the Comprehensive Guide to get sound to work in Ubuntu. And it's still not that great.

---

### Post by therunnyman on 2006-11-28
Maybe give this a whirl...

Create a file in your home directory called .asoundrc

```
sudo gedit /home/(your user name)/.asoundrc
```

Paste the following into it:

```
pcm.!default {
type hw 
card 1 
}

ctl.!default { 
type hw 
card 1 
}
```

Save and reboot.

---

### Post by tehhaxorr on 2006-11-28
> **ReaderRat said:**
> Do you have more than one sound card? 
I have the same sound on my laptop, and I had to use the Comprehensive Guide to get sound to work in Ubuntu. And it's still not that great.

No just the one card, i am runing the ALC alsa drivers now and will post back when they are done.

---

### Post by tehhaxorr on 2006-11-28
> **ReaderRat said:**
> Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)

In that second link, how the hell did sourcs.list end up like that? that's an invalid format and it will just cause errors won't it.

---

### Post by halfvolle melk on 2006-11-28
> In that second link, how the hell did sourcs.list end up like that? that's an invalid format and it will just cause errors won't it.
Yes it will. I think Sef intended /etc/modules or something like that. Not sure.

---

### Post by ReaderRat on 2006-11-28
Whoops, looks like I didn't get the whole thread....only part of it. Sorry.

---

### Post by tehhaxorr on 2006-11-28
Will compiling my own kernel with ICH7 into it help at all? it looks like a big task for a beginner, but hell, i have nothing to loose.

---

### Post by therunnyman on 2006-11-28
Not even going to try an .asoundsrc file?  By the way, if the "card 1" part doesn't work, you can rewrite it with "card 0" or "card whatever".

Compiling a kernel is more fun, I grant you, but I may have given you a less drastic solution.

runny

---

### Post by tehhaxorr on 2006-11-28
> **therunnyman said:**
> Not even going to try an .asoundsrc file?  By the way, if the "card 1" part doesn't work, you can rewrite it with "card 0" or "card whatever".

Compiling a kernel is more fun, I grant you, but I may have given you a less drastic solution.

runny

I tried that yesterday, with no luck.i will change it so card0 and get back to you.

---

### Post by tehhaxorr on 2006-11-28
> **tehhaxorr said:**
> I tried that yesterday, with no luck.i will change it so card0 and get back to you.



No luck. I tested a few more distro's and the sound doesn't work on any of them. Maybe a newer kernel will have the updated drivers, or CVS alsa?

---

### Post by therunnyman on 2006-11-28
Gadzooks, friend!  I'm at a total loss, especially now that you've tried other distros to no avail...

Got US $15?  I'd nab a cheapo soundcard at the nearest electronics store; you might even get a nice soundcard off ebay for the same price.

Boy, that's annoying, isn't it?  I had a similar problem, but that file fixed it (or most of the problem, anyway).  If you pop over to alsa's website, info there might be of some help - that's where I found the .asoundrc info, and a bunch of other neat sound stuff.

Sorry I couldn't be of more help.

runny

---

### Post by tehhaxorr on 2006-11-29
> **therunnyman said:**
> Gadzooks, friend!  I'm at a total loss, especially now that you've tried other distros to no avail...

Got US $15?  I'd nab a cheapo soundcard at the nearest electronics store; you might even get a nice soundcard off ebay for the same price.

Boy, that's annoying, isn't it?  I had a similar problem, but that file fixed it (or most of the problem, anyway).  If you pop over to alsa's website, info there might be of some help - that's where I found the .asoundrc info, and a bunch of other neat sound stuff.

Sorry I couldn't be of more help.

runny

Looks like i am going to have to spend a fair chunk more than $15 mate, i record instruments on my PC. I got that particular board because of the low cost/high performance on board audio.

Thanks for the advice, i'll try alsa CVS to see if it is patched in new releases, or would it be suitable to use the Feisty kernel  or Alsa .deb? And if so, where can i find them?

---

