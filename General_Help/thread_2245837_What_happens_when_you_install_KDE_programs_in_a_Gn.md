---
title: "What happens when you install KDE programs in a Gnome DE? (Also, photo management.)"
date: 2014-09-26
forum: General Help
---

### Post by AwaitingUserInput on 2014-09-26
I am trying to find a good photo manager for my system. I want to be able to tag photos and then search for them with a combination of tags. Example: If I select tags "family," and "vacation" then it will return only pictures of family vacations, but not pictures of my family at home.

So far I have not had luck with any of the Gnome managers.

**Shotwell** does not allow for complex searching / filtering of tags.

**F-Spot** crashes on startup and there has not been an update since 2010, so I assume that project is dead.

[B]KDE
[/B]A lot of articles say Digi Kam is very powerful and I would like to try that one. All these articles, though say that it's for the KDE environment and that it will bloat and slow down my Gnome system because of all the dependencies. My question is would this bloat/slowdown only happen when I am actually using DigiKam, or would it be more of a "global" dragging down of my system? I have a pretty modern computer, so I'm not sure if I should worry about this.

The only other photomanager that I have used that I like was actually a free one put out by Microsoft, and I plan to make a Windows 7 virtual machine for other reasons, so maybe I should just use the Microsoft product?

I haven't tried Picasa for linux because I don't want to upload my photos online and am concerned about sharing even more personal date with Google than I already do.

I'm open to any advice. Right now I'm leaning towards DigiKam, but again, the KDE dependencies concern me.

---

### Post by vasa1 on 2014-09-26
> **AwaitingUserInput said:**
> ...
I'm open to any advice. Right now I'm leaning towards DigiKam, but again, the KDE dependencies concern me.
If you have a decent machine, it shouldn't be a problem.

---

### Post by ibjsb4 on 2014-09-26
It does have the kde bloat to it.  You can see it, before you install by using synaptic package manager.
[ATTACH=CONFIG]256714[/ATTACH]
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

So I went ahead and installed it on a dual core virtual machine (running gnome) with 2G of ram. Played with it for five minutes and found it to be fast on my system.

---

### Post by AwaitingUserInput on 2014-09-26
Thanks ibjsb4!

Would it be accurate to say that all the extra libraries and stuff do not consume resources unless I'm actually using Digikam? In other words, if I just start up my system, do they require any RAM or processing power, or do they just sit there dormant on the hard drive until needed by a KDE application?

---

### Post by ajgreeny on 2014-09-26
I have always installed digikam and k3b (and gthumb) in my gnome or xfce based OSs without any problems, and you are correct regarding the resource usage; ie, only when the application is in use.

Talking of gthumb, have you checked if that can deal with tags in the manner you want?  I don't know as I have not used tags for some time, since I was bitten by tags that I had added in application A which were not read and used by application B; most annoying, and I can't now even remember what application I used to add the tags.

---

### Post by ibjsb4 on 2014-09-26
At boot I see nothing kde.
[ATTACH=CONFIG]256723[/ATTACH]is booted
When I boot digi I see.
[ATTACH=CONFIG]256722[/ATTACH]
When I close it.
[ATTACH=CONFIG]256724[/ATTACH]

I think (like vasa1 said) you should be good.

edit
Just noticed ajgrenny is here too and ditto :)

---

### Post by SeijiSensei on 2014-09-26
> **AwaitingUserInput said:**
> Would it be accurate to say that all the extra libraries and stuff do not consume resources unless I'm actually using Digikam?

Yes.  Only when you load a KDE app do you also load the supporting libraries. 

However digikam has a lot of dependencies of its own.  I installed it just now on a fairly vanilla Kubuntu 14.04 system, and it brought in over thirty dependencies totalling about 220 MB.  On any modern system this is a trivial amount of storage.  If you have 4+ GB of physical memory, you shouldn't see any performance hits whatsoever.  I suspect that's true for a 2 GB system as well, but I'll let others chime in on that.

---

### Post by ajgreeny on 2014-09-27
Run command ```
apt-cache depends digikam
``` and you'll see all the dependencies that digikam has; quite a lot, but it is a very good picture/photo manager so worth it in my opinion.

---

