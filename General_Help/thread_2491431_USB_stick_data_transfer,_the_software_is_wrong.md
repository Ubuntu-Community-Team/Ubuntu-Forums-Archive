---
title: "USB stick data transfer, the software is wrong"
date: 2023-10-08
forum: General Help
---

### Post by smeg2 on 2023-10-08
When transferring data to a USB stick the software reports that the data has completed transferring but the light on the USB stick keeps flashing for many minutes after indicating that there is still data being transferred, the software should not report that data transfer has completed until it actually has completed, I am sitting here waiting for data to complete transferring and it has been 10 minutes since the software reported transfer complete, I am sick of it.

---

### Post by sudodus on 2023-10-09
The transferring tool (copying or moving tool) writes via a buffer in RAM, and reports that it has completed the operation. Then a process in the background might still be busy flushing the buffer (writing from RAM to the memory cells). This is indicated by flashing light by some USB sticks. Please notice that the memory cells of some USB pendrives are very slow compared to other hardware. If too show, please get a [faster USB drive](https://help.ubuntu.com/community/Installation/FromUSBStick/pre).

You can check (and *should* check before unplugging) in order to get a reliable result, that the copying operation has finished all the way to the memory cells.

The command
```

sync

```
will give higher priority to flushing the buffers and when the terminal window returns to prompt the whole copying operation has reached the all the way to the memory cells.

It is even safer to **unmount all partitions on the drive before unplugging a USB drive.** Unmounting starts by flushing the buffers, and continues by making it impossible to continue writing to the unmounted partiitons.

```

[SIZE=3]sudo umount /dev/sdx*[/SIZE]

```
where x is the drive letter (a or b or c ...) and the wild card * makes **[FONT=Courier New]umount[/FONT]** find all partitions and try to unmount them. If it fails, you should finish  some program, that keeps the filesystem in the partition busy, and try to unmount again.

If you want to see the progress of flushing the buffers, you can install [mkusb](https://help.ubuntu.com/community/mkusb) which brings the tool
```

watch-flush

```
So first start unmounting the drive, and then in another window start **[FONT=Courier New]watch-flush[/FONT]**. As before, when **[FONT=Courier New]umount[/FONT]** has finished, you can unplug the USB drive (and quit from **[FONT=Courier New]watch-flush[/FONT]**).

---

### Post by Impavidus on 2023-10-09
The file copy tool writes all data to the file, then closes the file. It can write faster than the physical disk can accept, because the OS buffers the write operation. When the tool has closed the file, the copy is complete as far as the copy tool is concerned. If you now open the file with some different tool, you'll see the new contents, so in that sense the copy is complete.

Actually writing it to the hardware is a different matter. There's no guarantee that everything will be flushed as soon as possible. In fact, it may be better if it isn't. You may want to modify or even remove the file before unmounting the drive. In that case, delaying the write allows you not to write at all, saving write cycles. That's why you always have to unmount usb drives before pulling them out. For usb drives that were automatically mounted from the file manager, you can unmount them there too. Right-click on the usb drive and choose eject or something like that, depending on the exact filemanager you use.

---

### Post by TheFu on 2023-10-09
> **smeg2 said:**
> When transferring data to a USB stick the software reports that the data has completed transferring but the light on the USB stick keeps flashing for many minutes after indicating that there is still data being transferred, the software should not report that data transfer has completed until it actually has completed, I am sitting here waiting for data to complete transferring and it has been 10 minutes since the software reported transfer complete, I am sick of it.

This is a feature, not a bug. Working as expected. The other posters, with vast experience and knowledge, have both explained why and how it works.  Slow flash drives, connected to slow USB ports, running slow file systems (like FAT32) all add up.

GUI programs don't have any view as to when that copy process completes. They just now that the kernel file copy has said it has all the data, not when all the buffers are cleared. That's on the target device side.  These days, relatively cheap USB3 flash storage is available. If you need faster, get an external SSD  Cheap ones should be able to get to 550 Mb/sec writes over a SATA m.2 connection via USB.  That's pretty fast.  

As flash storage gets used, it slows down.  older flash storage slows much more than newer stuff where the vendors have all learned how to deal with write wear leveling better.  And you don't need to get expensive Samsung T3 SSD devices to get great performance.  Even mid-tier brands like AData and Patriot USB3 and USB 3.2 flash storage can be pretty quick.   

You can also use fast MicroSD u3 storage with a $10 USB3.2 adapter to get pretty good performance from $10-$25 microSD storage.  These have the bonus of being compatible with phones and tablets as well.  I have a $10 Kingston USB3.2 adapter for microSD and it does really great.  The Amazon number is: B085P5FDXQ, if you are interested.  It is noticeably faster than some old microSD to USB3 adapters that I have.

I took an old m.2 Micron 500G SATA SSD and put it inside a $13 external adapter (AMZ: B089GV3FYS).  That Micron SSD was previously used as an OS and VM storage for one of my systems, but after 3 yrs, I migrated with a fresh OS install to a Samsung 970 Pro NVMe SSD which is 10x faster, in theory.  That left me with a SATA SSD doing nothing,  The case is USB 3.2 and it shows.  For fun, pulled a large-ish video file from the HDD to the external SSD using rsync. This was a local copy.  

4.3GB file in :25 seconds .... 172.52MB/s  That's 1380Mbps.  Pretty fast, but I'd expect closer to 500MB/sec writes actually.  And the source storage for that file was a WD Black HDD - that's probably the slowdown.  Let me move the file to the NVMe storage and try again.  Eh .. my home ran out of room. Adding 10G to it quickly through the magic of LVM.

Ok, that's much faster, 458.93MB/s (3671.44 Mbps) in 9 seconds.    USB3 is 5Gbps.  USB 3.2 is 10 Gbps for the bus speed, but anything slower will make it less.  I was using a USB 3.2 port (red color USB) for the transfers, BTW.  With this last test, it is the Micron SATA SSD that limits how fast the copy can go. The file system on the external SSD is .... cough ... NTFS.  I use it with a video recording hardware device that only supports NTFS or FAT32 and FAT32 really sucks.

Hopefully, these different tests have made a point about choosing carefully how and which hardware you use. Huge differences are possible even when things appear to be the same, if they actually aren't.

---

### Post by HermanAB on 2023-10-10
Note that all USB widgets are not created equal.  If your widgets are slow - buy better faster ones!

---

