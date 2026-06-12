---
title: "dvd"
date: 2004-11-06
forum: General Help
---

### Post by bluefuse on 2004-11-06
I am currently downloading Ubuntu 4.10 "The Warty Warthog Release" my question is this I have a HP Pavilion N5340, it has a dvd player, will I have to find codec's to play dvd's or is this software default.

I am thinking about converting all my home pc's to ubuntu
but I will make that decision upon likes and dislikes.

---

### Post by im_ka on 2004-11-06
you won't have the codecs to play encoded dvd's by default.

BUT all you need to do is to add a new source (christian marillat's multimedia repository) to apt, and install mplayer which will give you the necessary codecs, and not only for dvd's.
```
sudo gedit /etc/apt/sources.list
```
add this line:
```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```
run
```
sudo apt-get update
```

and you'll be able to install mplayer via synaptic.

hth

---

### Post by bluefuse on 2004-11-06
thanks

---

### Post by Verlager on 2004-11-06
[QUOTE=bluefuse]I am currently downloading Ubuntu 4.10 "The Warty Warthog Release" my question is this I have a HP Pavilion N5340, it has a dvd player, will I have to find codec's to play dvd's or is this software default.

I am thinking about converting all my home pc's to ubuntu
but I will make that decision upon likes and dislikes.[/QUOTE] As an enthusiastic new  ubuntu user, I was very pleased to install both videolan (VLC) and Mplayer. (What a break from Libranet 2.8.1, my main Linux.) And now I can play DVDs, mpgs, 'most everything. But, I don't think I'm going to be able to rip DVDs in Linux as easily as I could with WinXpro's freeware like DvdDecrypter and DvdShrink. So I view the Linux multimedia apps as a sickly little brother versions of Windows MM counterparts. 

That said, I like the option of being able to have more choices in managing multi-media; I don't _have_ to use Windows to create mp3s or to watch DVD's, or to burn CD's.

---

### Post by im_ka on 2004-11-06
[QUOTE=Verlager]As an enthusiastic new  ubuntu user, I was very pleased to install both videolan (VLC) and Mplayer. (What a break from Libranet 2.8.1, my main Linux.) And now I can play DVDs, mpgs, 'most everything. But, I don't think I'm going to be able to rip DVDs in Linux as easily as I could with WinXpro's freeware like DvdDecrypter and DvdShrink. So I view the Linux multimedia apps as a sickly little brother versions of Windows MM counterparts. 

That said, I like the option of being able to have more choices in managing multi-media; I don't _have_ to use Windows to create mp3s or to watch DVD's, or to burn CD's.[/QUOTE]

dvd ripping is the only area i've found linux being behind. you can do it, but imho it takes too much time to set it up... i have to use my gf's laptop for that :(

---

### Post by NemoTheLobster on 2004-11-13
If you can get dvd::rip installed, it works great for ripping & converting DVD's.

---

### Post by Marauder1 on 2004-11-13
Can we just add codecs and plugins for totem or
is it better to un-install it and grab mplayer ?
Which is better mplayer or xine ?
Why would the ubuntu guys install something
that no one will use ?

I know it's a lot of questions but it's the only thing
missing on my system right now, a good movie player.
I tried totem on some movies but it's whatever they 
fail to open or i can only hear the sound.

TIA.

---

### Post by HiddenWolf on 2004-11-13
[QUOTE=im_ka]dvd ripping is the only area i've found linux being behind. you can do it, but imho it takes too much time to set it up... i have to use my gf's laptop for that :([/QUOTE]

Games, ugh!

And I still have to see a program that can shoot Nero out of the water on linux.

---

### Post by duff on 2004-11-13
[QUOTE=Marauder1]Can we just add codecs and plugins for totem or
is it better to un-install it and grab mplayer ?
Which is better mplayer or xine ?
Why would the ubuntu guys install something
that no one will use ?
[/QUOTE]

It's because the default totem uses gstreamer as a backend.  Most of your questions can be answered in the wiki:

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

As far as which is better, I find xine to have better DVD support and mplayer better support for most video codecs.  I'm pretty sure mplayer has played everything I've ever thrown at it.  Plus there's mplayerplug-in to run mplayer from firefox, so the trailers at apple.com work.

---

### Post by Marauder1 on 2004-11-14
Thanks Duff for that link, it answered all my questions ...
So i will try totem for dvd and mplayer for video.
As far as video plugin for firefox maybe i will later try
mplayer-plugin.

Cheers 
 \\:D/

---

### Post by duff on 2004-11-14
[QUOTE=Marauder1]As far as video plugin for firefox maybe i will later try
mplayer-plugin./[/QUOTE]
That works great, too.  Just remember to add the multiverse repos to your source list...I don't think that's mentioned in the wiki (or I just missed it).  I use it for the trailers on apple.com, or listening to Sirius radio online.

---

### Post by scoon on 2004-11-15
[QUOTE=NemoTheLobster]If you can get dvd::rip installed, it works great for ripping & converting DVD's.[/QUOTE]

Hey there, 

The easiest way I have found is using dvdbackup and mkisofs and growisofs.  If the dvd needs to be compressed then dvdshrink version 2.3 works with wine perfectly.  

scoon

---

### Post by UnHoly on 2004-11-15
I think as Linux gains popularity Games will be a non issue, even know with transGaming Cedega (which has a free demo that u can download right now) you can play hundreds of your windows games, plus, you could always go to tuxgames.com and get about sventy boxed games just for Linux like Doom 3, MOH: Allied assult, Never winter nights, Unreal 2004 and so on.

---

### Post by Marauder1 on 2004-11-16
Thanks duff took note of that !!!
By the way i had to flunk totem, dont like it
and the wiki suggest xine.
So i installed xine and everything is perfect !!!
Next step is mplayer-plugin.   8)

---

### Post by mr_ed on 2004-11-16
[QUOTE=NemoTheLobster]If you can get dvd::rip installed, it works great for ripping & converting DVD's.[/QUOTE]

But can you shrink them like DvdShrink in Windows?

AFAICT, dvd::rip only lets you have the unmodified DVD, or convert to DivX, not "shrink" it to single-layer DVD size.

---

### Post by dubdubdub on 2004-11-17
[QUOTE=NemoTheLobster]If you can get dvd::rip installed, it works great for ripping & converting DVD's.[/QUOTE]

I got DVD rip to work, but I am a moron and can't figure out how to use it. Like stated before, Windows has such easy ways to rip dvds. Its almost easier to boot back into xp and rip.

Anyone have a little tutorial on DVD:Rip i can read?

---

### Post by zenwhen on 2004-11-17
If you are wanting to make backups of DVD's you could use this:

[http://zenhardwhere.com/index.php?p=13](http://zenhardwhere.com/index.php?p=13)

---

