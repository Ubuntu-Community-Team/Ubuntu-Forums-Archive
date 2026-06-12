---
title: "Issue with USB back up drive not seen"
date: 2020-04-25
forum: General Help
---

### Post by oilyfish on 2020-04-25
OS is  19.04

 My  old 4TB back up drive  bit the dust.  
So I ordered a new one.[SIZE=3]   A  WD Gold 4TB Enterprise Class Hard Disk Drive - 7200 RPM Class SATA 6 Gb/s 128MB Cache 3.5 Inch - WD4002FYYZ [/SIZE] 
    The slower cache was cheaper. 

I use an out board  USB fed Thermaltake  drive port for this.
I have a lap top and a workstation  Neiuther  can see this drive.  G parted can not see this drive 

 I powered my workstation down and  plugged  the 4 TB drive into one of my front bay drive ports and booted  the machine.
The boot sequence was taking for ever  like two minutes passed and it hadn't booted 

Tell me  is you can  is this  Looooooong boot up  to be expected because the big drive is being scanned? 

Or  does it seem the drive is shot and   I should send it back?

---

### Post by CelticWarrior on 2020-04-25
How is it connected? SATA or USB? 

What is a "Thermaltake  drive port"? What is a "front bay drive port"? All iof this is meaningless if you don't specify the connection type you're using in either case.

---

### Post by oilyfish on 2020-04-25
USB like I said in the title
  Thermaltake is just a brand  of external USB  drive  bays   [https://www.amazon.com/dp/B01GF0OYI2?tag=duckduckgo-d-20&linkCode=osi&th=1&psc=1](https://www.amazon.com/dp/B01GF0OYI2?tag=duckduckgo-d-20&linkCode=osi&th=1&psc=1)
Thing is  it  works fine  with other drives  IT's what I use for back ups  but   This new drive is not being seen  so I can't format it  G parted doesn't see

---

### Post by CelticWarrior on 2020-04-25
I know nothing about this one in particular but many other similar dock stations have a capacity limit. Nothing is mentioned here though: [https://www.thermaltakeusa.com/blacx-hdd-docking-station.html#additional](https://www.thermaltakeusa.com/blacx-hdd-docking-station.html#additional)
And if your old 4GB HDD worked with the same docking station then it is not a limitation. But it can be some other wierd incompatibility.
The only way to make sure is by testing the drive in a native SATA connection.

---

### Post by oilyfish on 2020-04-25
> **CelticWarrior said:**
> I know nothing about this one in particular but many other similar dock stations have a capacity limit. Nothing is mentioned here though: [https://www.thermaltakeusa.com/blacx-hdd-docking-station.html#additional](https://www.thermaltakeusa.com/blacx-hdd-docking-station.html#additional)
And if your old 4GB HDD worked with the same docking station then it is not a limitation. But it can be some other wierd incompatibility.
The only way to make sure is by testing the drive in a native SATA connection.

That would be what I mentioned above  in one of my front load drive bays.  The boot sequence was  endless.  Never booted.   Haven't yet  taken a look at what the BIOS sees.  

My main board  should not be too old for this drive It's an ASUS X79 Deluxe the SATA is  rated at 6Gb/s.  I considered maybe I should jumper it to run slower but I can find nothing  on that for a WD drive

---

