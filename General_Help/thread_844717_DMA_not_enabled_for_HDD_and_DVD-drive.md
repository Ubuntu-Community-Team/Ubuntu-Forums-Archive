---
title: "DMA not enabled for HDD and DVD-drive"
date: 2008-06-29
forum: General Help
---

### Post by FFighter on 2008-06-29
Hi folks,

I'm trying to optimize my system's performance. I have a HP dv6448SE laptop which is a Core 2 Duo T5250 1.50Ghz, 2GB RAM, 250GB SATA HDD.

I just did a quick research and found out an article teaching about hdparm and DMA settings, I then checked out if my HD and DVD-drive had DMA enabled, here's the output I've got: 

> marcelo@marcelo-laptop:~$ sudo hdparm /dev/sda
[sudo] password for marcelo: 

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0
marcelo@marcelo-laptop:~$ 


Something very similar is also shown for my DVD-drive:

> marcelo@marcelo-laptop:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
marcelo@marcelo-laptop:~$ 


Hmmm... strange. As you can see, the HDIO_GET_DMA attribute failed to be fetched. The two others too. For the DVD-drive, the HDIO_GETGEO also failed like the two others. I don't know what this message means really, nor what ioctl is.

Another strange thing is the value of the IO_support attribute. Is 16-bit really correct? I mean, my system does not have a hight-end configuration, but it is still good hardware for today's standards, should this thing be running in 16-bit mode? (Pardon the ignorance).

I then have tried to activate DMA on sda:

> 
marcelo@marcelo-laptop:~$ sudo hdparm -d1 /dev/sda
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
marcelo@marcelo-laptop:~$ 

Same error message.

Is there anything wrong here? If so, how could I fix it so that I can get the maximum performance out of my HD and DVD-drive I/O ?

---

### Post by kuja on 2008-06-29
That looks correct, and - unless everything is extremely slow - that should be normal.

Take a look at hdparm -i /dev/sda and see if there's an asterisk next to one of the udma's to be sure, also take a look at sudo hdparm -d /dev/sda and it will tell you its on/off state.

As per the 16-bit I/O, I'm not sure what it refers to exactly, but that's normal also.

---

### Post by RAOF on 2008-06-29
hdparm almost certainly isn't the right tool; at least your hard drive uses the SATA interface (which, among other things, always uses DMA) and this interface isn't supported by hdparm - it's PATA/IDE.  Unless that's changed recently, of course :).

---

### Post by FFighter on 2008-07-01
> hdparm almost certainly isn't the right tool; at least your hard drive uses the SATA interface (which, among other things, always uses DMA) and this interface isn't supported by hdparm - it's PATA/IDE. Unless that's changed recently, of course . 

So, which tool should I use to tune up SATA drives?

---

### Post by kuja on 2008-07-01
They should already be performing at their best without effort .... Try to benchmark their performance in some way or another, like by peforming a huge file transfer or something, you'll see what I mean :)

---

### Post by Vivaldi Gloria on 2008-07-01
AFAIK, you cannot enable or disable dma (or udma) for sata drives, they use a different protocol.

```
vivaldi:~$ sudo blktool /dev/sda dma
[sudo] password for vivaldi: 
HDIO_GET_DMA: Inappropriate ioctl for device
```

---

### Post by FFighter on 2008-07-05
So, there isn't much (if any) optimizations one could do for Serial ATA drives on Linux ?

---

### Post by Vivaldi Gloria on 2008-07-05
> **FFighter said:**
> So, there isn't much (if any) optimizations one could do for Serial ATA drives on Linux ?

All I can think of is that if you use ext3 then keep them less than %80-85 full so that the drives don't get fragmented. 

Also use smartctl once in a while to check their errors.

---

### Post by UrbanFallout on 2008-07-06
To get DMA working on your ATAPI DVD drive you could try this:

Type the following:
```
 sudo gedit /etc/modprobe.d/aliases 
```

And add the following lines to the bottom of the file:
```

## Turn on DMA for DVD ############################
alias ata_generic off
alias pata_atiixp on

```

I'm not quite sure why this works, but I think there is something wrong with the generic ATA module. If anyone can better explain why this is please feel free to add a comment below.

Note this worked when I had the following symptom when running
```
 dmesg | grep ata 
```
one of the lines was:
> 
ata2.00: simplex DMA is claimed by other device, disabling DMA


---

### Post by erythrocyte on 2008-07-20
> **FFighter said:**
> So, there isn't much (if any) optimizations one could do for Serial ATA drives on Linux ?

Have you looked at the sdparm package yet? Maybe that's what you need.

---

