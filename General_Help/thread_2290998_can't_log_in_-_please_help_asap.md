---
title: "can't log in - please help asap"
date: 2015-08-17
forum: General Help
---

### Post by al.adab on 2015-08-17
hello there,

i'm in a sticky situation: I tampered with /etc/default/grab/ to try and find a solution to Ubuntu 14.04.03 not shutting down. After that, Unity was gone but I was still able to log in (I'd set "log in" in the automatic mode upon installing Ubuntu) and use the folder system to get to USB creator and Terminal.  

Thinking that the system was broken I tried right away to re-install the system, though USB Creator let me down: it first gave me some "bus" error (sorry I'm not going to be very precise here) when I clicked on "erase" (usb stick) and then the message "installation failed" popped up. I tried to reboot a few more times to no avail (had to force shut the machine every time). Now I can't even log in any more (I'm on a guest session, where - I've just found out - there's no way to use USB creator. I understand the security issue up to a point here. 

Anyway, here's what happens in details: 

- upon booting the pc (Asus UX301) the Ubuntu username & password screen appear,
- i insert both, the screen flashes + produces the Ubuntu error sound, but doesn't log me in;

- if i CTRL + ALT + F1 username & password are accepted. I don't know what i should do next, though, to regain access to Unity (I tried *startx* and *startx unity* but some message about (from memory) Xauthority or something appears and then some other message about some "protocol" also appears. 

can you please help? I just need to log in to then re-install Ubuntu btw. I just hope I'm not faced with the same situation again (shutting down bug). Maybe I should go for 15.04? 

many thanks in advance.

---

### Post by dino99 on 2015-08-17
[http://ubuntuforums.org/showthread.php?t=2290845](http://ubuntuforums.org/showthread.php?t=2290845)

---

### Post by al.adab on 2015-08-17
hmmm...can i really edit a file on CTRL + ALT + F1?

---

### Post by The Cog on 2015-08-17
> **al.adab said:**
> hmmm...can i really edit a file on CTRL + ALT + F1?

Yes.
nano is an easy editor to use - prompts at the bottom of the screen:
```
sudo nano /etc/default/grub
```

---

### Post by al.adab on 2015-08-17
> **The Cog said:**
> Yes.
nano is an easy editor to use - prompts at the bottom of the screen:
```
sudo nano /etc/default/grub
```


thanks for the suggestion, i do not doubt that, except that i tried already and it led to nothing - the only messages (in ctrl * alt + f1) i vaguely remember seeing was something along the line of "file can't be edited in this environment" - perhaps indicating that X or Unit was not accessible? when i tried later (that is, after it became impossible to log in) a string of other messages came up and they seemed to have to do with some log-in conflict...

anyway thanks again - i've just jumped-started the pc and installed 15.04, so all is well :)

---

### Post by oldos2er on 2015-08-17
Strange. nano doesn't require X to run.

---

