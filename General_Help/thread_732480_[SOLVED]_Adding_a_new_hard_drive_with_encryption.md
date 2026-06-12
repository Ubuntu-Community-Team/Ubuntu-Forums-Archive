---
title: "[SOLVED] Adding a new hard drive with encryption"
date: 2008-03-22
forum: General Help
---

### Post by kerryhall on 2008-03-22
Hey all! So I did a Gutsy install on my computer, with full encryption. It works great and I love it! :)

I recently purchased a new hard drive. I would like to add this hard drive, possibly making it my home directory, and I would like it to be fully encrypted as well, using the same password as the encryption of my installation. Does anyone know how to do this? I have searched the forums, but I couldn't find info about this. Thank you!!

---

### Post by kerryhall on 2008-06-05
Bump.

---

### Post by kchen on 2008-06-06
It doesn't seem like anyone has much information on this - I am also curious what the possible solutions are.

I'm assuming that you have set up your primary drive with a /boot partition and a LUKS encrypted partition with LVM2 (volume groups, physical volumes, and logical volumes). From what I've read, LUKS encryption is partition based. This means that if you want your second hard drive to be encrypted, you'll need to use cryptsetup to format the hard drive as another LUKS partition. You can use the same password to mount your second HD as your first, but this might require typing the password twice on boot.

Since you have LVM2, I'm guessing that you can add your second encrypted hard drive as an additional physical volume and dynamically resize your /home folder to meet your needs. I'm guessing the key to making this all work seamlessly would be to have ubuntu ask for the passwords of both hard drives immediately on boot, before LVM2 kicks in. Personally, I'm very curious if this would work. If it does, it could be a great community-contributed howto.

Good luck!

---

### Post by kerryhall on 2008-06-07
I have no idea how it was set up. I did the setup with encryption.

Obviously I have a lot of reading to do unless someone can write a how-to, or it is a feature to be included in Ibex. Does anyone know where I can suggest new features?

Thanks!!

---

### Post by kerryhall on 2008-06-24
bump...

---

### Post by kerryhall on 2008-07-03
bump....I'm surprised that I am the only one with this question. Does no one else use encryption?

---

### Post by kerryhall on 2008-07-15
bump

---

### Post by kerryhall on 2008-07-22
bump

---

