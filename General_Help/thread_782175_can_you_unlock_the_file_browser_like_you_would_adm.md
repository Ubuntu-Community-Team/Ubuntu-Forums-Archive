---
title: "can you unlock the file browser like you would administrative apps?"
date: 2008-05-04
forum: General Help
---

### Post by keeler1 on 2008-05-04
I am writing some things in using Googles Android SDK.  I have to give the emulator for it an sdcard image which is a Fat32 disk image.

I mount the image to put things onto it with 

```
mount -o loop sdcard.img /home/matt/temp 
```

Now I want to be able to drag and drop files from the temp folder but I do not have write permissions.  

I tried

```
sudo chown matt temp
```

as well as

```
sudo chmod a+w temp
```

but neither work.  I get a permission denied error when trying to chown and chmod just doesnt work.

I was wondering if there was a way to unlock nautilus like with the network manager or other administrative applications.  I need it to believe that I am root.

---

### Post by raul_ on 2008-05-04
gksu nautilus

should do it

---

