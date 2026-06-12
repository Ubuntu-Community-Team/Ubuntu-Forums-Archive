---
title: "Best way to add swap storage"
date: 2019-08-01
forum: General Help
---

### Post by AwaitingUserInput on 2019-08-01
Kubuntu 18.04.

I sometimes run out of RAM when I am editing a photograph, and this causes the program to crash. IT doesn't happen often, but for photos taken in certain conditions, I will crash the program. I am hoping to solve this by adding more swap storage.

I found this article that gives a few options for increasing swap space: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

My questions:
1) What's the easiest and most foolproof way to increase swap space? The article lists several, and I don't know what one to do.
2) Do I need to boot from a USB before doing this, or can I do it from a live system?

Thank you for any help.

Also:
```
[FONT=monospace][COLOR=#000000]$ swapon -s[/COLOR]
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       1003516 310828  -2
[/FONT]
```

[IMG]https://imgur.com/lUDM142[/IMG][COLOR=#FFFFFF][FONT=&amp][IMG]https://i.imgur.com/lUDM142.png[/IMG]

test[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-08-01
Adding a swap file is by far the easiest method.

[https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-18-04/](https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-18-04/)

That only creates a 1 GB swapfile; here are the steps for a 4 GB file.
```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=4194304
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

```
Then edit /etc/fstab so it will be activated at boot Use "sudo nano /etc/fstab" and add the line
```

/swapfile swap swap defaults 0 0 

```

---

### Post by AwaitingUserInput on 2019-08-01
Thank you very much for the help. I have multiple hard disks in this computer, and only one SSD. The rest are mechanical disks. I think I should put the swap file on the SSD, which is what I boot from. If I use your commands, will it put the swap file on the SSD?

I have edited the /etc/fstab file before so that my hard drive automatically mount when I boot the system, so I am familiar with that process.

---

### Post by mastablasta on 2019-08-02
not sure if swap on SSD is a good idea. however you have plenty of RAM and SWAP really shouldn't be used that often. so i would say go for it (current swap numbers you have are really are too low). after you create it i would reduce swappiness, so that swap file kicks in later when ram get's low.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

i did this on a USB key with server installed. my server doesn't really need 4 GB ram. still i created swap and it would start swapping when about 3.5 GB ram is occupied. normal RAM usage is i think below 0.2 GB

---

### Post by AwaitingUserInput on 2019-08-02
Thanks guys for the help. I went through the steps and added a 4GB swap file. Then I went back to a photo that would reliably crash my editing program when I tried to use it. Even though it was using lots of RAM and swap space, the program did not crash!!

I am going to mark the thread as solved. Thanks again.

---

