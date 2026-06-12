---
title: "Ubuntu is not recognizing my RESET password"
date: 2017-12-15
forum: General Help
---

### Post by javierdl on 2017-12-15
For the life of me, I couldn't remember the password I was using in my old pc, so I followed [these steps]("http://www.psychocats.net/ubuntu/resetpassword") to reset it.
Everything seemed ok, it did show that the password had been "successfully" reset.
However, when rebooting and entering the new password it would just blink the screen and stay at the login screen. I did the password reset "twice", and I'm still stuck here :(

Any ideas?

Thanks guys

---

### Post by Impavidus on 2017-12-15
> **javierdl said:**
> ... it would just blink the screen and stay at the login screen.

So it doesn't give you the message that the password is incorrect. This means that the password is correct, but your session crashes immediately and you are logged out.

Which version of Ubuntu? Can you login on the console (ctrl+alt+F2; ctrl+alt+F7 to return to graphical login)? Before Ubuntu 17.10 this problem is often caused by wrong permissions/owner of the files .Xauthority or .ICEauthority.
```
ls -l .Xauthority .ICEauthority
```If not owned by you, fix ownership (or simply delete, as they will be recreated when you log in). So too if permissions are not rw for the owner and none for group and others.

---

### Post by javierdl on 2017-12-15
Hi Impavidus,

I am using 14.10 
I'll try the return to the graphical login as you suggest.
Should I enter that command line? (ls -l .Xauthority .ICEauthority)

---

### Post by javierdl on 2017-12-15
Ok, so I rebooted and once I was at the login screen, and used Ctrl Alt F2, and I got this:

```
[COLOR=#212121][FONT=Roboto]Ubuntu 14.10 javier-System-Product-Name tty2
javier-System-Product-Name login:[/FONT][/COLOR]
```

I tried the only password I could think of, and of course it didn't work.
Then I entered the code you gave me, I thought: what the heck!
But of course, it didn't work either.

---

### Post by ian-weisser on 2017-12-15
Ubuntu 14.10 is long past EOL and out of support.
We gently suggest you backup your data and install a supported version of Ubuntu.

---

### Post by Impavidus on 2017-12-16
> **javierdl said:**
> Ok, so I rebooted and once I was at the login screen, and used Ctrl Alt F2, and I got this:

```
[COLOR=#212121][FONT=Roboto]Ubuntu 14.10 javier-System-Product-Name tty2
javier-System-Product-Name login:[/FONT][/COLOR]
```

I tried the only password I could think of, and of course it didn't work.
Then I entered the code you gave me, I thought: what the heck!
But of course, it didn't work either.

You must first type your user name (which I assume to be javier), hit enter, then type the password and hit enter.

But I agree with ian-weisser. 14.10 is old and there's no easy and reliable way to get it upgraded to something supported. It reached end of life in July 2015. Create a live disk of 16.04 or 17.10, use it to access the hard drive and make backups of all files you still need on an external drive and make a fresh install. 16.04 is the current LTS release. 17.10 is not an LTS release, but if you plan to upgrade to the next LTS release ASAP anyway, that doesn't matter.

---

### Post by javierdl on 2017-12-16
Fair enough!
I was starting to feel that way too, anyway.
Thank you guys for your help :)

And Happy Holidays!

---

