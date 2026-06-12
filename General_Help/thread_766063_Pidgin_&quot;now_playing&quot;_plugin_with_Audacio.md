---
title: "Pidgin &quot;now playing&quot; plugin with Audacious"
date: 2008-04-25
forum: General Help
---

### Post by templesyrinx2112 on 2008-04-25
With XMMS out of the repos, I am having the most difficult time with this once easy task.

Usually it was XMMS + Current Track + Pidgin = current song as my status

Now, with Audacious, I've tried Current Track (crashes Pidgin), Music Tracker (didn't work), and even the Pidgin-Audacious that is in the repos.  That didn't do anything either.

Looking around, there isn't really anything out on the web yet.  But, I did find a Pidgin-Audacious-Remote source to compile.  It's now there in my Plugins list, but I can't check it to enable it.  When I jam on the mouse, it eventually crashes Pidgin.

Can anyone offer some insight on this?  Or, let me know where to find XMMS?  Or, know if WinAmp works through WINE?  

Thanks!

---

### Post by DirtDawg on 2008-04-25
Hi. Check the second post of this thread. There's a link for a Hardy deb package of xmms: [http://ubuntuforums.org/showthread.php?t=765609](http://ubuntuforums.org/showthread.php?t=765609)

I still can't believe xmms was removed from the repos. Bad move, IMO.

---

### Post by templesyrinx2112 on 2008-04-25
Thanks for pointing me over to that XMMS deb!

So, to have this work again....

Download that, and any dependencies that it needs.

Download Current Track for Pidgin
[http://sourceforge.net/project/platformdownload.php?group_id=151509](http://sourceforge.net/project/platformdownload.php?group_id=151509)

It's a RPM, so you'll need to:
```

sudo alien currenttrack-1.2-1.i386.rpm

```

Once you got the .deb file, click to install

In Pidgin > Plugins, enable Current Track. 
Configure Plugin, and choose XMMS

It will **automatically** display if you have a song playing.

---

### Post by zero777zero on 2009-05-27
bump, i cant get this to work with pidgin + audacious

---

