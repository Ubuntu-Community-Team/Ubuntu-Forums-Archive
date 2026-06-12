---
title: "DVD playbacjk problems with xine"
date: 2005-04-05
forum: General Help
---

### Post by apriest on 2005-04-05
Hi, 

I have followed the instructions in the unofficial guide for installing DVD playback with xine but xine refuses to recognize the DVD. 


I get the following error:

            - xine engine error -
There is no input plugin available to handle /dvd:/'.
Maybe MRL syntax is wrong or file/stream source doesn't exist.

I have tried uninstalling and reinstalling the codecs and libdvd files to no avail. Xine and totem are working perfectly in my browser but, I just can't get dvd playback.

Any help would be appreciated.

Thanks

---

### Post by slade_slater on 2005-04-06
Check to make sure that your /dev/dvd symbolic link is pointing at the right device.  Use the following command:
sudo ln -sf /dev/hdc /dev/dvd (or hdd or whatever your device is) and then try playing a DVD....

---

### Post by apriest on 2005-04-06
Per the guide, I used ln -sf  /dev/cdrom /dev/dvd. this did not work. My box has two cd burners in it. One of them is a dvd/cd/rw combo drive. 

Any other suggestions?

Thanks

---

### Post by achilles21 on 2005-04-14
[QUOTE=apriest]Per the guide, I used ln -sf  /dev/cdrom /dev/dvd. this did not work. My box has two cd burners in it. One of them is a dvd/cd/rw combo drive. 

Any other suggestions?

Thanks[/QUOTE]

Check which hd?? device  from the /dev directory is your DVD drive, after that
you can create a link to your DVD drive :

ln -sf /dev/hd?? /dev/dvd

---

