---
title: "Ubuntu 18.04.5 LTS bionic - brightness set to maximum and change doesn't work"
date: 2022-07-05
forum: General Help
---

### Post by monera on 2022-07-05
Hi guys,

I am trying to solve this situation since a long time with no success.

The brightness is set at its maximum, and it is not possible to change. I use the keys to change it, the image of the change appears there, I can go up and down, but the brightness never changes, and is always in the maximum. I checked the drivers and everything looks fine. I already tried:

this [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
this[/B] [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=linux"


[/B]and even installed a program that promised to put things to normal, but nothing works...

Please help me guys. It is quite annoying to have this set to full brightness.

Thank you.

I also tried this: [https://www.youtube.com/watch?v=PQqvKnalipM](https://www.youtube.com/watch?v=PQqvKnalipM)


with no success too...

Guys, I also tried this: [https://www.youtube.com/watch?v=g2_V5OtiRx8](https://www.youtube.com/watch?v=g2_V5OtiRx8)

and it says my gamma siz is 0! So looks like that is the reason why nothing changes. It comes like this:

monera@monera-HP-Pavilion-Notebook:~$ xrandr --listmonitors
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +*default 1366/361x768/203+0+0  default
monera@monera-HP-Pavilion-Notebook:~$ xrandr --output default --brightness .50
xrandr: Gamma size is 0.

 Does anybody knows how to solve that?

I also tried this with no success :S  monera@monera-HP-Pavilion-Notebook:~$ sudo -i [sudo] senha para monera:  root@monera-HP-Pavilion-Notebook:~# sudo /etc/rc.local sudo: /etc/rc.local: comando não encontrado root@monera-HP-Pavilion-Notebook:~# sudo gedit /etc/rc.local  ** (gedit:4561): WARNING **: 12:23:45.821: Set document metadata failed: Não é suportada a definição do atributo metadata::gedit-position root@monera-HP-Pavilion-Notebook:~# xrandr -q xrandr: Failed to get size of gamma for output default Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768 default connected primary 1366x768+0+0 0mm x 0mm    1366x768      76.00*  root@monera-HP-Pavilion-Notebook:~# exit sair monera@monera-HP-Pavilion-Notebook:~$ sudo ubuntu-drivers autoinstall [sudo] senha para monera:  No drivers found for installation.

I also tried this with no success :S   monera@monera-HP-Pavilion-Notebook:~$ sudo -i [sudo] senha para monera: root@monera-HP-Pavilion-Notebook:~# sudo /etc/rc.local sudo: /etc/rc.local: comando não encontrado root@monera-HP-Pavilion-Notebook:~# sudo gedit /etc/rc.local ** (gedit:4561): WARNING **: 12:23:45.821: Set document metadata failed: Não é suportada a definição do atributo metadata::gedit-position root@monera-HP-Pavilion-Notebook:~# xrandr -q xrandr: Failed to get size of gamma for output default Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768 default connected primary 1366x768+0+0 0mm x 0mm 1366x768 76.00* root@monera-HP-Pavilion-Notebook:~# exit sair monera@monera-HP-Pavilion-Notebook:~$ sudo ubuntu-drivers autoinstall [sudo] senha para monera: No drivers found for installation.

---

### Post by #&amp;thj^% on 2022-07-05
Check your Other thread: [https://ubuntuforums.org/showthread.php?t=2476717&p=14103056#post14103056](https://ubuntuforums.org/showthread.php?t=2476717&p=14103056#post14103056)
Posting multiple threads here is discouraged, adds confusion and dilutes community efforts to help you.

---

