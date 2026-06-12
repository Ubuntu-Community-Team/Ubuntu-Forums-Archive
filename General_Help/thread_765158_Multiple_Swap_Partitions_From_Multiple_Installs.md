---
title: "Multiple Swap Partitions From Multiple Installs?"
date: 2008-04-24
forum: General Help
---

### Post by igfud on 2008-04-24
Hello,

After installing 8.04 this morning I decided to take a look at my partitions with GParted while booted into LiveCD mode.  Attached is a screenshot of what I saw.  sda2 is my Windoze restore partition, sda1 is Windoze itself, and sda7 is Ubuntu 8.04.  Then there are three "linux-swap" partitions (sda5, sda6, sda8 ) all categorized under sda4 along with the Ubuntu (sda7) partition.

I think the last two times I upgraded Ubuntu, I just deleted the existing Ubuntu partition and installed on that free space. I never deleted the swap, though, and each time it just created a new one.  Seeing the keys icon next to sda8, I assume this is the current one and should be kept?  I tried deleting the other two but got some error about not being able to mount logical drives over "5"?  Should I try rebooting into a LiveCD again and deleting the other two swap partitions?

Thanks,
igfud

---

### Post by prshah on 2008-04-24
> **igfud said:**
> Hello,
Should I try rebooting into a LiveCD again and deleting the other two swap partitions?


Or you can use the command ```
sudo swapoff -a
``` (that turns off all swap partitions), then use fdisk to delete the extra swap partitions. You can then turn back swap on with the command ```
sudo swapon -a -e
```

---

### Post by igfud on 2008-04-24
I couldn't seem to figure out fdisk...so I went ahead and rebooted into the Live CD.  I still couldn't delete the swaps with GParted because of the error until I turned them off with your command.  Worked great.  Thanks!!

I went ahead and moved the current swap to the end of my hard drive and then enlarged my Ubuntu by the space gained from deleting the two unneeded swaps.  Linux makes this stuff so easy!  It would cost a small fortune for software to do this in Windows.

I was reading up on swap space ([http://www.linux.com/feature/121916]("http://www.linux.com/feature/121916")) and the article mentioned that 
> 
One great thing about the Linux swapping subsystem is that if you mount two (or more) swap spaces (preferably on two different devices) with the same priority, Linux will interleave its swapping activity between them, which can greatly increase swapping performance.

Would it be of benefit on my computer to keep multiple swap spaces, albeit on the same hard disk?  I've never seen more than a few MB used, so I assume it wouldn't make a noticeable difference?

igfud

---

### Post by prshah on 2008-04-25
> **igfud said:**
> 
Would it be of benefit on my computer to keep multiple swap spaces, albeit on the same hard disk?  

If the multiple swaps were on separate hard disks it will provide a boost for systems that need to use swap. Keeping two swaps on the same drive provides absolutely no benefit at all.

---

### Post by indytim on 2008-04-25
One note... if you are running multiple Lx ops at boot and remove one or more of the extra swaps, suggest you edit your fstab to make sure the swap identified there is, in fact the one remaining on your h/d.

IndyTim

---

