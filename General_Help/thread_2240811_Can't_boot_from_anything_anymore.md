---
title: "Can't boot from anything anymore"
date: 2014-08-22
forum: General Help
---

### Post by Paul_Cambal on 2014-08-22
Hello everyone,
A week ago I gave try to ubuntu, I installed it nicely, with the 3 partitions, but then, for some reason, it told me I had to manage the partitions and everything and I was like: Ok I'll stick to windows 7. I booted up with windows 7, opened the partition manager and deleted all 3 partitions ( Duh, idiot ). Then I created a new partition (FAT32) that I called D:/ using all the space I just freed.

Now when boot up, it tells me "error: unknown filesystem, entering rescue mode" and the prompt goes like "grub rescue>" waiting for me to input something..
All the commands I got to work were ls and set. 
It seems that it's trying to boot on the old partition like (hd0,msdos3) or something, weird ... O_o

So I was like OK, I'll try using some live repair tools, so I opened up my bios, and booted with my usb. All I get is a black screen and a blinking underscore on the top left of my screen, no matter what tool I try. I even tried to boot with the ubuntu installation iso, but still nothin..
That's where I am now :/

If any of you has any idea, you're welcome :)

---

### Post by overdrank on 2014-08-22
Hi and welcome, Maybe this can help. [_RestoreUbuntu/XP/Vista/7Bootloader_]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")

---

### Post by sotiris2 on 2014-08-22
Well since you deleted some partitions it's now wonder grub fails. However that should in now way affect your ability to boot from a live usb. Are you sure you still have the ubuntu installer on the usb and you didn't reuse it for something else? Also make sure you are choosing to boot from the usb.

If you want to go back to just windows you 'll probably have to reinstall the windows bootloader to the mbr so you will need a windows repair tool or install disk.
However I don't think ubuntu ever asks you to manage your partitions post install. So you could just reinstall ubuntu as well. If some message you don't understand appears you can ask for clarification here.

---

### Post by Paul_Cambal on 2014-08-22
Thanks overdrank for your answer, but maybe I didn't precise I couldn't even boot on windows.
I tried launching gparted live before and it worked like a charm. Now that I retried, the same black screen reappeared. Fortunately, after exactly 6h38 of struggle, I:

1)Restored my BIOS options to factory
2)Enabled PXE (Shouldnt have helped, but heh)
3)Set SATA to IDE mode
4)Created a new Ubuntu image with pendrive

5) boot override with USB aand..

it worked ;) Grub got repaired and I have now a brand new Ubuntu!
Thanks sotiris for your.. mmh I cant find the word.. your will to help? 
> [COLOR=#000000] If some message you don't understand appears you can ask for clarification here.[/COLOR]
I dont find good guys greg like you on every forum ;)

I hope it will do if you have a similar issue
Seeya

---

