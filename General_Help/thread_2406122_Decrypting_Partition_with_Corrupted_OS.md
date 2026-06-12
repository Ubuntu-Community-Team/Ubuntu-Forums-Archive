---
title: "Decrypting Partition with Corrupted OS"
date: 2018-11-15
forum: General Help
---

### Post by budgetballer on 2018-11-15
So I have a Dell Inspiron 15-3565 I had Windows 10 and Ubuntu 16.04 dual boot on where my Ubuntu /home folder was encrypted using the encryption option on install. I corrupted both OS's when I attempted to install Qubes so I could test my C++ programs in a sandboxed environment and try out Whonix. It wouldn't work at all in UEFI mode and I switched to legacy ignoring the warnings. Qubes installed but then I couldnt ever get it to boot up past the Qubes logo so I corrupted my normal OS's for nothing. Luckily I backed up all my code on a flash drive about a week ago and had a copy of my crypto keys unencrypted in my Windows partition and recovered that. However I want to recover my bookmarks, 
PGP keys I use to encrypt a copy of my code I store on cloud storage and misc files I had in my encrypted Ubuntu partition.

Now when I first installed Ubuntu the mouse wouldnt work and had to use my keyboard to finish install and fixed the drivers after booting up full installed version. When I was getting updates it started freezing on the newer kernals and I had to always boot using an older kernal. Of course when I tried using a live USB 18.10 or even an old Ubuntu 16.04.4 ISO I originally used to install Ubuntu only works for like a minute then freezes and wont even let me use the keyboard. I tried adding acsi=off and have AHCI enabled in my BIOs and still wouldnt work. I ended up getting lubuntu to work to recover the files on my Windows partition but when I click on the encrypted drive and enter the correct password I always logged in with it throws an error and a folder appears on the drive list with my username and wen I click on it it says access denied. I tried adding a user with the exact same name and password then trying to decrypt it and I was actually asked to enter a password twice but it says "Authorization failed for some reason". This is quite frustrating as I saw on another topic if I got Ubuntu Live to work the last method I tried should work but as I said it always freezes before I can copy the files to a flash drive.

Does anybody have any suggestions to recover this partition? I need to do it before I use my Dell Windows recovery live USB because it says it'll wipe the whole drive so that computers basically a dud (besides using lubuntu) until I figure this out. Nowhere in town sells a hard drive adapter and the one I ordered on ebay says it wont be here for over a week. I figure I could use my other computers 16.04 install and hook my hard drive to the dud computer into this one as a eternal hard drive and try again that way. But if there is a way to just do it with two computers and two flash drives anybody would like to share you'd be a life saver. 

Thanks for any help.

---

