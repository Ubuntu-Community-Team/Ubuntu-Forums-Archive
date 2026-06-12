---
title: "dd command doesn't seem to actually write to usb drive"
date: 2017-12-09
forum: General Help
---

### Post by firephyz on 2017-12-09
I'm currently developing some low-level boot code as a hobby and I've been using dd to "burn" my boot.bin output images onto my usb drive /dev/sde. I'll generally use the following command:
```
sudo dd if=./boot.bin of=/dev/sde
```
For the most part, this command works just perfectly and I'll achieve write speeds of about 150KB/s when it's working. About an hour or so into development however, the reported write speed magically jumps up to around 3 MB/s after which point I find that the boot.bin image actually isn't being written to the disk.
I suspect that this has something to do with internal linux caches but I've tried almost every method to clear them such as using
```
sync
``` before the write or after the write.
I've also tried ```
echo 3 > /proc/sys/vm/drop_caches
``` It seems this does free up about 6GB worth of buff/cache as reported by the free command but subsequent writes to /dev/sde still fail to actually transfer the data.
If anyone has a solution, please enlighten me as it's getting fairly annoying to have to reboot the computer every hour or so just to continue development. Thanks!

---

### Post by HermanAB on 2017-12-09
***Careful!!!***

dd *always* writes somewhere.  If you are not sure where it is writing to, then you can ruin your system and may need to re-install.

Run dmesg.  Plug the schtick in.  Run dmesg again.  Stare at the screen a bit.  It will tell you the exact name of the USB schtick.  That is the name you need to use with dd.

---

### Post by QIII on 2017-12-09
Or be really safe if you are even the slightest bit unsure:

Disconnect all of your drives except the stick and your optical drive.  Run dd from optical media.

---

