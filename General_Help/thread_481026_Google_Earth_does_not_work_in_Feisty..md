---
title: "Google Earth does not work in Feisty."
date: 2007-06-22
forum: General Help
---

### Post by joe.turion64x2 on 2007-06-22
Hello everybody.

Today I installed Google Earth in my Ubuntu 7.04 system (32 bits). I installed through Synaptic (from Medibuntu) but can not get it running. Or course I accepted the EULA but when I launch it a window appears saying it is initializing but nothing else happens in a long while, so I kill the process. I have tried with Beryl disabled as well.

Do I have to wait a really long time for Google Earth to start? or, are there known issues with that software?

Thanks.
Joe.

---

### Post by swisscow on 2007-06-22
No you don't have to wait too long and yes it has hung.

I have found that if you have an ATI graphics card (I have the X300) and you are using either Beryl through the radeon drivers and AIGLX or the fglrx drivers through XGL, GoogleEarth just hangs. I cannot (and I am not saying this is true for all ATI cards) get both Beryl and GoogleEarth to work - for me it's one or the other.

I chose GoogleEarth because I live near the Alps and looking at the mountains and places I want to visit is more fun than watching a cube making me dizzy;)

I have just the fglrx drivers installed (no Beryl, XGL etc) and GoogleEarth runs just fine. I downloaded my version of GoogleEarth from the website and installed it using:

```
sudo ./GoogleEarthLinux.bin
```

though I think (not sure) that
```

su ./GoogleEarthLinux.bin
```

works as well

Hope this helps you solve your problem.

---

### Post by dizee on 2007-06-22
Try using it without XGL or AIGLX, Google earth hangs when I try to use it in an XGL session but loads fine in a standard GNOME or KDE session.

Even if you disable Beryl in an XGL session it doesn't work you need to log out and log back in under a different session.

I'm pretty sure this is a bug. I remember seeing workarounds for it here but haven't tried them myself.

---

### Post by walkerk on 2007-06-22
works fine for me while running aiglx.. i downloaded the .bin from google.com..

---

### Post by dizee on 2007-06-22
Yeah, as I understand it there are problems with OpenGL programs and XGL, though they work fine with aiglx. Unfortunately with an ATi card aiglx is not always an option.

Some ideas here [http://ubuntuforums.org/showthread.php?t=354956&highlight=google+earth+xgl](http://ubuntuforums.org/showthread.php?t=354956&highlight=google+earth+xgl)

Edit - got it working by using  
```
DISPLAY=:0 /usr/local/google-earth/googleearth
```
Replace "/usr/local/..." with the path where google earth is installed. However with beryl as the window manager there are no window borders drawn so you need to exit through the file menu, though the program seems to work well otherwise.

---

### Post by joe.turion64x2 on 2007-06-22
Thanks for the replies, I guess I will give up using Google Earth in my laptop (ATI) and will use it in my desktop (NVIDIA) instead. Anyway I don't use Google Earth that much.

Joe.

---

