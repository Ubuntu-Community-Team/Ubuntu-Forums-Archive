---
title: "Amarok losing sight of libgpod"
date: 2008-01-26
forum: General Help
---

### Post by ronniet on 2008-01-26
I have an 80gb *iPod Classic* (6G) so compiled *libgpod* to 0.6.0 to get the *iPod Classic* working with *Amarok* and it worked fine.

**Or so it seemed!**

If I have to reboot the computer *Amarok* seems to lose *libgpod 0.6.0* and I end up getting the dreaded 'no music' on my iPod. Only way to get it working again with the iPod is to:

```
sudo rm /usr/lib/libgpod.so.2
sudo rm /usr/lib/libgpod.so.3
```

then:

```
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
```

Then all is well with *libgpod* and *Amarok.*

**Is there a way to make this permanent so that I don't have to keep deleting and recreating the two libgpod.so.x files??**  :confused:

---

### Post by browndruid on 2008-01-27
You could always make a script to do it. I don't know how to do that, but if you google "programming the shell", you should be able to find out how. Hope that helps, and maybe somebody else could give you instructions.

---

### Post by ronniet on 2008-01-27
yeah, I may have to make a small start up script that deletes the two files then re-creates them. But i'm wondering if it's a bug in Amarok or something??...

---

### Post by browndruid on 2008-01-27
It most likely is a bug. I personally like [Songbird]("http://songbirdnest.com/"). It's not currently the best choice for someone who really likes radio, but I'm sure a proper plugin for last.fm will be written soon enough, as well as other radio services. It's based on the Mozilla engine, so the add-ons work almost exactly like Firefox's.

---

