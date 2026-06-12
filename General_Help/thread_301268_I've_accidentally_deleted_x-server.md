---
title: "I've accidentally deleted x-server"
date: 2006-11-16
forum: General Help
---

### Post by chris23 on 2006-11-16
In my try to uninstall nvidia drivers, i deleted also x-server from synaptic. Now Ubuntu boots to a shell and ask me to fix the problem...It says no module found and etc..Can i fix the problem or   
I have to install Ubuntu again??:-?

---

### Post by UltraSonicSite on 2006-11-16
Reformat.

---

### Post by chris23 on 2006-11-16
no other option???
:(

---

### Post by UltraSonicSite on 2006-11-16
Well I've had about 8 occurrences where the same thing happened, and so far it has succeeded to elude the ubuntu user-base, so I just assume that the only alternative it to reformat. 

Sadly, I've learned to not put too much valuable stuff on ubuntu if I know I'm gonna mess with the X-server.

So, for me, I just reformat.

Sorry =(

---

### Post by UltraSonicSite on 2006-11-16
Actually, hold on, I believe you can reconfigure and reinstall the X-server, if all you did was merely delete it, though you'll have to wait until someone who knows what to do comes.

---

### Post by taurus on 2006-11-16
```
sudo aptitude update
sudo aptitude install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Foxmike on 2006-11-16
Well, before reformating you can just try
```
sudo apt-get install xserver xorg
```

If it tells you it is already installed then try 
```
sudo apt-get install xserver xorg --reinstall
```

You have nothing to loose!

---

### Post by chris23 on 2006-11-16
apt-get ...command not found...

---

### Post by dasunst3r on 2006-11-16
Also, if you really have to reformat, I suggest backup up your home directory (if it's on the same partition as /).  I usually mount it in the shell and copy it, but does anybody have other ideas?

In any case, it seems that someone beat me to the punch in suggesting trying to reinstall X.  Best of luck!

---

### Post by chris23 on 2006-11-16
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```


It responed only at the last command ...

Failed to load module nvidia
module does not exist
no drivers available

---

### Post by Foxmike on 2006-11-16
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

Just seen this post after having sent mine.   Well, I think this you better follow those instructions!;)   Good luck!

---

### Post by taurus on 2006-11-16
> **chris23 said:**
> apt-get ...command not found...
What about the commands from my #6 post?

---

### Post by taurus on 2006-11-16
So you can't run "sudo apt-get" or "sudo aptitude" from a terminal at all?

---

### Post by chris23 on 2006-11-16
no...command not found
I've tried both.

---

### Post by taurus on 2006-11-16
Can you still use synaptic?

---

### Post by chris23 on 2006-11-16
> **taurus said:**
> Can you still use synaptic?


Ubuntu only boot at shell.
Only text,nothing else.

---

### Post by tminuszero on 2006-11-16
Are you sure that it has finished booting? Can you see your files & all mounted drives? What happens when you run 'dmesg'? Are there any error messages showing up at the end?

---

### Post by taurus on 2006-11-16
What if you boot it into recovery mode from GRUB and at the prompt, see if you can find apt-get or aptitude with

```
whereis aptitude
whereis apt-get
```

---

