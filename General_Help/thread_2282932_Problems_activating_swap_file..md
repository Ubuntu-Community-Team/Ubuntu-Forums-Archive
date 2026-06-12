---
title: "Problems activating swap file."
date: 2015-06-17
forum: General Help
---

### Post by luke27 on 2015-06-17
Hello everyone.

I am running Ubuntu 12.04 on my old Android phone with the help of an app called Linux Deploy. I am running a Minecraft server off of it.
Everything works fine, but one plugin on my Minecraft server won't do what I need it to do unless there is more available RAM. I can't exactly add more RAM to a phone, so I figured a swapfile would help me out.
I followed the guide [here]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F") and made the swap file, but when I do 'sudo swapon /mnt/sdcard/swap/512MiB.swap' I get "swapon failed: Invalid argument". I added the swapfile to /etc/fstab then restarted and ran 'sudo swapon -a' and got the same result.
I'd really like for this to work. I'm hoping someone can help me.

If it helps, the app makes a .img file on the phone (I set it for 3GB) and installs the Ubuntu installation on that file. There is also an option to allow the Ubuntu installation to access mounts outside of that img file, such as the root of the internal SD card of the Android phone. I only have about 400MB free on that 3GB .img file, so I couldn't make the swap file within there. The internal SD card had about 2GB left, so I made the file in /mnt/sdcard/swap/.

---

### Post by nerdtron on 2015-06-17
I find this tutorial helpful for that: [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by luke27 on 2015-06-18
I've done all this, as I've stated in OP. I get "swapon failed: Invalid argument" when I try to activate it.

---

### Post by QDR06VV9 on 2015-06-18
What is the output of
```
cat /proc/swaps
```

---

### Post by luke27 on 2015-06-19
It comes up empty.

```
Filename                      Type         Size       Used     Priority
```

---

### Post by dino99 on 2015-06-19
> **luke27 said:**
> It comes up empty.

```
Filename                      Type         Size       Used     Priority
```

that is, no swap on that device; you can check with 'sudo blkid'

---

### Post by QDR06VV9 on 2015-06-19
> **dino99 said:**
> that is, no swap on that device; you can check with 'sudo blkid'
+1  
Or even
```
sudo blkid | grep swap
```
Oddly I have found that adding a swap after the fact that command gives good info when swap is on another disk or his case SD card.

---

