---
title: "lost startup applications"
date: 2014-12-18
forum: General Help
---

### Post by jgw on 2014-12-18
This has nothing to do with my thread on vlc.  I seem to have lost my "startup applications".  I cannot find it in unity or ubuntu software center.  I had it, now I don't.  I did see I have a program called "boot manager" but that is not what I am looking for.  I have certain programs starting that I want to stop.  I had put them in the startup applications and now want to remove them.

Thank you.........

---

### Post by mc4man on 2014-12-18
For starters try running from a terminal & see what happens
```
gnome-session-properties
```

---

### Post by jgw on 2014-12-19
Thank you for the reply.  
Here is what I got (ran it two times);
greg@greg-desktop:~$ gnome-session-properties
The program 'gnome-session-properties' is currently not installed. You can install it by typing:
sudo apt-get install gnome-session-bin
greg@greg-desktop:~$ sudo apt-get install gnome-session-bin
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greg@greg-desktop:~$

---

### Post by jgw on 2014-12-19
Thank you for the reply.  
Here is what I got (ran it two times);
greg@greg-desktop:~$ gnome-session-properties
The program 'gnome-session-properties' is currently not installed. You can install it by typing:
sudo apt-get install gnome-session-bin
greg@greg-desktop:~$ sudo apt-get install gnome-session-bin
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greg@greg-desktop:~$

Ran it one more time to see what happened:
greg@greg-desktop:~$ gnome-session-properties
The program 'gnome-session-properties' is currently not installed. You can install it by typing:
sudo apt-get install gnome-session-bin
greg@greg-desktop:~$

---

### Post by jgw on 2014-12-20
here is what happened:

greg@greg-desktop:~$ echo $DESKTOP_SESSION
ubuntu
greg@greg-desktop:~$

---

### Post by mc4man on 2014-12-20
And I forgot - what release of ubuntu? (14.04 ?

what's this show
```
apt-cache policy gnome-session-bin gnome-session-common
```

And  - 
```
ls /usr/bin |grep gnome-session
```

```
ls /usr/local/bin
```
```

ls ~/.config/autostart
```

---

### Post by jgw on 2014-12-20
I am running with ubuntu 14.10 (updated the same day as the other machine)
Again - I have no xorg whatever in my other software (I can send you a picture if you wish)
There is more stuff being autostarted than shown

Here is a link to the results:  [http://pastebin.com/swgn8XZc](http://pastebin.com/swgn8XZc)
"ls /usr/local/bin" returned noting.

---

### Post by mc4man on 2014-12-20
Well you are or were using this ppa (which I hardly ever have looked at
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3)

One way to take a look at - 
If the ppa has been disabled then re-enable & update your sources, ie.
sudo apt-get update

Then if not already installed,  install synaptic 
sudo apt-get install synaptic

Open synaptic > Origin > click on the listing for that ppa, the /now one & see which packages you have from there.

Or just enable the ppa if not already, update your sources, then run ppa-purge on - 
```
sudo ppa-purge ppa:gnome3-team/gnome3
```

Edit: if for some reason you want to keep that ppa then one would need to take a look at where is startup applications in gnome3 land or did they just do away with altogether. 
(- that may be another ppa that needs a dist-upgrade command vs. an upgrade command..

You could manually edit those .desktops in ~/.config/autostart to suit...

---

### Post by jgw on 2014-12-20
It worked (now have startup manager).  Here are the results: [http://pastebin.com/KR0GQjCR](http://pastebin.com/KR0GQjCR)

Thank you, VERY much!  People who actually know what they are doing tend to impress me a lot!  You are one of them!!!!

---

### Post by mc4man on 2014-12-20
Great - 
so in the future when using a ppa remember  it's always best to go to the ppa page first rather than just use a terminal (even though the Description is presented in the terminal.
That way you *may* get some useful info or warnings, ect.
And by & large it's best to purge ppa's before upgrading to a new release.

---

### Post by jgw on 2014-12-20
Thank you.........

I will store this suggestion into my box of things to remember.   I had created a genuine mess.  thank you again!

---

