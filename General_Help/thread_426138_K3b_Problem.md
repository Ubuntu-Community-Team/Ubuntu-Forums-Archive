---
title: "K3b Problem"
date: 2007-04-28
forum: General Help
---

### Post by CheeseQueen452 on 2007-04-28
I wanted to burn Feisty to a disc for my mom, but K3b doesn't seem to recognize that I put a disc in the burner. HELP! Screenshot attached....

---

### Post by patrickfromspain on 2007-04-28
what cd/dvd burner do you have? It seems it isn't supported under linux..

---

### Post by CheeseQueen452 on 2007-04-28
It's a hitachi cd burner/dvd player. You can see the name & model number in my screenshot. It worked when I burned Edgy back in the fall(end of nov). At that time, I was using Xandros which was giving me trouble so I switched to Ubuntu. But it DID work..... What do I do?

> **patrickfromspain said:**
> what cd/dvd burner do you have? It seems it isn't supported under linux..

---

### Post by CheeseQueen452 on 2007-04-28
Anyone?

---

### Post by CheeseQueen452 on 2007-04-30
If anyone has a solution, please help!

---

### Post by jimbob on 2007-04-30
Does cat /etc/fstab show something like this?

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Some have reported that adding irqpoll on the grub kernel boot line helped in recognizing CD/DVD drives.  

Don't know if this is related to your problem or not.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-04-30
Well, it doesn't even play a dvd as it should. I think it died, so I'll have to replace it.

> **jimbob said:**
> Does cat /etc/fstab show something like this?

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Some have reported that adding irqpoll on the grub kernel boot line helped in recognizing CD/DVD drives.  

Don't know if this is related to your problem or not.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by goodtimetribe on 2007-06-28
> **jimbob said:**
> Does cat /etc/fstab show something like this?

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Some have reported that adding irqpoll on the grub kernel boot line helped in recognizing CD/DVD drives.  

Don't know if this is related to your problem or not.
&#65279;[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I have a similar problem, and I *know* my burner is fine. My problem only began after I formatted my drive and installed Kubuntu 7.04. I know it's a newer version of k3b too.

It's also the same medium I was previously using, and occurs with different brands of supported speeds. Problem occurs on two drives. One's a generic IDE16x, the other's a LiteOn SATA 18x.

I was excited to see a suggestion I hadn't tried, so I tried it, and it did not change my situation. 

The problem prevents me from burning disks sequentially, which is something I need to do for my redundant backup program. I'm looking for any kind of assistance with this.

I of course tried rebooting to make sure everything was properly remounted.

Thanks,

---

### Post by goodtimetribe on 2007-07-14
Still looking for a solution to this.

---

