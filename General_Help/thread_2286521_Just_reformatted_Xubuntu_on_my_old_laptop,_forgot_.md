---
title: "Just reformatted Xubuntu on my old laptop, forgot to set auto-logging"
date: 2015-07-12
forum: General Help
---

### Post by Ghune on 2015-07-12
I just installed Xubuntu 15.04, and I love it (seems like I just installed an ssd...).

I just want to change the way I boot the computer: before, I used to log automatically and it was perfect. This time, I forgot to set it when I reformatted my laptop and even though I don't have to enter a password, I still have to click enter (in users and groups, I click "no password").

How can I remove the screen when I boot and directly to the desktop?


p.s.
I found a few commands on this forum, but they seem to apply to the last version, not this one.

---

### Post by kerry_s on 2015-07-12
you'll need to edit /etc/lightdm/lightdm.conf add this line:
autologin-user=user-name

"user-name" should be the name you use to log in.

---

### Post by Ghune on 2015-07-12
There is no such file in this directory: I have lightdm-gtk-greeter.conf, lightdm-gtk-greeter-ubuntu.conf and users.conf

Do I have to create one?

Edit: changed .com to .conf

---

### Post by kerry_s on 2015-07-12
okay, lol, lets just go straight to instructions.

press alt-f2 , should get a run dialog

type:
```
pkexec /usr/bin/mousepad /etc/lightdm/lightdm.conf

```
you should see this:
```
[SeatDefaults]
autologin-guest=false
autologin-user=user
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

i am running xubuntu 15.04 so it's the exact same system.

---

### Post by Ghune on 2015-07-12
Funny, I get a blank file. Nothing. Just an empty file. Do I copy paste your code?
  
[http://i.imgur.com/bGJRYdE.png](http://i.imgur.com/bGJRYdE.png)

---

### Post by Bucky Ball on 2015-07-12
Let's go straight to:

Settings> Users and Groups> Password ... and change the setting there, instead.

---

### Post by kerry_s on 2015-07-12
> **Ghune said:**
> Funny, I get a blank file. Nothing. Just an empty file. Do I copy paste your code?
  
[http://imgur.com/bGJRYdEl.png](http://imgur.com/bGJRYdEl.png)

sure, copy the code. i did  mine during install, so that might be the difference.

---

### Post by kerry_s on 2015-07-12
> **Bucky Ball said:**
> Let's go straight to:

Settings> Users and Groups> Password ... and change the setting there, instead.

not there in xubuntu 15.04. he wants "autologin" so when you boot it go's straight to the desktop.

---

### Post by Ghune on 2015-07-12
Bucky Ball, that's what I did, and since then, I don't have to enter a password, but I still have my name and I have to press enter. So, it didn't work completely.

So, what can I change in order to create the files? What is this LightDM thing? (yes, you will have guessed, I'm a newbie)

---

### Post by Ghune on 2015-07-12
Bucky Ball, that's what I did, and since then, I don't have to enter a  password, but I still have my name and I have to press enter. So, it  didn't work completely.

So, what can I change in order to create the files? What is this LightDM thing? (yes, you will have guessed, I'm a newbie)

---

### Post by Dennis N on 2015-07-12
> **kerry_s said:**
> not there in xubuntu 15.04. he wants "autologin" so when you boot it go's straight to the desktop.

If you click on "change" on the password line, there is a box to check for autologin.

---

### Post by kerry_s on 2015-07-12
sure, copy the code. i did  mine during install, so that might be the difference.

---

### Post by kerry_s on 2015-07-12
sure, copy the code. i did  mine during install, so that might be the difference.

---

### Post by Ghune on 2015-07-12
Bucky Ball, that's what I did, and since then, I don't have to enter a password, but I still have my name and I have to press enter. So, it didn't work completely.  So, what can I change in order to create the files? What is this LightDM thing? (yes, you will have guessed, I'm a newbie)

---

### Post by Ghune on 2015-07-12
Bucky Ball, that's what I did, and since then, I don't have to enter a password, but I still have my name and I have to press enter. So, it didn't work completely.  So, what can I change in order to create the files? What is this LightDM thing? (yes, you will have guessed, I'm a newbie)

---

### Post by Bucky Ball on 2015-07-12
kerry_s: The screenshot you posted is not there in 15.04? That is the exact screen I am talking about. :)

---

### Post by kerry_s on 2015-07-12
> **Dennis N said:**
> If you click on "change" on the password line, there is a box to check for autologin.

no not for auto login, only no password

[forum is bugging out today. lol ]

---

### Post by kerry_s on 2015-07-12
> **Bucky Ball said:**
> kerry_s: The screenshot you posted is not there in 15.04? That is the exact screen I am talking about. :)

that is what i have, there's just no settings for autologin in there.

[sorry forgot to add pic]

---

### Post by Ghune on 2015-07-12
It didn't work. Ok, time to go to bed, I demand a solution by tomorrow 8:00AM! ;-P

Thanks guys

---

### Post by kerry_s on 2015-07-12
> **Ghune said:**
> It didn't work. Ok, time to go to bed, I demand a solution by tomorrow 8:00AM! ;-P

Thanks guys

so you rebooted & still came to the log in screen ?

---

### Post by Dennis N on 2015-07-13
> **kerry_s said:**
> no not for auto login, only no password

[forum is bugging out today. lol ]

Well, that's interesting. I have looked at that dialog before, and assumed no password would set up automatic login!

So to do that, you need to create a file /etc/lightdm/lightdm.conf  with autologin-user=<user name>. I will make a note of that. Thanks.

Obviously possible with a single user only.

---

### Post by kerry_s on 2015-07-13
yeah, that's the only way i see on the internet. i looked at the man pages for lightdm & dm-tools, don't see any command line options for auto login.

---

### Post by Ghune on 2015-07-28
I just wanted to let people know that I eventually reinstalled Xubuntu (it took 20 minutes). Everything is working.

So, be careful when you install. Be sure to select the right option for you as it doesn't seem there is a simple way to change it afterwards.

---

### Post by Bucky Ball on 2015-07-28
Thanks for letting people know what worked for you. A resolution if on solution.

Please mark as solved. See the first link in my signature. Good luck.

---

