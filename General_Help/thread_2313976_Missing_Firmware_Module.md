---
title: "Missing Firmware Module"
date: 2016-02-17
forum: General Help
---

### Post by Redalien0304 on 2016-02-17
Got this Message on doing Sudo apt-get upgrade " Possible missing firmware /lib/firmware/radeon/TAHITI_vce.bin for module radeon"
Something to fix or not worry about? Have RV530/M66 GL [Mobility FireGL V5250] in my Thinkpad T60p. Am running kernel 4.2.0.


Any help is much Appreciated 
Thanks in Adavnace

---

### Post by Eric_Bruce on 2016-03-15
this worked for me.
[URL="http://www.linuxquestions.org/questions/linux-hardware-18/missing-radeon-firmware-4175560806/"]
[/URL][http://www.linuxquestions.org/questions/linux-hardware-18/missing-radeon-firmware-4175560806/](http://www.linuxquestions.org/questions/linux-hardware-18/missing-radeon-firmware-4175560806/)




download you missing files here:
[URL="https://people.freedesktop.org/~agd5f/radeon_ucode/"]https://people.freedesktop.org/~agd5f/radeon_ucode/
[/URL]
gksu (whatever your file manager is)  in my case on Mint 
```
gksu nemo

```
and copy the downloaded file to : /lib/firmware/radeon
then run:

   ```
sudo update-initramfs -u
```

---

