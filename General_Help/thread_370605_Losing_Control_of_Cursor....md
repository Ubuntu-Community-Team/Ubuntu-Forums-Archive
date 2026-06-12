---
title: "Losing Control of Cursor..."
date: 2007-02-25
forum: General Help
---

### Post by metafour on 2007-02-25
I'm running Xubuntu 6.10 Edgy and every once in a while (usually when I'm doing something resource-heavy) I lose total control of the cursor.  The cursor flat out starts jumping all over the screen all by itself, sometimes even clicking icons (I've had it hit the Quit button numerously).  Any way to fix this because it is EXTREMELY frustrating having the cursor jumping back and forth, minimizing windows, and such.

---

### Post by metafour on 2007-02-26
bump.

---

### Post by yabbadabbadont on 2007-02-26
I've had my optical mouse jump around the screen once in a while.  I just bump it and it stops.  I've never had it click on things though....  that sounds like someone messing with you.  :shock:

---

### Post by metafour on 2007-02-26
I think its my PC getting bogged down and then going crazy for some unxplainable reason.  Yesterday it happened and it opened like 15 Trash Cans by itself.

---

### Post by metafour on 2007-02-26
bump.

---

### Post by Ramses de Norre on 2007-02-26
Does it happen with the network cable unplugged too?

---

### Post by metafour on 2007-02-26
Yes.

---

### Post by metafour on 2007-03-01
Bringing this back up, still have no idea whats going on.

---

### Post by dr_dirk on 2007-04-15
I have had a similar problem with my mouse jumping, but it's not during heavy resource usage and it doesn't click on anything.

I **am** using Beryl... could that be the source of the problem?  I hope someone has a solution  because it is indeed frustrating.

Derek

---

### Post by christhemonkey on 2007-04-15
Is this using a laptop?

This sort of behaviour happens with its touchpad, but this is due to the hardware failing.

If immediately after you get these strange quirks you get the output of this command and post it back here it might help.
```
cat /var/log/messages | tail 
```

---

### Post by dr_dirk on 2007-04-15
No, this is not with a laptop.  I'll try to get the output when the problem shows up next (should be any minute).  Thanks

Derek

---

### Post by dr_dirk on 2007-04-15
root@Gonzalez:~# cat /var/log/messages | tail
Apr 15 12:35:11 Gonzalez -- MARK --
Apr 15 12:55:11 Gonzalez -- MARK --
Apr 15 13:15:12 Gonzalez -- MARK --
Apr 15 13:35:12 Gonzalez -- MARK --
Apr 15 13:55:12 Gonzalez -- MARK --
Apr 15 14:15:12 Gonzalez -- MARK --
Apr 15 14:35:12 Gonzalez -- MARK --
Apr 15 14:55:12 Gonzalez -- MARK --
Apr 15 15:15:13 Gonzalez -- MARK --
Apr 15 15:35:13 Gonzalez -- MARK --
root@Gonzalez:~# 

This is what I got when the mouse started jumping around again.  Incidentally, the mouse wheel lags as well.

---

### Post by pressman57 on 2007-04-15
I have a wireless mouse that happens to once and a while when the batteries get low or when it wants to get re-connected (pushing the connect button on the base and the one on the mouse).

---

### Post by christhemonkey on 2007-04-16
Ok, thats nothing to do with it, that is just marking every 20 minutes that the pc is on.

Personally i cant help you anymore than that, was just a stab in the dark im afraid.

---

