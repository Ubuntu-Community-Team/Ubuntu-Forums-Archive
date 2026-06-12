---
title: "Keyring problem"
date: 2006-11-03
forum: General Help
---

### Post by jogebau on 2006-11-03
Hello,

I installed network manager to take care of the wlan-connections. Now Ive got the following problem: when gnome starts the keyring app asks for my keyring password twice (not only once like it should). What can I do about that?

Thanks in advance

---

### Post by cptnapalm on 2006-11-04
This is one of those stupid but true things... at the moment there is no fix or workaround for it.

I know it is irritating as I get the same thing.  While I had hoped that Edgy would fix it, alas that has not been the case.  It is a known bug.

Maybe some additional whining on LaunchPad might aggravate someone into fixing it sooner.  ;)

---

### Post by jogebau on 2006-11-04
OK, good to know I didnt do anything wrong...

Just out of curiosity, does anybody know whether its a keyring problem or a networkmanager one?

---

### Post by jogebau on 2006-11-05
Sorry, but after rereading this thread, I found that I might have been misunderstood before:

My Problem is not that I have to enter two passwords when I enter gnome (gnome and keyringmanager). 

My Problem is: It seems that the keyringmanager is starting twice, and I have to enter its password twice as well. How can I prevent gnome from starting two instances of the keyringmanager?

---

### Post by jogebau on 2006-11-06
sorry for that, but its annoying me (the prob):

bump

---

### Post by kimusabi on 2006-11-06
Check the start-up application's list and see if the program in question is listed there twice.

Just my 2 cent's.

-Kimmeh

---

### Post by jogebau on 2006-11-06
Nope, neither networkmanager or keyringmanager are listed double. nm is listed once as it should be, keyring not at all.

---

### Post by louistan3 on 2006-11-08
my other laptop was like that too.. it asks for the keyring twice each boot.. i fixed it by goin to system > preferences > sessions > current session

and i saw two nm-applets there.. so i removed one.. then tada.. its fixed.. 

hope this helps you guys out :D

---

### Post by jogebau on 2006-11-08
Nope, only one nm-applet there.

Im a bit confused with that one...

---

### Post by jogebau on 2006-11-09
Just noticed another strange thing:

In university I use a not protected wirelessconnection together with the university-vpn. when I start my laptop here, it connects automatically to the wlan, and then when I connect to the vpn, keyringmanager appears only once, not twice, like it does at my home wlan.

Any Ideas?

---

### Post by Macchi on 2006-11-28
Same annoying problem here on my laptop:
The keyring manager asks for the password twice regarding the networkmanager applet upon start of a session with Ubuntu Edgy Eft. This occurs on a freshly installed system with the latest updates. Lets hope someone can help us with this bug, since the NetworkManager is a very useful software package for a laptop.


PS: By the way, there is also another issue with the nm-applet, that gives the following message: "The NetworkManager applet could not find some required resources". The workaround is to issue the following command and then restart: "sudo gtk-update-icon-cache -f /usr/share/icons/hicolor".

---

### Post by jogebau on 2006-11-28
Interesting that somebody reopens this thread.
Yes this is exactly the same problem that I have as well. Doesnt seem like there are any workarounds for that right now, at least I didnt find anything. Lets just hope it can be solved soon...

CU

---

### Post by lollypork on 2007-02-12
I don't know if this has been solved anywhere else, but this is what I think:

After logging out of gnome for the first time, you probably have automatically saved your session, with nm-applet started. So the next time you log into a Gnome session, it tries to start the same programs that were open with that session. But nm-applet is also in the startup list, so it gets opened twice. Am I correct?

I will try to shut it down now, reboot (and saving the session) and see what happens.

---

### Post by jogebau on 2007-03-06
no, this is not the prob i have. it only happens with my home internet connection via the router, not at university with their wlan

---

### Post by jleasure on 2007-03-20
This really got on my nerves, so here's the ugly hack I use:

```

$ cd /usr/lib/gnome-keyring/
$ sudo mv gnome-keyring-ask gnome-keyring-ask.bin
$ sudo cat > gnome-keyring-ask
#!/bin/sh
lockfile='/tmp/gnome-keyring-ask.lock'

if [ ! -e "$lockfile" ]; then
  echo -n > $lockfile
  /usr/lib/gnome-keyring/gnome-keyring-ask.bin $@
  rm -f $lockfile
else
  while [ -e "$lockfile" ] ; do sleep 1; done
  echo 1
  echo
fi

^D

$ sudo chmod +x gnome-keyring-ask


```

---

