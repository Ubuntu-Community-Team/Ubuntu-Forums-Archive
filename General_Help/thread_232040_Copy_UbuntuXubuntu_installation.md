---
title: "Copy Ubuntu/Xubuntu installation"
date: 2006-08-08
forum: General Help
---

### Post by seshomaru samma on 2006-08-08
I would like to install Xubuntu on a computer , download several programmes , tweak it , set it the way I like and 'clone' it to several other computers (6 actually).

I have looked for similar threads and [this one]("http://ubuntuforums.org/showthread.php?t=226495&highlight=clone+ubuntu") suggested using partimage  (offering [this ]("http://www.psychocats.net/ubuntu/partimage.html")guide). This looks like a good advice except that I would like to install it simultaniously and I only have one internet access ( I will need internet to download partimage to the Ubuntu install disc)

Is there a different way?
Can I use Norton ghsot?
Or maybe Knoppix?

---

### Post by seshomaru samma on 2006-08-11
If anyone is interested here is what I did:
I intended to install Xubuntu on 6 very old computers with 128M memory and old hardware. My boss was so impressed with the idea (of using very old and CHEAP machines) that she got 6 more.
I didn't want to go thru the installation process + apt-getting software on each machine ,especially since some of the programmes are very large. As these machines are going to be used by people who are not interested in learning how to wOrk with XFCE , I had to create desktop shortcuts to everything and tweak it to the easiest possible setup.
I did not use partimage with Xubuntu's live CD for several reasons:
1) The live CD is SUPER slow on those machines, I hope that one day there will be an option for the live Cd will be able to mount the system without a GUI interface
2) I will have to download partimage from the net every time I boot the live CD , I hope that one day partimage will come with the live CD

I set a new hard disk as slave and tried with Knoppix first
Knoppix boots much faster than Xubuntu and has partimage built in, but I got lost in permission problems. I think that someone with a better command of the terminal might have been able to do it easily , but I just couldn't figure it out.

I then booted an old Norton Ghost CD (Ghost 8.0 , I think) which is used for DOS machines . I copied an image of the old hard disk into the new hard disk  in 5 minutes.

I couldn't ,however , boot from the new hard disk and got a grub error . I suspect that the best way to fix it would have been with Knoppix , but I don't know how. Instead I had to boot from the live CD and fix it through the terminal with 

```
sudo grub
find /boot/grub/stage1
```
and put that input into :
```
root (hd?,?)
setup (hd0)
quit
```
I was then able to access my new system which was an exact clone of the first one. Within 3 hours I had 11 new Xubuntu machines (1 didn't work for some reason , probably defect hardware).
I believe that if I had known how to restore grub with Knoppix I could have done it much faster.A if there is a non graphic tool , I could have had all 10 machines cloned in about an hour.
I hope my account can help in same way to those who are planning something similar.

cheers

---

