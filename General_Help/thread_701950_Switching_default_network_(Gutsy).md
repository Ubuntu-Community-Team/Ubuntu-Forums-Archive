---
title: "Switching default network (Gutsy)"
date: 2008-02-19
forum: General Help
---

### Post by Krunktor on 2008-02-19
I've searched high and low for an answer to this, so you can't blame me for not searching! :P

I have both a wired network (eth0) and a wireless network (eth1) on my computer. I don't use the wired connection much; it's heavily firewalled by the people running the building, so I can't even use Pidgin. But I like to keep it connected in case the wireless ever goes out for whatever reason. 

When I log in each time, Ubuntu automatically sets my wired connection to be the default, so I have to manually change it to wireless before I can do anything online. It's not a big issue, but certainly an annoyance.

Any help?

---

### Post by Krunktor on 2008-02-19
Seriously? Not a single person is going to touch this? Not even to direct me to a thread where it's already been solved, or to tell me that it *can't* be solved? 

Wow, great community. I could get this kind of treatment back at the Windows camp.

---

### Post by pointone on 2008-02-19
Uh... first post one hour ago? Please do calm down, and appreciate that a lot of people here aren't experts and are taking their own personal time to help people. 

Paitence is a virtue.

I'm pretty sure there's a setting for this somewhere in gconf-editor, but I'm away from my Ubuntu machine at the moment. I'll see if I can find out shortly.

---

### Post by Iowan on 2008-02-19
Probably not the solution you're looking for...
One possible option: Edit **/etc/network/interfaces** remove the **auto** from eth0.  Insure the wireless (eth1?) interface has the **auto** option.

---

### Post by Krunktor on 2008-02-20
> **pointone said:**
> Uh... first post one hour ago? Please do calm down, and appreciate that a lot of people here aren't experts and are taking their own personal time to help people. 

Paitence is a virtue.

I'm pretty sure there's a setting for this somewhere in gconf-editor, but I'm away from my Ubuntu machine at the moment. I'll see if I can find out shortly.
Sorry, it's been a frustrating day and it seemed like much more than an hour since I first posted.

Thanks, Iowan. I tried that before, but the file didn't contain any mention of eth0 or eth1. I've decided to add them in with auto next to eth1 and see how that goes. I'll find out at next restart.

EDIT: No luck. It's still booting up with the wired connection enabled by default.

---

### Post by Iowan on 2008-02-20
> **Krunktor said:**
>  but the file didn't contain any mention of eth0 or eth1.
Sounds kinda odd - can you post your **/etc/network/interfaces** file?

---

### Post by Krunktor on 2008-02-20
Sure thing.

```
auto lo
iface lo inet loopback
```

That's all that's in there. In my Network Tools panel, it says that lo is a "Looback Interface."

---

