---
title: "Beryl Edgy Problem"
date: 2006-12-07
forum: General Help
---

### Post by feest on 2006-12-07
hi i've installed beryl and it works exept the window borders, they dont appear. how can i solfe this? the cube works fine etc. but there are no borders. how can i solve this?

---

### Post by endersshadow on 2006-12-07
Open up a terminal and type:

```
emerald &
```

Voila.

---

### Post by feest on 2006-12-08
thx but i already solved it :)

---

### Post by ingo on 2006-12-08
how? the same way? I'm still having teething problems with beryl :( and any advice would be greatly appreciated...

---

### Post by Get_Ya_Wicked_On on 2006-12-08
Beryl is really unpredictable (on XGL, more or less).

I remember the same thing happening to me at first.

And eventually it kind of "fixed" itself. It did all kinds of nonsense.

Thank god for AIGLX...

---

### Post by ingo on 2006-12-08
Hm, bear with me on this one, please...

What on earth is AIGLX? You got a good howto or summink like that? Any help greatly appreciated.

BTW, I'm running on Kubuntu.

Cheers

---

### Post by endersshadow on 2006-12-08
[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

Instructions differ between Dapper and Edgy, so choose wisely.

---

### Post by ingo on 2006-12-08
I keep on asking hoping to find a howto that works for me. I've got everything installed as instructed but when i switch to beryl not only do window borders all but disappear but the desktop stops responding. Fortunately I can go back to KDE windows manager using the beryl diamond thingy so I don't have to Ctrl Alt Backspace all the time...

Will bother the Kubuntu lot now since I know that KDE is not as forthcoming as Gnome when it comes to silly stuff like this :(

Thanks anyway

---

### Post by Get_Ya_Wicked_On on 2006-12-08
Go [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) there and see if your card is supported.

If it is, I would strongly reccommend uninstalling fglrx and 'enabling' the AIGLX that came with your computer. (assuming Edgy)

By the way, my card is [X300] is listed as experimental, but it works like a charm. So don't think it needs to be fully supported.

---

### Post by ingo on 2006-12-08
thanks for your continued efforts :) 

I've got an NVidia GeForce FX 5200 card (128MB) and am using the NVidia 1.0-9629 driver, so no ATI stuff

---

### Post by Get_Ya_Wicked_On on 2006-12-08
Ha, ha. I just realized I assumed you had an ATI card. My bad.

So, you need to go [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+with+beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+with+beryl) here (assuming ; ) that you have Edgy)

---

### Post by endersshadow on 2006-12-08
> **ingo said:**
> I keep on asking hoping to find a howto that works for me. I've got everything installed as instructed but when i switch to beryl not only do window borders all but disappear but the desktop stops responding. Fortunately I can go back to KDE windows manager using the beryl diamond thingy so I don't have to Ctrl Alt Backspace all the time...

Will bother the Kubuntu lot now since I know that KDE is not as forthcoming as Gnome when it comes to silly stuff like this :(

Thanks anyway

To start Beryl, use this command:

```
emerald --replace &
beryl &
```

Voila. Window borders.  Emerald == window borders :)

---

### Post by HighD on 2006-12-10
> **ingo said:**
> thanks for your continued efforts :) 

I've got an NVidia GeForce FX 5200 card (128MB) and am using the NVidia 1.0-9629 driver, so no ATI stuff

I got the same card! And I HAD the same problem, what did it for me was the following: 

I went to Beryl Settings Manager and disabled "Sync to VBlank" and "Slowness fix".

Restart and then try (from a terminal):

```


beryl-manager
```

Hope that helps!!

---

### Post by ingo on 2006-12-11
Ok, I've tried both endersshadow's and HighD's suggestions and sifted through the Kubuntu forum to no avail.

@ endersshadow - I typed your commands in and then tried to activate beryl in the beryl manager. Again, no borders, an unresponsive desktop and, perhaps the most interesting, "beryl" is not really selected in the beryl-manager (it doesn't have the stripes next to it). Hmm...

@HighD - disabled those two settings and nothing has changed :( Beryl manager does not show beryl as being properly selected (does not have the stripes next to it).

I am at my wits' end and will probably try a complete reinstall of all things beryl and try your suggestions anew.

---

### Post by HighD on 2006-12-11
> @HighD - Beryl manager does not show beryl as being properly selected (does not have the stripes next to it)

I do not quite understand what you mean by that, maybe it's because I use Gnome...but...have you tried upgrading to 0.1.3?? 

From  [http://blog.beryl-project.org/](http://blog.beryl-project.org/)

**"Beryl 0.1.3 marks the first release to include the KDE Window Decorator named Aquamarine..."**

Maybe that could help...

---

