---
title: "Recovering Memory After Editing A Huge Image On Gimp"
date: 2016-05-30
forum: General Help
---

### Post by braznyc on 2016-05-30
Is there a way to make the computer run fast after editing a huge file on Gimp?

I know I can reboot the computer, but I'm looking for another way to recover the memory.
Maybe a command Line or an app that can help?

---

### Post by jim_deadlock on 2016-05-30
You don't have to do anything, the system will recover the RAM as needed.

---

### Post by braznyc on 2016-05-31
It doesn't recover the RAM.

It gets so slow I have to reboot it.

:(

---

### Post by jim_deadlock on 2016-05-31
This is after you close the Gimp app completely?

---

### Post by sisco311 on 2016-05-31
> **braznyc said:**
> It doesn't recover the RAM.

Are you sure? Can you post the output of
```
free -m
```
before and after editing a file?

You can also use
```
top
```
to check out which processes are `eating' your RAM and/or CPU.

---

### Post by braznyc on 2016-05-31
Yes. It stays slow after I close Gimp.

I'll try those commands. I'll post the results asap.

Thanks.

---

### Post by Impavidus on 2016-06-01
It might be using swap. During editing of the big file in gimp, data stored in ram for other applications was stored on swap space on the hard drive. After closing gimp it takes some time before all of it is read back into ram. The OS decides when it's the appropriate time to do so. As long as not everything is back in ram, the computer may be a little slow.

---

### Post by QDR06VV9 on 2016-06-01
It has not happened to me for quite some time now but I had some success with
```
sudo sysctl -w vm.drop_caches=3

```
the above command dose...Clear filesystem memory cache.
Regards

---

### Post by braznyc on 2016-06-09
> **runrickus said:**
> It has not happened to me for quite some time now but I had some success with
```
sudo sysctl -w vm.drop_caches=3

```
the above command dose...Clear filesystem memory cache.
Regards



This helped!


Thank you all for your help!

---

