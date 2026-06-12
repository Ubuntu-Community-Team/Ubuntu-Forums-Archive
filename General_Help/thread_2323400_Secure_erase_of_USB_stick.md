---
title: "Secure erase of USB stick"
date: 2016-05-04
forum: General Help
---

### Post by ChristmasPi on 2016-05-04
I have a USB stick that has old tax information that I would like to securely erase.

I'm just wondering if Ubuntu 14.04 has any kind of utility that would allow me to do this?  I did use the Startup Disk Creator to at least format the stick, but I'm looking for something that is a bit more secure.

Thank you

---

### Post by DuckHook on 2016-05-05
The command line utility *shred* does what you are looking for. Use it carefully. CLI utilities don't babysit. They just do what they're told without asking twice. If not careful, you could wipe out your system disk, or worse, all your data. Backup first, but you should be doing that regularly anyway.

---

### Post by HermanAB on 2016-05-05
Hmm, shred doesn't actually work...

On a flash memory device, it is sufficient to erase the device - there is no need to repeatedly overwrite a file.

However, a flash device is controlled by a little ARM processor and there is no way to know what it does behind the scenes.  That device will move blocks around to ensure 'wear leveling' and 'improve write speed'.  So when you try to repeatedly write to a file, it will actually write to a new block each time.

Therefore, the only way to securely erase a flash device, is with a big hammer.

Another option, is to use dd to write zeros to the whole device, then format it again, but whether that will in fact cause the whole device to be erased and overwritten with no data left somewhere in 'bad blocks', you cannot be sure about.

---

### Post by DuckHook on 2016-05-05
Thanks HermanAB. Dang-it. I actually wrote an earlier post saying the same thing some months ago. Late night brain cramp. Must stop posting while sleep deprived.

---

### Post by kurt18947 on 2016-05-05
There are "secure-delete" and "nautilus-wipe" in the repositories. I believe that either or both overwrite selected files. I am also under the impression (perhaps mistaken) that creating a new partition table then reformatting would make it fairly difficult to get any usable data from the device. Herman's recommendation (percussive disassembly) seems the most certain though given that flash drives are pretty cheap these days. I guess it depends on the sensitivity of information and level of paranoia.

---

### Post by DuckHook on 2016-05-05
> **kurt18947 said:**
> There are "secure-delete" and "nautilus-wipe" in the repositories. I believe that either or both overwrite selected files. I am also under the impression (perhaps mistaken) that creating a new partition table then reformatting would make it fairly difficult to get any usable data from the device.Unfortunately, these methods won't work in the case of USB sticks. HermanAB is right: the little ARM chip inside the stick will defeat every attempt to write anything directly to a physical field. It intercepts all write requests from any OS and then uses its primitive but tenacious little brain to scatter new data to the least used fields in the interest of wear levelling. As far as I know, there is no way to bypass this function. Full erasure is likely achievable by filling the stick entirely with 0s, but this risks bricking the stick due to a peculiarity of EEPROM memory: their actual "rest" state is 1, not 0. So filling a stick with 0's would leave no further room for the primitive little ARM brain to shuffle things around, and if can't do its job, it is not smart enough to recover gracefully, so it just gives up the ghost. All of the old utilities like *secure-delete*, *nautilus-wipe*, *shred*, etc were designed for a simpler age of  HDDs and don't really work with EEPROM-type devices.>  Herman's recommendation (percussive disassembly) seems the most certain though given that flash drives are pretty cheap these days. I guess it depends on the sensitivity of information and level of paranoia."percussive disassembly"... :)  Cool phrase. The reason that USB sticks are so inflexible is the same reason that they are so cheap. I suppose that manufacturers could include a "kill" switch in the ARM chip that would allow the entire stick to be securely erased, but then they would probably charge more for them. Unlikely to happen given how USB sticks have become so commoditized that the race to the bottom defines that industry segment these days.

---

### Post by sudodus on 2016-05-05
For very high security I think the big hammer might do it. Or maybe better with an axe: to cut it into small pieces.

But for normal security I'm sure that > **HermanAB said:**
> Another option, is to use dd to write zeros to the whole device, then format it again, is enough. But > **DuckHook said:**
> CLI utilities don't babysit. They just do what they're told without asking twice. If not careful, you could wipe out your system disk, or worse, all your data. Backup first, but you should be doing that regularly anyway.

***dd*** is nick-named 'disk destroyer' because it does what you tell it to do without questions, even if you tell it to wipe the family pictures. You can wrap a safety belt around dd with ***mkusb***. It can also help you restore a partition table and file system automatically. See the following link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe).

---

### Post by vasa1 on 2016-05-05
> **DuckHook said:**
> ... So filling a stick with 0's would leave no further room for the primitive little ARM brain to shuffle things around, and if can't do its job, it is not smart enough to recover gracefully, so it just gives up the ghost. All of the old utilities like *secure-delete*, *nautilus-wipe*, *shred*, etc were designed for a simpler age of  HDDs and don't really work with EEPROM-type devices. ...

> **sudodus said:**
>  ... You can wrap a safety belt around dd with ***mkusb***. It can also help you restore a partition table and file system automatically. See the following link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe).
Is [mkusb's wipe the whole device]("https://help.ubuntu.com/community/mkusb/wipe#Wipe_the_whole_device") suitable for usb sticks with the "ARM brain"? How can I tell, non-destructively, whether my usb stick has this "ARM brain"?

---

### Post by sudodus on 2016-05-05
I have used this method many times on my own pendrives (of several brands). I think all of them have "ARM brains", and I have not managed to brick any of them. On the contrary, I think they are re-vitalized by the wipe-whole-device cure.

---

### Post by DuckHook on 2016-05-05
> **vasa1 said:**
> Is [mkusb's wipe the whole device]("https://help.ubuntu.com/community/mkusb/wipe#Wipe_the_whole_device") suitable for usb sticks with the "ARM brain"? How can I tell, non-destructively, whether my usb stick has this "ARM brain"?AFAIK, almost all of them have one, or all cheap consumer grade sticks do anyway. Calling them a "brain" is giving them way too much credit and may be misleading. It's a tiny primitive chip with some limited logic that implements wear-levelling. It does so by tracking what fields have been less used and automatically shoving writes into those fields with no user choice in the matter. I don't know of any USB sticks not using this technology. These days, almost all manufacturers use MLC memory to leverage more capacity with the fewest possible transistors. But since MLC memory will only take 3K to 5K erase cycles, wear-levelling is a necessary technique in cheap consumer grade USB sticks. Wikipedia has two good articles on this stuff: USB sticks [here]("https://en.wikipedia.org/wiki/USB_flash_drive"), and MLC [here]("https://en.wikipedia.org/wiki/Multi-level_cell"). To answer your specific question though, I don't know how to determine which sticks use MLC and which use the more robust SLC. SLC are bound to be more expensive but that's a pretty unreliable indicator. You could try the manufacturer's website.

As interesting as some may find this, I don't want to hijack the OPs thread either. Suffice it to say that sudodus' and HermanAB's dd method is the only one that will reliably wipe a modern USB stick. I wasn't aware that *mkusb* had a "wipe whole device" option, but it will come in useful. USB controllers may have advanced to the point where they can handle a 100% filled stick gracefully, and my info could be out of date. No way to tell but try it out. I think I might risk a couple of sticks in the next few days just to see.

---

