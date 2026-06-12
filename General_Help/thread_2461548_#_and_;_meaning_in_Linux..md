---
title: "# and ; meaning in Linux."
date: 2021-05-03
forum: General Help
---

### Post by gardenair on 2021-05-03
hi,
        In any configuration file  if we want to comment that particular line Linux allow " **#** " sign. Where as  there is another character " **;** " which is also use in configuration files like in  smb.conf

I shall be glad if you may guide me what " **;** "  function of this character is ? 

Thanks.

---

### Post by Xian on 2021-05-03
When the option is commented with ";" it means the setting differs from the default program behavior.

---

### Post by gardenair on 2021-05-03
well it is just like comments.The system not read that line when it execute
Example /etc/network/interfaces

```
**#** This ia a test line for assigning IP Address.
**;** address 192.168.1.10
**; **netmask 255.255.255.0
**;** gateway  192.168.1.1
```

The Linux kernel will not read both line if it is inside the configuration file.If I um-comment " **;** "  thing works.

So what is the difference in ** # **and **;**

---

### Post by guiverc on 2021-05-03
Which standard to use....  [https://xkcd.com/927/](https://xkcd.com/927/)

GNU options are usually '--' in front of the option, unix tends to use '-' (or nothing; `ps aux`)
GNU/Linux tends to use "#" as marking comments; BSD tends to prefer ";"

But our systems today are a mixture of some components that started up the older BSD or unix world; plus other parts that were from GNU or Linux, thus some programs/applications use the ";" whilst others use "#" etc

The difference is where the programmer initially came from; which "standard" or OS the developer preferred... and thus which he/she then implemented in their newer created project/application.

The difference is just historical & which standard felt "*most at home*" to the developer.

I'll refer back to the XKCD comic - [https://xkcd.com/927/](https://xkcd.com/927/)

---

### Post by Geoff_Lane on 2021-05-03
> **Xian said:**
> When the option is commented with ";" it means the setting differs from the default program behavior.

Ah, interesting.  Didn't actually know that.

geoff

---

### Post by Xian on 2021-05-03
The OP referenced a specific file as an example of their question. 

In that file the following is shown below.

It's use with that application is not expected to be found globally.

```
# Some options that are often worth tuning have been included as# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
```

---

### Post by gardenair on 2021-05-07
Thanks a lot for the valuable information. In short we can say that " **#** " or " **; **" have same characteristics .

---

### Post by The Cog on 2021-05-07
> **gardenair said:**
> Thanks a lot for the valuable information. In short we can say that " **#** " or " **; **" have same characteristics .

That's not at all universally true. Many configuration files use just one or the other. I think that being able to use either in a configuration file is unusual.

---

### Post by mIk3_08 on 2021-05-07
For me;
The ";" this is to declare a function to be functional. sensitive type of function.
while "#" this is to avoid the string to be functional in short non-functional 
That is in my opinion.  
But in IRC this "#" can be a channel :-) #ubuntu

---

