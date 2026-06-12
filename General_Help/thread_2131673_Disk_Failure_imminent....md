---
title: "Disk Failure imminent..."
date: 2013-04-02
forum: General Help
---

### Post by linuxlunatics on 2013-04-02
I get a dialogue box up every time I start my computer.

It refers to my hard disk and tells me that a disk failure is imminent. I ran a test from the BIOS that passed, so is my hard disk really about to fail?

Can anyone offer any advice regarding this?

I have included a screenshot of the window and what it says...

[ATTACH=CONFIG]240881[/ATTACH]

If you were to scroll down the list, you would see that it says something about the airflow failing in the past also.

Thanks so much people!

---

### Post by oldos2er on 2013-04-02
Hopefully you have good backups.

---

### Post by reeseslover531 on 2013-04-02
It seems like your BIOS isn't able to understand all of the SMART codes. SMART is a service that can report the health of your hard drive and it looks like a lot of sectors are being re-mapped. This means that the hard drive is trying to keep it self going but not using sectors that it can tell are bad. As that number goes up, the hard drive will run out of good sectors to map to and you'll start losing data.

Its almost impossible to figure out when the hard drive will fail, but I would backup your data as soon as possible and replace the hard drive. Thankfully, hard drives are cheap!

---

### Post by linuxlunatics on 2013-04-02
Thanks for your reply reeseslover531. I think I'll have to go get a new hard drive! Can I copy my entire OS onto another HD, then just plug it in?

This seems like as good I time as any to start building my own computer, something I've wanted to do for a while but vetoed by the girlfriend...lol

---

### Post by linuxlunatics on 2013-04-02
> **reeseslover531 said:**
> It seems like your BIOS isn't able to understand all of the SMART codes. SMART is a service that can report the health of your hard drive and it looks like a lot of sectors are being re-mapped. This means that the hard drive is trying to keep it self going but not using sectors that it can tell are bad. As that number goes up, the hard drive will run out of good sectors to map to and you'll start losing data.

Its almost impossible to figure out when the hard drive will fail, but I would backup your data as soon as possible and replace the hard drive. Thankfully, hard drives are cheap!

Thanks for your reply!

Can you tell me whether I can transfer my current OS and all it's files to a new hard disk the I'm going to buy and fit into my laptop?

---

### Post by Paqman on 2013-04-02
> **linuxlunatics said:**
> is my hard disk really about to fail?


Yes, you have 2862 bad sectors. In normal use a drive would have maybe 2 bad sectors. Your disk is massively knackered. Back up everything on there immediately and buy a new disk.

How old is the disk? Could be a warranty job?

Easiest way to transfer the whole system from one drive to another is to take the dying drive out of your laptop and plug both it and the new drive into a desktop computer, then just image one to the other using a tool like [Clonezilla]("http://clonezilla.org/"). Then slap the new drive into your laptop and you're laughing.

---

### Post by 3rdalbum on 2013-04-02
Sorry to say, but you have probably already lost data and you will probably lose more the longer you wait.

---

### Post by linuxlunatics on 2013-04-02
Listen Paqman, guys and girls...

Thanks so much for your replies, I will follow your advice. Luckily, I have hardly anything stored on this machine as I've only just started using it (it was forgotten about for a long time, and since my proper laptop was stolen not long ago, I whacked a copy of 12.04 on it and cracked away), so I haven't noticed any data go missing (about 59gb still free lol!).

Can anyone point me in the direction of a decent replacement drive? Something a bit larger (double the size possibly) and reasonable price as I'm a skint student.

Thanks again for all your help!

PS. My machine is an HP Pavilion dv5000

---

### Post by 3rdalbum on 2013-04-03
I can't point to a specific model, but Western Digital makes good hard disks and I have found them cheaper than competitors.

---

### Post by prodigy_ on 2013-04-03
You should make a clean install rather than transfer. It's safe to copy data (provided they're salvageable) but using system files that are potentially broken is unwise.

Re. replacement, I would seriously consider SSD but if you're sure you want HDD, [WD Black series](http://www.wdc.com/en/products/products.aspx?id=790) are probably the best because of 5-year warranty.

---

### Post by Paqman on 2013-04-03
> **linuxlunatics said:**
> 
Can anyone point me in the direction of a decent replacement drive? Something a bit larger (double the size possibly) and reasonable price as I'm a skint student.


If you're looking at magnetic drives (ie: not an SSD) then they're all pretty much equivalent. The only real difference in speed is the difference between 5400rpm and 7200rpm drives. You can get quicker ones, but they're a fair bit more expensive and IMO if you want speed and are prepared to pay for it you get an SSD.

I prefer Seagate or WD, but there's little between different brands in reality. Get any 2.5" SATA 7200rpm drive that is within your budget and the right size for what you need.

If I were you I'd seriously consider forking out a bit more and getting a small SSD and use something else for mass storage (USB sticks? SD cards? Cloud? NAS?). SSDs are the way to go in laptops.

---

