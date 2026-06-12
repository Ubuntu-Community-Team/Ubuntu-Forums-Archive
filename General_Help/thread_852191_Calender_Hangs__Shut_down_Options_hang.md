---
title: "Calender Hangs / Shut down Options hang"
date: 2008-07-07
forum: General Help
---

### Post by bardic on 2008-07-07
I don't know if these two problems are related, but whenever I click on my clock to look at my calender, it just hangs. I can let it sit there all day and the whole gnome panel is un-usable. If I quit the panel, it comes back and work fine.

Also, whenever I bring up the menu to shut down, restart, lock, log, etc, it sometimes hangs. And it will hang for 5 minutes + sometimes before displaying the options. 

Any idea's about how to fix either of these issues? Thanks

---

### Post by llama320 on 2008-07-07
i don't know if they're related, but the gnome-panel problem was an early bug on hardy (i'm assuming you're using hardy, by the way :D). It should have been fixed by updates. Have you updated your system?

```
sudo apt-get update
sudo apt-get upgrade
```

should do it.

If that doesn't fix the problem (after a reboot, maybe) then you can just kill the panel. Note this is only a temporary fix, but at least you won't have to restart X or reboot or something. Anyways, to kill the panel type

```
killall gnome-panel
```
the panel should then come back within a couple seconds.

***

I'm not sure how to fix the shutdown options stuff, but you can get around that one too until you figure out a more permanent fix. Just type

```
sudo shutdown -P now
```

and if you want to reboot:
```
sudo reboot
```

Good Luck

---

### Post by bardic on 2008-07-07
Thanks for the reply. I will give those a try when I get home (at work currently). 

And ya, I'm using hardy :P

---

### Post by nikgare on 2008-07-07
It *may* be a hosts problem - can you post /etc/hosts please

---

### Post by bardic on 2008-07-07
127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

does that look normal?

edit:
@llama320 I did the update and upgrade. No updates or upgrades. :S

---

### Post by nikgare on 2008-07-07
Mine doesn't have this line:
**127.0.1.1 ubuntu**

But I don't know if that is a problem or not for you, sorry.

---

### Post by moschops on 2008-07-24
I have exactly the same problem - it's been bugging me for a while and I just learned not to click on the clock, but every once in a while I need to get the calendar and forget...

After clicking the clock panel stays in its "depressed" state and all the panels are frozen/hung so I can only use the windows on the screen and right-click from the desktop.  

If I kill Gnome with ctrl-alt-bsp I can login again but Gnome doesn't come up so it is useless.  I have to ctrl-alt-bsp and restart the machine.  

I'm fully updated and this machine was installed from scratch with Hardy.

---

### Post by moschops on 2008-07-24
Okay, entering my previous reply got me thinking - maybe I actually installed Hardy before the final version and upgraded afterwards.  Which lead me to think perhaps it was something busted in the Gnome configuration files for my user.

I created a new user and logged in as them and the clock freeze problem didn't happen.  

So I logged back in as me, renamed the .gnome and .gnome2 directories in my home directory and logged out and back in.  Low and behold the clock problem was gone.  So it was something in the config files that was broken.  I don't know what exactly but as I don't think there was anything important in my .gnome dirs (I didn't mess with my setup much) I'm not going to bother figuring it out.

I hope this helps!

---

