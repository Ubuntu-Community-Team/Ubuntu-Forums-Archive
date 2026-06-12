---
title: "Desktop freezes"
date: 2006-12-01
forum: General Help
---

### Post by timbounceback on 2006-12-01
I recently installed Ubuntu Edgy Eft on my Dell Inspiron 6000 laptop. However, every time I close the laptop lid (and the laptop goes into standby), I open it again, and everything happens very slowly. I have tried running "killall gnome-panel" to refresh the panel, but this does not help. When I shutdown/reboot, I see a two messages repeating quickly on the screen that flash by to quickly for me to read, but it seems to want me to reset something. Can anyone help? ](*,)

---

### Post by LLRNR on 2006-12-01
I don't know how to fix your problem... Just an idea though: you might want to try ```
sudo shutdown -hv now
```in a terminal, to get the verbose output of your laptop's shutdown... (change the '**-h**' switch with a '**-r**' one if you want to restart instead of turn off)

Also, you might want to try to stop all running daemons before shutdown / restart, who knows, maybe there's a problem at stopping running processes as well.

Apart from this, I don't have any other ideas, but hopefully somebody else will have something better to say.

LLRNR

---

### Post by timbounceback on 2006-12-01
> **LLRNR said:**
> I don't know how to fix your problem... Just an idea though: you might want to try ```
sudo shutdown -hv now
```in a terminal, to get the verbose output of your laptop's shutdown... (change the '**-h**' switch with a '**-r**' one if you want to restart instead of turn off)

Also, you might want to try to stop all running daemons before shutdown / restart, who knows, maybe there's a problem at stopping running processes as well.

Apart from this, I don't have any other ideas, but hopefully somebody else will have something better to say.

LLRNR
I closed my laptop lid, and it didn't clog up. It was probably just a coincidence the last couple time it happened. However, when the problem does crop up again, I will give that a try. Thanks!

---

### Post by timbounceback on 2006-12-01
It happened again. The command did the same thing, but just continued to echo the output until I pressed CTRL+C. here are the fragments I have recovered:
It says something about a controller consuming too much power, and wants me to report this to shcmi@ (or something like that (it may be shpcmi, I'm not so sure.). It also mentions something about a card.

---

### Post by LLRNR on 2006-12-01
I'm really sorry, I don't know anything about that... :(

I never had such problems since I have a desktop (not a laptop), but I saw a lot of people having issues with Edgy shutdown on laptops, while others say that Edgy shutdown works perfectly on... desktops.

Good luck though, maybe somebody will have a solution for your problem; or search around a bit, maybe somebody already fixed this, I have no idea.

LLRNR

---

### Post by timbounceback on 2006-12-01
Ok, thanks anyway. But if anyone else can give me any suggestions, I will be happy to hear them!

---

### Post by timbounceback on 2006-12-01
Sorry for double posting. Anyway, I've found that this problem happens when I unplug the laptop from it's power cord. Is there anyway I can recover the shutdown messages from the system logs? It seems to be an ACPI problem. Thanks in advance! Edit: I have found the messages in the logs, and have attached them.

Tim ](*,) ](*,) ](*,)

---

### Post by timbounceback on 2006-12-01
Anyone? :(

---

### Post by LLRNR on 2006-12-01
I'm not sure if this can be of any use at all, but since I noticed in your log the string "card is consuming too much power" too often, here's a [link](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hardware) to the Hardware section of the (un)official Edgy guide; if you scroll down a little, you'll see something about sensors, controlling CPU temperatures and other such strange stuff... You might want to check those... or not :confused:

LLRNR

---

### Post by timbounceback on 2006-12-02
Interesting, although my problem seems to be laptop battery specific. I have noticed in the logs that it wants me to report the error to some mailing list  I have never heard of - should I? Thanks!

---

