---
title: "(?)set GRUB_TIMEOUT to 0 or turn off grub menu at all"
date: 2013-04-11
forum: General Help
---

### Post by Locus Kiesselbachi on 2013-04-11
```
sudo nano /etc/default/grub
```
GRUB_TIMEOUT=10 , I set it to "0" (zero)
```
[FONT=Ubuntu Mono]sudo update-grub[/FONT]
```
...doing something...
RESTART
GRUB still waits its time-out :-s
What to do?

solving it, would also [solve] [B][this]("http://ubuntuforums.org/showthread.php?t=2134647")

Lubuntu 12.10[/B]

---

### Post by pfeiffep on 2013-04-11
I installed a gui based grub customizer and have had excellent results;)
```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

---

### Post by Locus Kiesselbachi on 2013-04-11
tried that already, didnt help
> **pfeiffep said:**
> ;)
```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
[B]gives:
[/B] More info: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmp7nc4al/secring.gpg' created
gpg: keyring `/tmp/tmp7nc4al/pubring.gpg' created
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp7nc4al/trustdb.gpg: trustdb created
gpg: key 3F055C03: public key "Launchpad PPA for Daniel Richter" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK


```

grub-customizer
```
[B]gives:
[/B]grub-customizer: command not found

also:
sudo: grub-customizer: command not found

any more ideas? Please! [-o<

---

### Post by pfeiffep on 2013-04-11
Those are the commands I used to install grub customizer in 12.10; and I tested the command from terminal [B]grub-customizer 
[/B]I'm pretty certain it didn't install for you possibly because of  > [COLOR=#000000]gpg: no ultimately trusted keys found[/COLOR]


I have 3 OSes installed on my machine so I need a time to choose what I'm booting into - here's a section from /etc/default/grub
```
GRUB_DEFAULT="Ubuntu, with Linux 3.5.0-24-generic"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"

```
In you case I believe you want to change these 2 items to value in red
```
GRUB_HIDDEN_TIMEOUT_QUIET="[COLOR=#ff0000]false[/COLOR]"
GRUB_TIMEOUT="[COLOR=#ff0000]0[/COLOR]"

```

---

### Post by Locus Kiesselbachi on 2013-04-12
Something from **grub**:
```
GRUB_DEFAULT=0#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=[COLOR=#ff0000]false[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]0[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
no effect, grub still sits with its timeout

Wait a minute, my commands does not have (**[COLOR=#ff0000]""[/COLOR]**) on true/false and numbers, as you have, pfeiffep.
no effect...
:-k

---

### Post by pfeiffep on 2013-04-12
Maybe this will [help]("http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry?rq=1")

---

### Post by Locus Kiesselbachi on 2013-04-12
I think it just reads GRUB from somewhere else.
I remember when I started messing with GRUB settings in the very beginning, it asked me something like "do you want to create /grub.??", but I already had "problem" with grub.
Also I looked one webpage which talked about: ```
sudo update-grub[SIZE=3]**2**[/SIZE]
```

I start to think there is another grub somewhere. Is it possible?:|

> **pfeiffep said:**
> Maybe this will [help]("http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry?rq=1") 
nop, didnt help.

---

### Post by Locus Kiesselbachi on 2013-04-15
Ok! Problem stays somewhat, but workaround is [**here**]("http://ubuntuforums.org/showthread.php?t=2134968").

---

