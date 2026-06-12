---
title: "HP Upgrade Manager"
date: 2018-02-16
forum: General Help
---

### Post by daniell59 on 2018-02-16
Every time I boot up I get the following notice. 

HP Upgrade Manager
Latest Version of HPLIP-3.17.11 is available
I hit the download install button. The notice goes away, only to return when I boot up again.

Ubuntu 16.04 64

Thanks in advance

---

### Post by #&amp;thj^% on 2018-02-16
> **daniell59 said:**
> Every time I boot up I get the following notice. 

HP Upgrade Manager
Latest Version of HPLIP-3.17.11 is available
I hit the download install button. The notice goes away, only to return when I boot up again.

Ubuntu 16.04 64

Thanks in advance

When you need something more recent than what is provided in the repository you would have to go to a different source, in this case you can go directly to HP.

The latest HP provided drivers are located at:
[https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)

That is a permanent link where they provide their latest drivers, which currently is version 3.17.11.

After you have run the install program, followup with the apt command to fix the missing dependencies.

```
sudo apt install -f
```
BTW I would just stay with the current version you have now, Unless there is a reason to upgrade. (Just my 2 cents worth)

---

### Post by daniell59 on 2018-02-16
Thanks, since everything is working perfectly, I will leave it as is. But what is the purpose of the notice, if it does not install when I hit the install button?

---

### Post by #&amp;thj^% on 2018-02-16
> **daniell59 said:**
>  But what is the purpose of the notice, if it does not install when I hit the install button?
Just to notify the user of a newer version.(On Linux)
I all can say here>>>>Wishful Thinking.
Who knows maybe one day. ;)

---

