---
title: "&quot;mei_me: init hw failure&quot; after updating to kernel 3.13.0-51-generic"
date: 2015-04-30
forum: General Help
---

### Post by chaaderf on 2015-04-30
Hello all!

Yesterday I did the kernel update on my Lubuntu 14.04.2 desktop from 3.13.0-49-generic to 3.13.0-51-generic. In reboot, before Lubuntu logo, there was an error message on screen. But I couldn't read it (it disappeared) and the logo took place. Today the same message was shown and I took a look at the logs. It seems that in the /var/log/dmesg there are following lines (at least some of them are the same as in the error message shown during boot):

```
[   10.625694] mei_me 0000:00:16.0: version message write failed: ret = -5
[   10.626162] mei_me 0000:00:16.0: hbm_start failed ret = -5
[   10.626548] mei_me 0000:00:16.0: reset failed
[   10.626855] mei_me 0000:00:16.0: link layer initialization failed.
[   10.627290] mei_me 0000:00:16.0: init hw failure.
[   10.627674] mei_me 0000:00:16.0: initialization failed.
```

Does anyone have an idea what is this and will it need to be fixed and how?

Thank you.

edit: Fix released in kernel linux-image-3.13.0-53-generic. Marking as solved.

---

### Post by Sebastian-ElMagico on 2015-05-02
I have exactly the same problem with my Notebook

---

### Post by chaaderf on 2015-05-04
Anyone please?

---

### Post by Sebastian-ElMagico on 2015-05-05
Now with the update to kernel 3.13.0-52-generic the problem persist. :(

---

### Post by QIII on 2015-05-05
Hello!

That looks similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1450813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1450813)

You might want to give that a read and see.

If that is the one, please create a launchpad account so you can click "Affects me" to turn up the heat.

---

### Post by Dennis N on 2015-05-05
Same problem here. Every boot I get all four of these to the screen:

```
mei_me 0000:00:16.0: reset failed
mei_me 0000:00:16.0: link layer initialization failed.
mei_me 0000:00:16.0: init hw failure.
mei_me 0000:00:16.0: initialization failed.
```

In the meantime, you can use an older kernel. I switched to 3.13.0-48 where these messages are not present on screen or in log.

---

### Post by chaaderf on 2015-05-06
Thank you for responses! ^^

QIII: It seems almost the same, but as I don't understand the meaning of each detail, I can't be sure. In the bug report, the first line contains irq 47, mine seems to be irq 44. Also, I'm not sure what you mean by "Affects me" - it seems I can't find it on launchpad (yes, logged in). Further, it looks like there is two patches on the launchpad, but I have no idea what those .patch files actually mean. Do I need to do something or just wait for the update manager to do its job? :confused:

---

### Post by Dennis N on 2015-05-06
Posted on 5 May 2015:

After logging in, there is a line (which is a link) that appears in the upper left, right after "Bug #1450813 reported by Pali on 2015-05-01" which reads: "This bug affects 4 people. Does this bug affect you?". Click on it and you can register in a little dialog box that you are affected.

You don't need to take any action yourself. Any fix will be supplied in another kernel upgrade.

Added:
7 May: No fix here in 3.13.0-52.86
20 May: Fixed in 3.13.0-53.88

---

