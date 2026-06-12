---
title: "[SOLVED] K3B warning message"
date: 2008-03-18
forum: General Help
---

### Post by Rytron on 2008-03-18
Hi,
I wanted to copy an iso to cd so I opend up K3B. I never got this warning before. Please view attached image. I tried the command 'su hdparm -d 1 /dev/hda' in the terminal but I go this:

```
myname@computername:~$ su hdparm -d 1 /dev/hda
su: invalid option -- d
Usage: su [options] 

[LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display 

this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment    

    do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL           

  use SHELL instead of the default in passwd
```

as normal user I got this (I know I must be as root but this brought up info that may be relevant):

```
myname@computername:~$ hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma     =  0 (off)
```

What must I do?
Thank you.

---

### Post by chewearn on 2008-03-18
How about:
```
sudo hdparm -d 1 /dev/hda
```

---

### Post by Rytron on 2008-03-19
> **AstalaVista said:**
> How about:
```
sudo hdparm -d 1 /dev/hda
```

[COLOR="Sienna"]It worked a charm.[/COLOR]

---

