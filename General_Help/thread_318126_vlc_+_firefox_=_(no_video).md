---
title: "vlc + firefox = (no video)"
date: 2006-12-13
forum: General Help
---

### Post by Choad on 2006-12-13
i installed the mozilla vlc plugin through synaptic, and all i get is a thing saying (no video)

i searched and there were a few peoplw reporting the same thing, but no fixes as far as i could see...

---

### Post by Choad on 2006-12-13
bump

---

### Post by karlar on 2006-12-17
got the same problem. 

it seems like the vlc's mozilla plugin is not correct installed, dont response so any calls maked to it.

---

### Post by eallenjacobs on 2006-12-20
Experiencing same problem. Uninstalling vlc doesn't help either. Looking into it more

---

### Post by hanzomon4 on 2006-12-20
I've only been able to get mplayer-plugin to work(after much frustration)..... I tried vlc plugin awhile back.... never got it working, but considering that I use vlc for everything video related I'll see if I can get it to work.....

---

### Post by Choad on 2006-12-21
> **hanzomon4 said:**
> I've only been able to get mplayer-plugin to work(after much frustration)..... I tried vlc plugin awhile back.... never got it working, but considering that I use vlc for everything video related I'll see if I can get it to work.....
exactly, VLC is the best player in the world. i want to use it for everything! i think gnome should use vlc for **all** its programs instead of gstreamer.

---

### Post by Celil Rifat on 2006-12-21
I have the same problem. ](*,)

---

### Post by tenghoward on 2006-12-23
> **Choad said:**
> i installed the mozilla vlc plugin through synaptic, and all i get is a thing saying (no video)

i searched and there were a few peoplw reporting the same thing, but no fixes as far as i could see...

Run this in terminal.

```

sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils
```

Then restart computer.

Try to see if this works. Sorry I'm using mplayer plugins so can't help you much. :???: Read this off from Ubuntu wiki [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy").

Howard T.

---

### Post by xabbott on 2006-12-23
MIght want to try [this Firefox extension]("https://addons.mozilla.org/firefox/446/"). As for the VLC plugin itself. It's poor in both windows and linux atm.

I agree that the player is very nice though. I think the same issues that stop Ubuntu from including mp3 support installed by default is what stops them from including VLC.

Personally I think if all the codecs came installed Totem+gstreamer wouldn't really be that bad. Also I think Totem's ui is much more suited for Ubuntu. ;)

---

### Post by Azakus on 2006-12-23
Is totem's plugins also installed? They and VLC fight each other for control, so delet the totem plugins.

---

