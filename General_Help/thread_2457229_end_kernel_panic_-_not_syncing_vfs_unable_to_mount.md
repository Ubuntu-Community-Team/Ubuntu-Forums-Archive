---
title: "end kernel panic - not syncing vfs unable to mount root fs on unknown-block(0 0)"
date: 2021-01-28
forum: General Help
---

### Post by savant1919 on 2021-01-28
Ubuntu 20.10

[COLOR=#242729][FONT=Arial][FONT=var(--theme-question-body-font-family)][FONT=inherit]I've got a dual boot system where have Windows in one partition and Ubuntu 20.10 in other.I'm not sure what started to cause it but nowadays anytime I try to start my Ubuntu I get the > end kernel panic - not syncing vfs unable to mount root fs on unknown-block(0 0) Error.
[/FONT]
[FONT=inherit]As I have dual boot I can go into grub menu and tried one of the options I found online. basically it was this:[/FONT]
[FONT=inherit]I found that my ubuntu installation was in (hd0, msdos8) so;[/FONT]
grub> set root=(hd0,msdos8)

> grub> linux /boot/vmlinuz-5.8.0-40-generic

> grub> initrd /boot/initrd.img-5.8.0-40-generic

> grub> boot

[FONT=inherit]I should note that during linux or initrd lines I sometimes get the error attempting to write or read outside disk (hd0). After a few tries on the same code it works tho. When I say boot however it sends me to initframs page. There I can't seem to get the ubuntu to start. Sometimes it just works I don't know how. It is annoying to go through this everytime I want to code on Ubuntu.
[/FONT]
[FONT=inherit]Note: I never have any trouble starting Windows and did a disk health check.
[/FONT]
[FONT=inherit]Thanks for replies.[/FONT]
[/FONT]
[/FONT][/COLOR]

---

