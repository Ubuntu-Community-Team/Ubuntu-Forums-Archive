---
title: "How have I encrypted mt external drive?"
date: 2024-05-16
forum: General Help
---

### Post by jjsh2 on 2024-05-16
Some time ago, I encrypted mt external USB drive, so tat when I plug it into Ubuntu, Im prompted for a password to decrypt and mount it. However, I cant remember how I did it, and it occurs to me that if my laptop dies, I wont be able to access the files. There is a ton of family stuff Ive scanned in and stored on there and it would be a pain to locate it all again. Is there a command I can run that will give me a clue as to how I did this / what software I would need to reinstall on a fresh system to be able to mount this again.

Just to be clear, Im not trying to hack anything here, I know the password I used, just cant find the "how to" I used to set it up. Im running Ubuntu 22.04.4 LTS

---

### Post by TheFu on 2024-05-16
There are many different sorts of encryption.  Should a critical part of the encryption header become corrupted, all data inside the encryption container will be lost. This means that having a backup of the encrypted data isn't just a good idea, it is mandatory.

So, since you could have used 1 of 20+ differrent encryption methods, only the process of elimination can be used to determine which method was used.  

On Linux, LUKS is the normal encryption method when we say to encrypt a HDD/SSD during installation.

```
sudo  cryptsetup info {device}
```
will show the header information, but only for LUKS.

Start with that, then if it isn't using LUKS encryption, you'll need to try some other encryption containers.  Good luck.

For setting up and using LUKS encryption, these links to how-to videos should help.
* Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
* Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
* Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)

---

### Post by jjsh2 on 2024-05-17
Thankyou - its Luks!

---

### Post by ActionParsnip on 2024-05-17
You may want to make a backup if the data is important. Having only a single copy of important data isn't very wise IMHO. Grab another USB drive or just copy the data to a desktop PC or two in order to give multiple copies in multiple places.
Imagine if the USB drive failed......where is your data?

---

### Post by dragonfly41 on 2024-05-17
Good to see that you realise that you need a "deadman's handle" protocol in place to deal with the event of you falling under a bus. Unravelling the Gordian knot of my environment is a concern. There is a balance between security and convenience of your executor to unravel data.

---

### Post by TheFu on 2024-05-17
For really important family things, arrange with another relative to hold the data. They hold yours and you hold theirs.  If you don't want them snooping, tell different family members 1/2 or 1/3 of the decryption passphrase to access the data.  This is what my family does.  When someone dies, they come forward with their part of the decryption to the executor.

---

