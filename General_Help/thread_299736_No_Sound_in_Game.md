---
title: "No Sound in Game"
date: 2006-11-14
forum: General Help
---

### Post by thecynicality on 2006-11-14
My sound works fine for the most part, it works on the desktop and for the internet and in some games, but when i try to play tc:e i have no sound in the game. I've tried a few things that people suggested like:

```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

```

sudo killall artsd 
sudo killall esd
```

```
/etc/init.d/alsasound restart
```

I also tried reinstalling alsa but no improvement.

Does anybody have any idea as to what i should do?

---

### Post by thecynicality on 2006-11-14
Anybody? This is really bugging me.

---

### Post by CatKiller on 2006-11-15
> **thecynicality said:**
> My sound works fine for the most part, it works on the desktop and for the internet and in some games, but when i try to play tc:e i have no sound in the game. I've tried a few things that people suggested like:

```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```


I don't think you want to do the second echo. And I believe this method will only work if you have the alsa-oss (?) package installed. I haven't used Enemy Territory, but I have used the first echo command you've got to get sound in RtCW, which I'd imagine is similar enough.

You're probably going to have more luck in the Gaming forum than the General one.

---

