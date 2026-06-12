---
title: "Repair Swap?"
date: 2006-11-02
forum: General Help
---

### Post by DarkNemesis618 on 2006-11-02
I believe I somehow screwed up my swap partition.  Whenever I boot, it gives me some really weird errors that I don't understand, but I noticed /dev/hda2 on there and that was where my swap is.  Is there some way to repair this?  It should be noted that I do get a prompt and can start X using 

```
/etc/init.d/gdm start
```

But in that terminal prompt, simple commands like vi, etc don't work...sudo doesn't even work...apparently I get right in as root

Is there a tool I can use to repair the swap partition on my ubuntu install?

I currently use 6.10 (edgy)

---

### Post by Joe_CoT on 2006-11-02
There's checkfs, defrag, and various other tools to repair data partitions. However, .... it's swap! You're better off just reformatting it.

To reformat the swap, you'll want to unmount it
```
sudo swapoff /dev/hda2
```

And then reformat it as swap
```
sudo mkswap /dev/hda2
```

You'll probably need to do that from a livecd or the recovery console if your system's that screwy, however. Also, this may not fix all your problems. A more complete listing of the errors would help sort this out, should redoing the swap not fix your issues.

---

### Post by sefs on 2006-11-02
If you are sure its just a swap partition you wanna repair why not head into gparted/qparted and delete the swap partition and recreate it and format it as a linux-swap partion (all within gparted/qparted). 

Take note of the size of it before you do though so that you know what side to create it as.  It will probably be nestled within a Extended partition. 

Were it me if it were inside an extended partition and was the ONLY partition inside that extended partition i would delete the extended partition as well, recreate the extended partition and then recreate the SWAP partition inside of there.

Please not its always wise to have a backup handy when fiddling with partitions, in case something goes wrong.

---

### Post by Joe_CoT on 2006-11-02
> Were it me if it were inside an extended partition and was the ONLY partition inside that extended partition i would delete the extended partition as well, recreate the extended partition and then recreate the SWAP partition inside of there.

Please not its always wise to have a backup handy when fiddling with partitions, in case something goes wrong.

... or he could just reformat the swap ... and **not** chance completely destroying his system. :-k

---

### Post by sefs on 2006-11-02
Agreed.

> **Joe_CoT said:**
> ... or he could just reformat the swap ... and **not** chance completely destroying his system. :-k

---

