---
title: "my ubuntu experience + help on slow speed (harddisk)"
date: 2007-12-23
forum: General Help
---

### Post by ultimatsz on 2007-12-23
skip this if you are not interested.. it includes random hang issues and stuff like that
start from *** is the problem that i wanted to ask.. 

i first started using ubuntu when i hear about it at some forum... that is when i installed fiesty on my acer aspire 5583. it is good because somehow that model have problems with windows (screen flickers ALOT. playing video prevents it thou.. should be frequency problems but heck.. you will know why later), ubuntu has been fast for my laptop. i like the experience and the linux kernel is better than windows kernel.

i visited acer frequently prompting on the issue of the screen flicker problems for a long time. eventually they change a laptop for me. acer aspire 5584. i think the only differences is that 5584 uses 1gb ram and nvidia 7300 geforce go while 5583 uses intel accelerated graphics and 512ram.

i happily installed fiesty.. sadly.. it contains random lockup issues... i m not sure what i can do with it... at that time.. gutsy is coming out.. so i hoped that issue is solved by that time. i m a linux newbie at that time.

when gutsy came. i made a fresh install. compiz fusion is nice and stuff. but somehow my laptop still contains random hang issues. from this forum i see that it is the nvidia driver issue.. making making things and boot parameters like noapic nolapic  and other things like combined_mode = libata. all didnt work. this lasted for a long time.. it made my ubuntu experience bad.

recently i only then discovered that whenever there is a lockup, the system log will show ata1: slow to respond please wait then soft resetting port things. then i discovered that my harddisk cause the lockup issue.. looking around.. i found a solution. by changing harddisk from sda to hda. from what i know. my old laptop uses pata harddisk. i think ubuntu identifies my 5583 harddisk as hda. thus no problems.apparently when ubuntu is installed to my 5584 acer laptop, it idenitfies my harddisk as sda...  so after changing to hda... my laptop hangs no more.. i m so happy about it.









*** however.. after changing from sda to hda (no harddisk changed. only made ubuntu identifies my harddisk as hda. my harddisk should be pata, with sata controller) , startup becomes slow.. "reading files needed to boot lasted for 12secs or more where usually it lasted less than 3 seconds on sda" login after gdm is slower slightly.. opening applications are slower. somehow.. thou using xserver-xgl to prevent black flashes problem (er. i m aware that this starts 2 xserver sessions. xserver-xorg and xserver-xgl) , i have blured flashes sometimes when it becomes slightly slower.

thats not all... playing videos on youtube will lag slightly and playing videos that are are big will lag slightly too. is that because i m using hda?

anyways.. i made ubuntu identify my harddisk as hda from a website suggesting to do this:

```
sudo gedit /etc/initramfs-tools/modules
piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

sudo update-initramfs -u
```

can someone tell me is it because i have done something wrong that makes my laptop speed go slow? or is that because i m using hda thats why?


anyways.. 1gbram
nvidia 7300 geforce go
swappiness=10

---

