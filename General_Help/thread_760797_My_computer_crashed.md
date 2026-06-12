---
title: "My computer crashed?"
date: 2008-04-20
forum: General Help
---

### Post by patrickaupperle on 2008-04-20
I just installed win 2k in a virtual box and installed guest additions. Everything worked perfectly, I was so happy. After that virtual box stopped working. So, I restarted, hoping that would fix it. No such luck. Halfway through the progress bar I get:
```
An automatic file system check (fsck) of the root filesystem failed. a manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance modewith the root filesystem mounted in read-only mode.
```

Then it mounts the root file system in read only mode and starts a maintenance shell. I don't know what to do at all. Please help. Is this recoverable? 

To clear it up for some. This is my actual computer, not the vm.

---

### Post by TeoBigusGeekus on 2008-04-20
What if you type
```
fsck
```

---

### Post by patrickaupperle on 2008-04-20
> **TeoBigusGeekus said:**
> What if you type
```
fsck
```

It starts asking questions. should I answer y to all of them?

---

### Post by TeoBigusGeekus on 2008-04-20
I don't know...If they're not private :)

No, I mean... what kind of questions?

---

### Post by patrickaupperle on 2008-04-20
> **TeoBigusGeekus said:**
> I don't know...If they're not private :)

No, I mean... what kind of questions?

The first is 
Resize inode not valid. Recreate?

---

### Post by TeoBigusGeekus on 2008-04-20
I don't know what it means, but I would answer yes to such messages...

---

### Post by patrickaupperle on 2008-04-20
Ok, I said yes. Now the hard drive light has been on solid for about 30 seconds. It is also posting messages. It looks to be working. I hope it does not break anything, I have not ever backed up, and the hard drive is accessible through live cd. It is now asking Clone multiply-claimed blocks?

edit: I accidentally clicked y. Now it it found that the free blocks count is wrong for group 0. it wants to know if it should fix. I will probably click yes,

---

### Post by TeoBigusGeekus on 2008-04-20
Well...yes... But I still don't know what it means....

---

### Post by patrickaupperle on 2008-04-20
I answered yes to everything. It looks to be booting correctly. Thank you for your help.

---

### Post by TeoBigusGeekus on 2008-04-20
Post us what happened in the end...

---

### Post by patrickaupperle on 2008-04-23
Well, it told me certain block counts were off. So I told it to fix them by pressing y. Then it did a few other things. I just clicked yes to everything else. after that it told me it needed to reboot. I rebooted it and at shutdown it gave an error messsage, so I had to do a hard shutdown. After that it booted normally without a single problem or message.

---

### Post by danwood76 on 2008-04-23
You can make fsck automatically say yes to all repairs:
```

fsck -y

```

---

### Post by patrickaupperle on 2008-04-24
> **danwood76 said:**
> You can make fsck automatically say yes to all repairs:
```

fsck -y

```

Thats cool.

---

