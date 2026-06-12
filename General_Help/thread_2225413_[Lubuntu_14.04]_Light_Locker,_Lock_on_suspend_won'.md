---
title: "[Lubuntu 14.04] Light Locker, Lock on suspend won't work"
date: 2014-05-21
forum: General Help
---

### Post by hirotop on 2014-05-21
Hello, 

I am using lubuntu 14.04. 

When I enter the light locker settings, I could turn on the "Lock on suspend", but when I apply it and close the setting and re-enter the settings, I find the button comes back to the original position, i.e., turned off. 

Is there anyone having same trouble with me? 

Thanks.

---

### Post by bapoumba on 2014-05-21
There is a bug running that on lubuntu. Autostart Applications is not respected.
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118)

Just add light-locker to the Prefs > Default Apps > Autostart tab and it should work for you as it works for me.

---

### Post by fabian8 on 2014-07-02
I'm having this same problem. I tried bapoumba's suggestion, but it did not solve the problem. 

I'm kind of a Linux newbie, so I'm not sure if the problem is related, but I also tried writing this in the command line:

> light-locker --lock-on-suspend

and got this error message:

> ** (light-locker:2148): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-csycLtIbjq: Connection refused

I would be very grateful for some help!

---

### Post by bapoumba on 2014-07-03
Are you using lubuntu ?

---

### Post by fabian8 on 2014-07-03
Yes.

But I realize things are a bit more complex; even if the setting keeps saying it is off, I am requested to enter a password when suspending through the logout menu (sometimes I'm requested to enter the password multiple times, but I'm guessing that's another problem...). But when I suspend by closing the lid of my laptop, and then reopen the lid, I am not requested to enter a password (at least I believe the computer is suspending, since that is the option I have chosen for closing the lid in the power manager).

I will try to experiment further, and I will come back to you if I come up with anything. If you have any ideas on how to solve my problems, I'd be glad to hear them.

---

### Post by bapoumba on 2014-07-03
OK, I'll try it your way when I get back to my lubuntu setup. What I do is suspend from the logout menu, which works.

In your case, it may have to do with the delay to request a password after inactivity or when the screen blanks out (I do not recall the wording). If this is set up to never, that could explain it. My understanding is suspend from the logout menu does not involve the exact same steps as suspend by closing the lid, but I may be wrong here.

---

### Post by bapoumba on 2014-07-03
Here is what I got, and it works closing the lid.
I added light-locker to the Autostarted Applications a while back though.

---

### Post by Bucky Ball on 2014-07-03
Just chiming in here. That worked for me, bapoumba. Just set up my wife's machine and this has been one of the last few irksome issues that I couldn't solve. I have a minimal install with xfce4 and lightdm so light-locker wasn't installed. Installed it and ... Solved! Thanks. ;)

@hirotop: If bapoumba's fix doesn't work for you then, not a fix but something to try to save a hard shutdown; when you close the lid, open and you have no mouse cursor, try hitting ctl+alt+F1 followed by ctl+alt+F7. Is the cursor back?

---

### Post by bapoumba on 2014-07-03
Hey, glad it helped BB :)
If you want the whole story and how I found out : [http://ubuntuforums.org/showthread.php?t=2224690](http://ubuntuforums.org/showthread.php?t=2224690)

Cheers !

---

### Post by fabian8 on 2014-07-08
Hi again,

My settings are the same as bapoumba's and it works! But this seems odd, since I believe my settings were the same before, when it did not work. Maybe I just was confused. :P

The important point is that it is now working. Thanks for all the help, bapoumba. :)

---

### Post by Bucky Ball on 2014-07-08
Please mark as solved using thread tools to help future travelers. ;)

---

### Post by bapoumba on 2014-07-08
You are welcome fabian8 :)
Will mark the thread as solved as the OP has not been back.

---

