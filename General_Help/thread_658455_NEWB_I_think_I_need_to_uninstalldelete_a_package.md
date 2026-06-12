---
title: "NEWB: I think I need to uninstall/delete a package"
date: 2008-01-04
forum: General Help
---

### Post by hblask on 2008-01-04
I'm new to Linux, but experienced as a user in Unix.  Ubuntu installed beautifully for me, but then I decided to add anjunta (C++ environment).

Well, it had dependencies, and one thing led to another and I've spent the day installing packages, which require other packages, which require other packages....etc.

So I'm currently trying to intall atk, and when I type the ./configure in the directory, I get the following message:

[INDENT]*** 'pkg-config --modversion glib-2.0' returned 2.14.4, but GLIB (2.14.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
[/INDENT]

I do have 2.14.4 installed, so what do I do next?  I've been poking around for an hour and I think I'm at a dead end as to how to make the system use 2.14.4

---

### Post by Nonno Bassotto on 2008-01-04
Well, all I can say is that this is not the way you are supposed to install packages in Ubuntu. There is a software manager, called Synaptic, which can handle the dependencies for you. [Here]("http://www.psychocats.net/ubuntu/installingsoftware") you find more details.

---

### Post by seventhc on 2008-01-04
anjunta isn't in synaptic as far as i can tell.

is it anjunta or anjuta?? if you are looking for anjuta then you can do this
```

sudo apt-get install anjuta
```and that will be easy

if this is the home page [http://www.anjuta.org/](http://www.anjuta.org/) then run the command, I just installed it in like 1 minute. I hope it is what you are looking for.
anjuta DevStudio with a horse head icon

---

### Post by hblask on 2008-01-04
> **seventhc said:**
> anjunta isn't in synaptic as far as i can tell.

is it anjunta or anjuta?? if you are looking for anjuta then you can do this
```

sudo apt-get install anjuta
```and that will be easy

if this is the home page [http://www.anjuta.org/](http://www.anjuta.org/) then run the command, I just installed it in like 1 minute. I hope it is what you are looking for.
anjuta DevStudio with a horse head icon


Here's what I get when I type that command:

[INDENT]$ sudo apt-get install anjuta
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package anjuta
[/INDENT]

And to the other responder, yes, I tried using Synaptic, but it wasn't in there, and I couldn't figure out how to get Synaptic to recognize it.  Either way I would've had to go and find a bunch of other libraries, right?  The problem now seems to be that the system knows it has a newer version of GLIB, but wants to run (?) the older version.  So if I could figure out how to remove them, I would.  I've tried uninstalling ALL versions of it with sudo make uninstall, and it seems to get rid of it, but I still get the same message after the reinstall.

---

### Post by seventhc on 2008-01-04
It installed for me without me having to do anything extra.
I had all the repos enabled,
screenshot of it.
[IMG]http://i14.photobucket.com/albums/a337/seventhc/anjuta.png[/IMG]

---

### Post by hblask on 2008-01-04
> **seventhc said:**
> It installed for me without me having to do anything extra.
I had all the repos enabled,

Thanks, this actually turned out to be a helpful response, because it turns out I've been searching for the wrong keywords.  Thanks to this post I found this page:

[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

and it turns out I CAN use synaptic to install Anjuta -- I'm working on it now, but I expect better results now.....

---

### Post by seventhc on 2008-01-04
Good:) Hope it works :)

---

### Post by hblask on 2008-01-05
> **seventhc said:**
> Good:) Hope it works :)

OK, it wasn't flawless, but it was pretty darn close.  It's all up an running now....

Whoo hoo, a new Linux programmer!!!!

---

### Post by seventhc on 2008-01-05
> **hblask said:**
> OK, it wasn't flawless, but it was pretty darn close.  It's all up an running now....

Whoo hoo, a new Linux programmer!!!!
Ah good to hear, I was wondering what happened. Now enjoy the fruits of your labor. :)

---

