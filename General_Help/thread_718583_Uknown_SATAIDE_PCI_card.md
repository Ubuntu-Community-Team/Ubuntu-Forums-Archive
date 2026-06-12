---
title: "Uknown SATA/IDE PCI card"
date: 2008-03-08
forum: General Help
---

### Post by parallaxedlife on 2008-03-08
Hello,

I have purchased a SATA/IDE PCI card from the newegg website. not really doing the amount of research that I should have done, I don't even know if this card has ever worked on anyones' computer.  So here is my problem, I have the card inserted and a 500GB SATA drive plugged into it.  after poking around i can't find the drive anywhere. My next step was to use the commands: "lshw and lspci" the relevant results are as follows

lspci:

01:09.0 RAID bus controller: VIA Technologies, Inc. Unknown device 3241 (rev 50)

lshw:

*-storage:0 UNCLAIMED
                description: RAID bus controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: latency=32

I have also attempted to use "modprobe" and the following 
sata_inic162x  sata_promise   sata_sil24     sata_sx4       sata_vsc
sata_mv        sata_qstor     sata_sis       sata_uli
sata_nv        sata_sil       sata_svw       sata_via

it is possible that i'm not doing that correctly but it didn't improve my situation.

Here is a link to the newegg product id page from which this was purchased, I hope this helps in helping me.

[http://www.newegg.com/product/product.aspx?item=N82E16815280001](http://www.newegg.com/product/product.aspx?item=N82E16815280001)

I Thank you for your time in advance,

John

---

### Post by fjgaude on 2008-03-08
The card has what is called fakeraid... is a Silicon Images or VIA chipset...

After you have booted Ubuntu, at command line run:

```
sudo dmraid -tay
```

Tell us what you get. From there you will be able to mount the drives, array. Then put a line in your /etc/fstab file so it mounts on bootup.

---

### Post by parallaxedlife on 2008-03-14
Sorry for the late reply, I just got back from vacation.

so after running the command:

sudo dmraid -tay

i get this 

"no RAID disks"

---

### Post by fjgaude on 2008-03-15
Okay, you have to run some kind of BIOS function to get the drives to be in a raid array. At startup go into the BIOS and see what options you have to make the raid active, and then setup the drives to be whatever raid is offered, what you wish it to be. Or did you have some software that permits you to setup the array outside of the BIOS?

Then boot up and do the -tay command. Then we can mount the array, and finally put a line in the /etc/fstab file to have it mounted automatically when you boot.

Let us know how you are doing.

---

### Post by parallaxedlife on 2008-03-15
Hello,

I have figured out the problem,  the SATA PCI card works just fine, I managed to get ahold of another SATA Drive and plugged it in.  the Drive was found as it should be.  it turns out that my hard drive is non-functioning, doesn't even powerup.

Thank you for all of your help, i appreciate it.

John

---

### Post by fjgaude on 2008-03-15
You mean you weren't trying to go raid array afterall... I need to read and remember more closely. <smile>

So a failed 500G drive, that's strange, strange indeed. Drives seem to be so reliable these days compared to three or more years ago.

Anyway, glad to see you solved your own problem... sooner or later we all become detectives.

---

