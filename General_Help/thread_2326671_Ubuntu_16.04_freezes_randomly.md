---
title: "Ubuntu 16.04 freezes randomly"
date: 2016-06-03
forum: General Help
---

### Post by Sostanzialmente on 2016-06-03
Hi guys, I'm not new to ubuntu and neither to other linux distro, but this time I've a problem that I can't resolve by myself.

My configuration:

MB: ASUS Sabertooth 990fx
VGA: ATI RADEON HD6950
CPU: AMD FX-6300
RAM: GSKILL 2x4 GB
Dual boot win10 and ubuntu 16.04

Ubuntu partition: / 20 GB, /home 80 GB e swap 4 GB.

And my problem:

Start by saying that this happens with every linux distro I've tried so far (fedora, debian, gentoo) and it does not seem be due to a specific DE, because I've tried with several of them (unity, gnome, kde, xfce, lxde).
The system freezes without any advice and mouse and keyboard stop working, so the only solution for me is a brutal switch off.

Despite of my VGA seems to be perfectly compatible [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), I've tried both proprietary drivers and not, but with no luck. I've also tried a kernel update, several different distros, even different version of the same distro, but nothing to do.

Thanks in advance.

---

### Post by SR71BB on 2016-06-03
Sounds similar to an issue I face. I use OpenGl as my rendering backend to fix screen tearing but it causes the pc to freeze and become unresponsive at times but is worth it since I view screen tearing to be a bigger issue for me. What compositor are you using? Try using a few others and see if it helps the problem.

---

### Post by pizza-pangolin on 2016-07-10
MB: MSI 970A
VGA: ATI RADEON HD5450
CPU: AMD FX-6300
RAM: Corsair 2x4 GB
Dual boot win10 and ubuntu 16.04

*edit* Ubuntu partition: /35 GB,  swap 2 GB.*/edit*

Hello I have the same problem. After some googling, I found out that this is a common problem... When I used my console to update my programs, my terminal encountered a problem evolving "AMD VI". That incident is logged but I do not know how to retrieve it.
Maybe some could help me fetch the log to shed some light on this issue.

---

