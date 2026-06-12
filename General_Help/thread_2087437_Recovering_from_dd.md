---
title: "Recovering from dd"
date: 2012-11-23
forum: General Help
---

### Post by pulseplanet on 2012-11-23
Hello All

   I meant to insert a different drive to burn an image on it, but instead used one where I had some important data.

```
dd if=ubuntu.iso of=/dev/sdh1
```

Is there anyway to recover the contents of the usb drive?

Thanks

KB

---

### Post by sandyd on 2012-11-23
> **pulseplanet said:**
> Hello All

   I meant to insert a different drive to burn an image on it, but instead used one where I had some important data.

```
dd if=ubuntu.iso of=/dev/sdh1
```

Is there anyway to recover the contents of the usb drive?

Thanks

KB

yes, and no.
dd is a low-level tool, and is sometimes given nicknames such as disk destroyer, data destroyer, .etc .etc.

The first 700M (that is the size of your iso) of data on the USB are lost, but the rest can be recovered with recovery software

---

### Post by pulseplanet on 2012-11-23
Thanks for the message.
Any idea how I go about doing that?

> **sandyd said:**
> yes, and no.
dd is a low-level tool, and is sometimes given nicknames such as disk destroyer, data destroyer, .etc .etc.

The first 700M (that is the size of your iso) of data on the USB are lost, but the rest can be recovered with recovery software

---

### Post by thnewguy on 2012-11-23
First, make an image of the drive so you're working with a clean copy, not the device itself.

dd if=/dev/sdh of=myimage

Then install the testdisk package from the Ubuntu repositories

sudo apt-get install testdisk

One of the programs in the testdisk package is PhotoRec. Run that on your newly created image.

photorec myimage

It will try to recover any files which survived the over-write.

---

