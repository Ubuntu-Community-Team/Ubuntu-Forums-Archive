---
title: "Hibernate/Suspend to Disk not working with full disk encryption"
date: 2013-01-15
forum: General Help
---

### Post by MHOOO on 2013-01-15
Hello everybody,

I have recently installed Xubuntu 12.10 and when asked during the installation, I chose to encrypt the filesystem. Now, for some reason though, hibernate is not working. I've already tried default, uswsusp & TuxOnIce hibernate. The latter two, seem to be writing the memory just fine, but as soon as I start the computer again, I simply get asked for a password during boot and the system starts just like always, i.e. without resuming.

Now, inside this article: [https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap) , I read that the problem lies in the swap being encrypted using a random key instead of a fixed key. However the command
`sudo cryptsetup status cryptswap1` returns this:

/dev/mapper/cryptswap1 is active and is in use.
  type:    PLAIN
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/mapper/xubuntu-swap_1
  offset:  0 sectors
  size:    8216576 sectors
  mode:    read/write

For some reason the device is not /dev/sdxY, as described in the article, so I'm unsure as to whether the article actually applies to my case.
Could somebody clarify to me why my device name is different, or even better, point me to a resource that describes what I need to do in order to get hibernation to work? I know there is a plethora of guides already available, but most setup the system using the terminal - which in my case the Xubuntu installation did - so I'm lost as to what applies to me and what does not.

Would love to get an answer.

Kind regards,
MHOOO

---

### Post by MHOOO on 2013-01-16
mini bump

---

### Post by brusegadi on 2013-01-16
I think the /dev/sdXY refers to something else.  To see the name of your device, type

```
 mount 
```

That will give you the info of all your mounted devices and partitions (thats where you will see your /dev/sdXY)  So, your main disk is /dev/sda and /dev.sda1 should be your first partition, /dev/sda2 the second partition, etc.

So, you should still be able to follow the guide you referred to above.  I dont think the fact that you are using Xubuntu should be a big deal.

---

### Post by MHOOO on 2013-01-27
So I finally got around to backing up my data and tried the approach - and you were right, it did work with the specified device.
I did have to uninstall the uswsup package though, since resume did not work with it.

Great thanks!

---

