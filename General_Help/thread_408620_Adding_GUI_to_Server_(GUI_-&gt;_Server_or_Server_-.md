---
title: "Adding GUI to Server (GUI -&gt; Server or Server -&gt; GUI?)"
date: 2007-04-13
forum: General Help
---

### Post by pkarjala on 2007-04-13
I was recently tasked with getting a LAMP server up and running.

Downloaded Ubuntu 6.10 server, installed, setup, no problem.

Only to find that my boss wants a GUI for his server.  *facepalm*

So I pose this question:  Is it better for me to drop a GUI over the server install, or to wipe and install basic Ubuntu and add in the server software?

I'm not worried about wiping and installing clean for a fresh start.

My main concern is having a clean system running either way, and to me it seems that installing Apache, PHP, mySQL, and so forth over a GUI would be smoother, mostly because the system is already setup for GUI operation.

What, if any, is your own experience in this situation?

---

### Post by daniel of sarnia on 2007-04-13
All you need to do is type in 
```
 sudo apt-get install ubuntu-desktop
```

It will set up you GUI just as good as if you were to use the desktop CD, you will have all the same programs and everything. No need to reinstall.

Although I've never seen the point in having a gui on a server.

---

### Post by pkarjala on 2007-04-13
Neither have I, but my hands are tied in this situation.

---

### Post by pkarjala on 2007-04-13
Oh, and thanks!  Pulling down GNOME and associated files now.

---

### Post by daniel of sarnia on 2007-04-13
Yeah, I know of boss' with infinite wisdom such as this. At lest he's not having you run a windows server.:D

---

### Post by daniel of sarnia on 2007-04-13
> **pkarjala said:**
> Oh, and thanks!  Pulling down GNOME and associated files now.

No problem, and when it's done, either reboot or enter the ```
startx 
``` command.

---

### Post by az on 2007-04-13
Install the linux-generic package, too.


The server kernel does not work with all desktop hardware (like some mice, for example).

Whether you install the server version and install the desktop, or install the desktop version and then install the LAMP stack, you end up with the same thing.  Just be sure of what kernel you are using.

---

### Post by pkarjala on 2007-04-16
One of my friends did bring up the point that it may be better to download a lighter X-client, such as icewm or Xfce, as it may have a lighter load on the system while running.  Anyone have experiences with either, or know if they're relatively stable X-clients?

---

### Post by DonThompson on 2007-04-24
And when the reply is:
  Unable to find package ubuntu-desktop
What then???

---

### Post by zvacet on 2007-04-24
```
sudo aptitude update
```

```
sudo aptitude install ubuntu-desktop
```

And you have all repos open don´t you?

---

### Post by jfinkels on 2007-04-24
> **pkarjala said:**
> One of my friends did bring up the point that it may be better to download a lighter X-client, such as icewm or Xfce, as it may have a lighter load on the system while running.  Anyone have experiences with either, or know if they're relatively stable X-clients?

xfce and even better icewm, fluxbox, or openbox are all excellent. If you HAVE to install a GUI on a server, but don't really need fancy stuff, just stick with any of the latter three, they are the lightest.

---

### Post by Asho on 2007-08-15
> **zvacet said:**
> ```
sudo aptitude update
```

```
sudo aptitude install ubuntu-desktop
```

And you have all repos open don´t you?
I am doing this too and did that. But it can't find "ubuntu-desktop".

---

### Post by zvacet on 2007-08-15
```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo aptitude install ubuntu-desktop
```

---

### Post by walmartshopper67 on 2007-08-21
I know servers really shouldnt need a gui, but i could see running something like plan9 or rat poison - they're super super lightweight.

---

### Post by Soarer on 2007-08-21
Maybe he means a GUI front-end like [Webmin?]("http://www.webmin.com/") This gives you a web based GUI without an extra load on your server, and you can manage it from any PC on the LAN.

---

### Post by DeusEx on 2007-08-21
webmin is the proper server gui!

---

### Post by urukrama on 2007-08-21
If you want gnome as a GUI, don't go for ubuntu-desktop, as that will install loads of stuff you probably don't need (Openoffice, ekiga, tetex, etc.).Go for gnome-core, and you'll have a lighter gnome running in no time (do also not forget x-window-system-core or xorg!) See [here]("http://psychocats.net/ubuntu/minimal") for more details.

---

