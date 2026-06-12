---
title: "Muisc Player Problem.."
date: 2008-05-09
forum: General Help
---

### Post by k1ngb0b0 on 2008-05-09
Hello.  I have a strange problem and I figured this would be the best place to look for help.

I use Amarok to play music but it recently crashed.  After that it would not load.  I'd try everything I could think of, it just would not start up.  Eventually (after deleting the configuration files) and reinstalling I got it working again.

Well the same problem happened (I narrowed it down to ipods being disconnected).  The difference is this time it makes it so none of my music players work!

I've tried banshee, rhythmbox, exaile...They all load, they load my library, but they hang when I try to play a song.  Eventually I have to just manually close the program.  The sound in youtube also does not work.

The sound that does work:  game sound/music in world of warcraft (installing via wine) Last.FM as well as the start music (from a restart)


I'm using ubuntu Hardy Heron.


Anyone have any ideas about this?  It's really bothering me...

---

### Post by didooofidooo on 2008-05-09
I think that the problem is from your sound card configuration so try to reconfigure it and also re-install the Gstreamer
I hope that works

---

### Post by atomkarinca on 2008-05-09
> **k1ngb0b0 said:**
> Hello.  I have a strange problem and I figured this would be the best place to look for help.

I use Amarok to play music but it recently crashed.  After that it would not load.  I'd try everything I could think of, it just would not start up.  Eventually (after deleting the configuration files) and reinstalling I got it working again.

Well the same problem happened (I narrowed it down to ipods being disconnected).  The difference is this time it makes it so none of my music players work!

I've tried banshee, rhythmbox, exaile...They all load, they load my library, but they hang when I try to play a song.  Eventually I have to just manually close the program.  The sound in youtube also does not work.

The sound that does work:  game sound/music in world of warcraft (installing via wine) Last.FM as well as the start music (from a restart)


I'm using ubuntu Hardy Heron.


Anyone have any ideas about this?  It's really bothering me...

Open up a terminal (Applications > Accessories > Terminal) and run Amarok in it, type this:

```
amarok
```

Then paste the output here (if there are any).

---

### Post by k1ngb0b0 on 2008-05-09
@atomkarinca:

I tried that one time and I got no output whatso ever.  The terminal would hang there until I closed it.

Update:

Deleting the amarok config. folder and a system restart seems to have fixed it.  Everything is working fine now.

I think the problem has to do with ipods connecting to amarok, but I'm afraid to test it :-/ 

Anyone have any thoughts?

---

### Post by atomkarinca on 2008-05-09
It's most probably because it couldn't quit properly. Just deleting amarokrc file would be enough, I guess.

---

### Post by wabbster on 2008-05-09
I'm a newbie here, but I've been told that Amarok plays havoc when you're using GNOME because there's just too many dependencies, in the sense, you'll have to install KDE specific plugins and things like that... All this, assuming you're running GNOME.

I'd rather keep it simple and just use one music player. I use Exaile and it's nice, although I don't *have* an ipod to test if it works with it. ;)

Good luck,
Wabb.

---

### Post by k1ngb0b0 on 2008-05-10
To be honest I don't really want to use amarok, BECAUSE of the problems you're describing.

I've tried a couple gnome alternatives but none of them offer the number of features/functionality that amarok does :-/

---

### Post by atomkarinca on 2008-05-10
> **k1ngb0b0 said:**
> To be honest I don't really want to use amarok, BECAUSE of the problems you're describing.

I've tried a couple gnome alternatives but none of them offer the number of features/functionality that amarok does :-/

Exaile offers pretty much what Amarok does. You can also try Quod Libet, that's a nice one. My favorite is Mpd + Sonata, it's lightweight as hell and very pretty.

---

