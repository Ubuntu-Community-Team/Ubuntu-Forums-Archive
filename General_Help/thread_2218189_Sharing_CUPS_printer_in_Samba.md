---
title: "Sharing CUPS printer in Samba"
date: 2014-04-19
forum: General Help
---

### Post by xWEkxhW on 2014-04-19
Hi all,

How do I share a network CUPS printer on my Samba server? (it's not on the Samba server, it's available on a different server shared through CUPS on the LAN)

Thanks!

---

### Post by deadflowr on 2014-04-19
Edit:
Whoops, read wrong.

Maybe see about CUPS setting on
```
localhost:631
```

But to note, 

You have a printer on one machine and samba on another, and want to connect the two together?
Is that right?

Like the printer will act like it's a samba printer?
Even though it isn't.

---

### Post by xWEkxhW on 2014-04-19
> **deadflowr said:**
> You have a printer on one machine and samba on another, and want to connect the two together?
Is that right?

Thanks for the reply

That's correct, the printer is connected to a server running CUPS. Samba is running on the other server. I was hoping to share the CUPS printer in Samba by providing Samba with the URI, if that's possible.

---

### Post by bab1 on 2014-04-19
> **xWEkxhW said:**
> Thanks for the reply

That's correct, the printer is connected to a server running CUPS. Samba is running on the other server. I was hoping to share the CUPS printer in Samba by providing Samba with the URI, if that's possible.

It's all listed here: [https://wiki.samba.org/index.php/Samba_as_a_print_server]("https://wiki.samba.org/index.php/Samba_as_a_print_server")

---

