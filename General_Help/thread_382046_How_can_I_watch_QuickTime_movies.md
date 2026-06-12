---
title: "How can I watch QuickTime movies?"
date: 2007-03-11
forum: General Help
---

### Post by jincast90 on 2007-03-11
Hello. I was looking around Apple's homepage today, but I found out I could not view the videos on their homepage. Can anyone tell me how to get this working?

---

### Post by IcemanV9 on 2007-03-11
You need to install mozilla-mplayer (mplayer-plugin for mozilla) to view QuickTime movies from Apple's website.

```
sudo aptitude install mozilla-mplayer
```

---

### Post by xopher on 2007-03-11
mplayer will play the videos just fine. You can install the mplayer plugin for firefox to get the videos to play in the browser.

apt-cache search mplayer to find out what the correct name for the plugin is ;)

Edit: seems like Iceman beat me to it. :)

---

### Post by jincast90 on 2007-03-11
Ok. I did a sudo aptitude install mplayer mozilla-mplayer

But the movies still won't work. So what is wrong now?

---

### Post by Tobster on 2007-03-11
Automatix is the best way the web site down at the moment but if you go on there there a link to a Wiki page that allows you to download the software, which provides you with all the media support you need.

If you own a version of Windows or Mac OS then you meet the legal requirements :)

[http://www.getautomatix.com/](http://www.getautomatix.com/) 

Thanks 

Toby

---

### Post by Tobster on 2007-03-11
The way the dudes above told ya will not work because it does not include the codecs do  it useing Automatix see my other post,

Toby

---

### Post by IcemanV9 on 2007-03-11
Ah. Yes. Forgot to mention about installing w32codecs stuff.

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

---

### Post by jincast90 on 2007-03-12
> **IcemanV9 said:**
> Ah. Yes. Forgot to mention about installing w32codecs stuff.

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

Ok, I did this. But it still dosn't work. I now have this installed including mplayer and mozilla-mplayer. I was thinking maybe it is because totem is set to play the movies in my browser, and not mplayer. I get the error seen on the picture when trying to play the movie.

---

### Post by bollix47 on 2007-03-12
With Firefox closed you could remove the totem plugins.

```
sudo rm /usr/lib/firefox/plugins/libtot*
```

---

### Post by Detonate on 2007-03-12
And delete the pluginreg.dat file from your /home/username/.mozilla/firefox directory before opening firefox.

---

### Post by IcemanV9 on 2007-03-12
I used this [[COLOR="Orange"]wiki[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats") on multimedia stuff when I installed mplayer last summer (2006). Totem did not work well for me, either.

---

### Post by strabes on 2007-03-12
Totem is a really bad media player. Its mozilla plugins are even worse.

---

### Post by mrmonday on 2007-03-12
Try this link:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I did it and quicktime movies work fine. Hope this helps.

---

### Post by hapablap on 2007-03-14
Anyone know how to get quicktime working with opera? 
Thanks.

---

