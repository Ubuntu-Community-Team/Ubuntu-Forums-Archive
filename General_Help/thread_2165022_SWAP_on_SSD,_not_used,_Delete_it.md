---
title: "SWAP on SSD, not used, Delete it?"
date: 2013-08-02
forum: General Help
---

### Post by Nikolai D. on 2013-08-02
Hi all,

Today i was for the first time kinda stressing my PC. Was running two VMs and bunch of other stuff. So first time most of the RAM was used.
So i checked the system monitor to see how it performed. And noticed that SWAP isnt used at all. And yes i use SSD.

What i am wondering now. As far as i understand. SWAP is kind of not so desirable on an SSD right? Because of the potential wear.
Maybe this is why its not even used already by default?

Any way should i delete Swap then? Because its actually disabled somehow on SSDs? Or is it actually still used? And its still ok to use it?

Thanks in advance,
Nikolai

---

### Post by kherring7383 on 2013-08-02
The more installed RAM you have the less the Swap will be used, in fact my Swap file is never used since I have 4GB of RAM. As for deleting, don't since it is a vital partition to the operating system. Here's a that may help link [http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)

---

### Post by CaptainMark on 2013-08-03
I'm no expert but I believe you can't hibernate without swap space.

---

### Post by Nikolai D. on 2013-08-03
But why does system monitor shows me that Swap is not used at all? Even when almost all RAM is used.

---

### Post by Irihapeti on 2013-08-03
Swap is not an essential part of the system. I'm using an EeePC 900 which has never had a swap partition on it. It works fine. You can't hibernate without swap equal to at least the amount of RAM, but you can suspend.

Your swap partition probably isn't being used because it isn't defined in /etc/fstab. If you want it to be used, you need to edit /etc/fstab as root, either with a terminal editor such as nano or vi, or with a GUI editor run with gksu (or equivalent). Add the following:
```
UUID=nnnnnnnnnnn none            swap    sw              0       0
```
to the end of /etc/fstab

In place of the string of nnnnns, add the UUID of your swap partition. To find out what it is, run the command
```
sudo blkid
```

For example, the relevant entry from my desktop machine reads:
```
/dev/sdb7: UUID="ca858886-6f4c-47a7-95b4-9bec3e3ce793" TYPE="swap"
```

You copy the number – it will be different on your machine – and add it in place of the nnnnnn that I've shown above.

Then run the command
```
sudo swapon -a
```
to enable swap.

---

### Post by Nikolai D. on 2013-08-06
look my swap line looks like this
# swap was on /dev/sda6 during installation
UUID=5f8018ef-6567-4e01-8464-21621d6f0173 none            swap    sw              0       0

edit:
ah blkid gives
/dev/sda6: UUID="5f8018ef-6567-4e01-8464-21621d6f0173" TYPE="swap"

edit2:
i think i only have to do swapon -a to enable it.

But what actually is interesting to me. Im actually considering deleting swap and extending my root partition. Because Win 7 already consumes most part of my not that big ssd drive in the first place. So from 120 of my ssd, my linux partition is basically only 20 gigs. And A view gigs are used by other system recovery partitions and swap ofc. So my linux install is kinda on a low diskspace. And additional view gigs would be cool.
And what i am actually thinking about now. Is how normal or not normal it is to use Swap on an SSD? I suppose its basically just ok. But since i want a bit bigger system partition it is ok to remove it eventually.

---

### Post by Irihapeti on 2013-08-06
I was expecting that you'd find the UUIDs were different, but they look the same. I'm not sure why it's not working.

---

### Post by Nikolai D. on 2013-08-06
> **Irihapeti said:**
> I was expecting that you'd find the UUIDs were different, but they look the same. I'm not sure why it's not working.

thank you for instruction :)

---

