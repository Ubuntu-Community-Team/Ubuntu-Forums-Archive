---
title: "current version?"
date: 2007-04-10
forum: General Help
---

### Post by Mia_tech on 2007-04-10
I just upgraded ubuntu to 7.04, how to verify what version I'm running? is there a command for that or where to go

thanks

---

### Post by justin whitaker on 2007-04-10
> **Mia_tech said:**
> I just upgraded ubuntu to 7.04, how to verify what version I'm running? is there a command for that or where to go

thanks

The system monitor has a tab which tells you all the information about your system, including which kernel version you are running. At least, I think it does. Might be wrong. :)

---

### Post by pupeeler on 2007-04-10
& what does *uname -a* return?

---

### Post by ardchoille42 on 2007-04-10
Open a terminal and type:
```

lsb_release -a

```

On my system, that command returns:
```

Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

```

---

### Post by Mia_tech on 2007-04-10
> **pupeeler said:**
> & what does *uname -a* return?

no uname -a doesn't return that info very useful though, I believe there is a lsb_vesion or something like that that gives you the version of ubuntu, uname gives you the kernel version

---

### Post by Kizilbas on 2007-04-10
I am using Xubuntu 6.06 Dapper Distrubution, and when I type the command ardchoille42 suggested I got this:

Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy


[b][i]But I had the OS; 6.06 Dapper. I might have updated it accidentally. 
Does this information show/mean I have all the functionality and updated versions of the default programs/interface etc for Ubuntu? (I am using the Xubuntu distro of Ubuntu by the way).

Thanks :)
[/b][/i]

---

### Post by zvacet on 2007-04-10
Are you sure that you installed Xubuntu Dapper,because it is posssibilty that you upgrade with update manager,but it is very big download so I think you will remeber it.

---

### Post by Kuoi on 2007-04-19
> **ardchoille42 said:**
> Open a terminal and type:
```

lsb_release -a

```

On my system, that command returns:
```

Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

```

That's working fine.
I wanted to verify if I had Feisty after an upgrade about an hour ago and guess what the above command returns ...
> Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty


Thank you "ardchoille42" for the tip .

Kuoi

---

