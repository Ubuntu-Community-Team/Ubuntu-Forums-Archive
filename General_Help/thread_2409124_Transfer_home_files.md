---
title: "Transfer home files"
date: 2018-12-28
forum: General Help
---

### Post by PantherStu on 2018-12-28
Hi all. Long story short, my father's computer with Ubuntu 18.04 has had the graphics card die, and due to age of computer it is not worth getting new graphics card, and decision was made to just get him a new computer and put Ubuntu onto it.

So my question, is there anyway we can transfer the home folder from his old computer to new one, considering we can't log in or see old computer??

Thanks in advance for your help.

---

### Post by Irihapeti on 2018-12-28
You'd need to remove the hard drive and either install it in a new computer or install it into an external drive case. It's not necessary to boot from the drive in order to get the files off; you just need to be able to access it.

Another option would be to boot from a live CD or USB that has a SSH server and then connect to that using another computer. That might be the more complex of the two operations, though it doesn't involve tinkering with hardware.

---

### Post by liaata on 2018-12-28
External drive is the way I would go

---

### Post by ajgreeny on 2018-12-28
You might be able to boot to a command line on the old machine, depending on the hardware it has and then simply copy all the old /home/user files from there to either an external hard drive, or even several USB flash drives if there is not a huge amount of files to copy.

I would do what Iripaheti says and use an external caddy for the old disk as I already have one, but you may find it easier to put the old disk in a new machine if it is not too difficult, which it may be if using a laptop.

One way or another, it is not too difficult a job to do.

---

### Post by HermanAB on 2018-12-29
You could stick a USB-VGA adaptor into the old machine.  They are not expensive - less than $10. 

Being a Linux machine, this type of adaptor will work immediately without any setup hassles.

---

