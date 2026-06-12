---
title: "help needed with luks / sda5_crypt decryption (password mixed up)"
date: 2017-06-05
forum: General Help
---

### Post by tschss on 2017-06-05
Hey, everyone! :)

I encrypted my notebook with luks / sda5_crypt and been using it for over half a year - I went out of town the past weekend and let a friend sleept in my room whom I wanted to give the possibility to use my ubuntu notebook. Then things went stupid: I just could not remember the right way to type my password once I really thought about it even though I had typed it in houndreds of times already. I am stuck with this problem since. I know the characters of my pass phrase I am only unsure about their order and which characters are capitalised. Being not really fond of mathematics the "easiest" (read: manageable) way for me was to write down all possible combinations and try and type them in. Still no success, the disk remains locked - but actually I feel like I should have entered the right password already...

Therefore I ask you for insights into the following questions:
- Is there a maximum of tries/fails of entering the pass phrase? Is there a certain limit after which even the correct entry is not accepted without further notice? I didn't see any message that is.

- Is there a possibility to boot the notebook via ubuntu-live-usb, then try to mount the hard disk and have a program running that automatically tries all combinations of my password? I am aware that this might take some time but considering I basically know the password's elements shouldn't be there a way to "crack" it? If so I would be really happy if you could point me to a detailed explanation how to do that, I am pretty new to all of this. Searching the Internet I stumbled about "brute forcing" which appears to kind of be what I mean but I don't know how to apply this to my problem really. I am not planning to actually break into some unkown password but I am just really fed up with typing in my own passwords in all thinkable combinations again and again and again whilst at worst even doing it wrongly and missing a combination.

Please help me out, I really need to access my data on that notebook. :???: :(

---

### Post by TheFu on 2017-06-05
If you don't know the password, there is no realistic way to unlock the disk.  You have 2 options.
a) Use your backup/restore method to put things back to a way before you forgot the LUKS passphrase.
b) Wipe everything and start over.

You can screw around with a live-boot, if you like, but it will not unlock the LUKS dm-crypt partition if you don't know the passphrase.  Plus, you'll want to be good with LVM commands to open those **after** you get the partition unlocked.

BTW, I did this multiple times over the weekend, so this knowledge is fresh.  But I know how to enter the decrypt passphrase on my system (I use 2FA for it).

---

