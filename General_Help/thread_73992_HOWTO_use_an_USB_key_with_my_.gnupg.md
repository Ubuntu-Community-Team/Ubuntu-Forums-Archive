---
title: "HOWTO use an USB key with my .gnupg"
date: 2005-10-10
forum: General Help
---

### Post by Biased turkey on 2005-10-10
I created a public-private key with GPG and I would like to save it on an USB key so I can carry it with me.
My USB key has been formated ( as root with an ext3 filesystem )
When I plug the key it is detected as media:/sdc1, could someone plaese be kind enough to tell me how to copy my .gnupg ( as a normal user ) to it ?
tia
P.S. I hope I posted in the right section.

B.T.

---

### Post by jasmuz on 2005-10-10
Hello
You shouldnt of formatted the USB Pendrive as ext3, because it will make it imposible to read on any other Windows based machine you might have to use with your key.

I recommend you format it back to FAT16.

If you wish to know how to transfer your file to the disk via terminal is as easy as this:

cp /home/user/.gnupg /media/sdc1

On a Nautilus window is as easy as copying the file to your Pendrive.

---

