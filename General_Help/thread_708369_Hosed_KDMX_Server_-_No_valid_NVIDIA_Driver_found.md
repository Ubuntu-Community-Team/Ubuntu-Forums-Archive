---
title: "Hosed KDM/X Server - No valid NVIDIA Driver found"
date: 2008-02-26
forum: General Help
---

### Post by Redlazer on 2008-02-26
Hey guys,

My Kubuntu install blew up again.

After yesterdays language file update, a restart hosed my install. It used to:

When i tried to login, it would get to the second finger (im using a custom login background), then return me to the login screen with no error messages.

Now, mysteriously, i can login, but about 75% of the time, still on the second finger, it hangs for about 2 minutes, then i get a message saying it cant start the kdmserver.

The other 25% of the time, it hangs on the second finger.

Ive tried creating alternate accounts, none of them work, except for the disaster recover partition - but i dont know what to do from there to actually fix anything. 

When i attempt to login from the shell (right term?) i get the error message that it couldn't find a valid Nvidia driver.

How do i fix it, preferably without reinstalling?

Thanks for your help!

-Fred

---

### Post by alan34 on 2008-02-26
Get to you login then Ctl-Alt-F2 will take you to a black terminal login screen.

Login then

sudo dpkg-reconfigure -phigh xserver-xorg

Pick the nv driver (vesa if that does not work)

Then

shutdown -r now

should get you back your desktop

---

### Post by Redlazer on 2008-02-26
That didnt quite work. I have tried that one before, and accepted most of the defaults.

However, when i run that program now, i get the following error:

xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/......

I dont see the reconfigure program at all - the screen goes blank for one second, then returns with that message.

Thanks for you reply.

-Fred

---

### Post by tgilbert328 on 2008-02-26
This fixed the language file update problem for me.  Found it on another thread:

```
sudo apt-get remove language-pack-kde-en-base
```

Then

```

startkde

```

Maybe that will help.

Tim

---

### Post by Redlazer on 2008-02-26
Damn. I bet that would have worked, but i gave up and reformatted.

Thanks for your time everyone.

-Fred

---

