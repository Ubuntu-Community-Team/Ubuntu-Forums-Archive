---
title: "Does ubuntu come with a firewall? And if so how do I turn it on?"
date: 2008-06-08
forum: General Help
---

### Post by Vigh on 2008-06-08
Does ubuntu come with a firewall? And if so how do I turn it on?

---

### Post by tom66 on 2008-06-08
Yes, Linux comes by default with iptables.

Firestarter lets you configure it.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by Pjotr123 on 2008-06-08
This may be interesting to read:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by Sef on 2008-06-08
> tom66  	
Yes, Linux comes by default with iptables.

Firestarter lets you configure it.

You can figure IP Tables with the Terminal.  Firestarter is simply a GUI to configure IP Tables.

> Does ubuntu come with a firewall? And if so how do I turn it on? 

Yes, (as has been previously mentioned), and it is turned on by default.

---

### Post by tom66 on 2008-06-08
I didn't know that, now I know something. But sometimes it is just easier to use a GUI, sometimes it's easier to use the Terminal.

---

### Post by the8thstar on 2008-06-08
there is also ufw (for uncomplicated firewall).

Type in the terminal:

> sudo apt-get install ufw

then type:

> ufw enable

---

### Post by Pjotr123 on 2008-06-08
> **Sef said:**
> You can figure IP Tables with the Terminal.  Firestarter is simply a GUI to configure IP Tables.



Yes, (as has been previously mentioned), and it is turned on by default.

It's not turned on by default:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

I found this out only recently myself.  :)

---

