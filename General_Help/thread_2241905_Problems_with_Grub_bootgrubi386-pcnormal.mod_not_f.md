---
title: "Problems with Grub: /boot/grub/i386-pc/normal.mod not found after restore"
date: 2014-08-29
forum: General Help
---

### Post by diyhouse on 2014-08-29
[COLOR=#000000]*I did a clean install of mythbuntu 14.04,.. once I got a stable system I created a backup using the following...*[/COLOR]
[COLOR=#000000]*---*[/COLOR]
[COLOR=#000000]*dd if=/dev/sda1 conv=sync,noerror bs=64K | gzip -c > /mnt/disky/OS-disk/sysimage-sda1-23May14.img.gz*[/COLOR]
[COLOR=#000000]*---*[/COLOR]
[COLOR=#000000]*Thus creating a snap-shot of my system,.. (this is something I regularly did with my 12.04 mythbuntu build)*[/COLOR]

[COLOR=#000000]*After some further playing with myth,.. (loaded some big tools via apt-get) decided to go back to prvious snap-shot. using *[/COLOR]
[COLOR=#000000]*---*[/COLOR]
[COLOR=#000000]*gunzip -c /mnt/disky/OS-disk/sysimage-sda1-XXyyy14.img.gz | dd of=/dev/sda1 conv=sync bs=64K*[/COLOR]
[COLOR=#000000]*---*[/COLOR]
[COLOR=#000000]*When I tried to reboot back into myth,.. GRUB failure!!! "error: file /boot/grub/i386-pc/normal.mod not found", ( this never happened with my 12.04 build)*[/COLOR]

[COLOR=#000000]*A quick search pointed me to some fixes about boot from DVD, mounting file system and reloading GRUB, This I tried but could not mount file system as it was corrupt, even tried a fsck,.. and just got too many errors to make me feel comfortable,.. So forced to reload and reconfigure. *[/COLOR][COLOR=#000000]*(ouch!).*[/COLOR]

[COLOR=#000000]*(*[/COLOR][http://askubuntu.com/questions/26642...-mod-not-found]("http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found")[COLOR=#000000]*)*[/COLOR]

[COLOR=#000000][I]OK so I have a working system again,.. but unable to restore snap-shots,..

My hardware has remain unchanged with no BIOS changes or updates, ( as far as I know,.. and pretty sure the wife hasn't tinkered :-) )

[/I][/COLOR][COLOR=#000000]* ....can anyone help as to how I can fix this little quirk, as I would regularly restore snap-shots when configuring system and I made a mistake or I did not like something.*[/COLOR][COLOR=#000000][I]

[/I][/COLOR]

---

### Post by diyhouse on 2014-09-04
Sorry, Just Bumping this back to the top,.. as I am still looking for help here,.. 
I have a nice stable mythtv system,.. that I cannot restore form a dd backup... and I have no idea where or what to look for.

---

