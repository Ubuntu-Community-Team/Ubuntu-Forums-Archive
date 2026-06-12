---
title: "boot repair"
date: 2023-07-02
forum: General Help
---

### Post by bluexpressed on 2023-07-02
hi Guys

my laptop is having boot problem, taking too long and once it boot its is too slow then freeze, so

i tried the boot repair but the boot repair GUI doesnt have an option to repair , the only option i have is "create bootInfo summary"  i saw this on the internet and this is what i did

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update -y
cat /etc/apt/sources.list.d/*yannubuntu*.list
sudo apt-cache policy boo-repair
sudo apt install -y boot-repair
boot-repair

..after the command the boot repair gui appears and doesnt have any option to recommend repair

---

### Post by Rubi1200 on 2023-07-02
Hi and welcome to the forums :-)

The boot repair is not usually used to fix problems of slow booting or freezing during/after but rather to fix being unable to boot in the first place.

Slow booting can be caused by a few issues, so to help us figure out what might be the cause run the System-Info script in my signature and post the link here.

---

