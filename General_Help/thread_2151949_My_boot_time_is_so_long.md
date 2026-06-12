---
title: "My boot time is so long"
date: 2013-06-06
forum: General Help
---

### Post by LinuxWillWin on 2013-06-06
[FONT=verdana][SIZE=2][COLOR=#333333]Hi Ubuntu-fans,

I'm new here in the forum and I don't know if this is the right section for this thread.
I installed Ubuntu 13.04 on my brand new computer and installed compiz, cairo dock, etc. I also made my unity launcher smaller. Now, after just a few days Ubuntu needs a long time to load after I logged in and also has a horrible boot time.[/COLOR]
[COLOR=#333333]How can I change this?[/COLOR]
[COLOR=#333333]I have already reset Unity and the time after the login was due to zero but I don't want such a big launcher. Here is a picture of bootchart:[/COLOR]
[COLOR=#333333][URL="http://s7.directupload.net/images/130605/b56glxyt.png"]
http://s7.directupload.net/images/130605/b56glxyt.png[/URL][/COLOR]
[COLOR=#333333]
Thank you so much for your help![/COLOR][/SIZE][/FONT]

---

### Post by greatsirkain on 2013-06-06
To show hidden start up items give the command
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
then go to starup applications in the installed apps menu and deselect anything you don't want or need 
eg I don't use bluetooth, gwibber, backup etc...Only disable it if you know you don't need it or you might break your setup
That should speed up your boot a little

---

### Post by LinuxWillWin on 2013-06-06
Thanks. I did this but there was only one application I could disable. This did not change the boot time. The thing is that the time after logging in is sooo long, but the time until the login screen shows is OK. Another problem is that I am not able to type in my password after standby mode. The text line stays empty. Really strange. I hope someone can help with these problem(s).

---

### Post by LinuxWillWin on 2013-06-10
Does no one have an idea?

---

### Post by pqwoerituytrueiwoq on 2013-06-10
```
rm /var/lib/ureadahead/*pack
```
reboot
hopefully the next reboot will be faster
also try booting using the profile kernel option once (hold shift during boot and edit the boot option and next to 'quite splash' add the option 'profile') [google grub2 profile for more info]
that should improve the boot speed next time

here is my boot chart if you want to compare them
[http://i.imgur.com/BCYTVA6.png](http://i.imgur.com/BCYTVA6.png)

---

### Post by LinuxWillWin on 2013-06-12
I tried it but it didn't help :(

---

### Post by LinuxWillWin on 2013-06-23
What else can I do?

---

### Post by LinuxWillWin on 2013-06-30
SOLVED!
The solution was: I installed e4rat and setted it up. Now the login time and my boot time is just half as much as before. 
[Here is the wiki and the installation advise for e4rat.]("http://wiki.ubuntuusers.de/e4rat")

Thanks for your help!

---

