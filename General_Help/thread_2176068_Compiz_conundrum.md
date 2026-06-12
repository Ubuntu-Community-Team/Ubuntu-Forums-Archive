---
title: "Compiz conundrum"
date: 2013-09-22
forum: General Help
---

### Post by jaedin2 on 2013-09-22
So, I go into the terminal and type "compiz" and this happens:

compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x15800090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Starting gtk-window-decorator

What do I do? I'm not going to file a bug of course because that takes too long. But when this happened, my side bar dissapeared. Help me!!

---

### Post by stinkeye on 2013-09-22
What ubuntu release are you using?
```
cat /etc/lsb-release
```

What desktop session are you running?
```
echo $DESKTOP_SESSION
```

What gfx card and driver are you using?
```
lspci -nnk | grep -iA2 vga
```

Why are you entering the command "compiz" in the terminal?

---

### Post by gdesilva on 2013-09-22
I presume that you want to have effects such as Compiz Cube and Rotate Cube?? I do not use Unity interface but as far as I know if you are running Unity then you cannot use Cube, Rotate Cube features. You will have to disable Unity settings in Compiz first. If you disable Unity features then of course you will loose the side bar etc. If you are not interested in Unity then you can login with the xfce desktop and tweak Compiz settings to get the Cube going (which is what I have done). A good tutorial to get Compiz to auto start from xfce login is given here [https://wiki.archlinux.org/index.php/Compiz](https://wiki.archlinux.org/index.php/Compiz)

---

### Post by stinkeye on 2013-09-22
> **gdesilva said:**
> I presume that you want to have effects such as Compiz Cube and Rotate Cube?? I do not use Unity interface but as far as I know if you are running Unity then you cannot use Cube, Rotate Cube features. You will have to disable Unity settings in Compiz first. If you disable Unity features then of course you will loose the side bar etc. If you are not interested in Unity then you can login with the xfce desktop and tweak Compiz settings to get the Cube going (which is what I have done). A good tutorial to get Compiz to auto start from xfce login is given here [https://wiki.archlinux.org/index.php/Compiz](https://wiki.archlinux.org/index.php/Compiz)
The cube works just the same in unity as it does in xfce.
You do not have to disable the unity plugin.

---

### Post by gdesilva on 2013-09-22
@stinkeye, thanks for the clarification. I did try using Compiz with earlier versions of Unity and gave up the idea of getting the cube to work - not have been an Unity user for a long time now!

---

### Post by stinkeye on 2013-09-22
> **gdesilva said:**
> @stinkeye, thanks for the clarification. I did try using Compiz with earlier versions of Unity and gave up the idea of getting the cube to work - not have been an Unity user for a long time now!

Yeah the cube has always worked but was problematic as sometimes compiz would not reload
properly after changing some ccsm settings.
Windows would also flash on rotate.
13.04 is a lot better though and the cube is a lot easier to set.

---

