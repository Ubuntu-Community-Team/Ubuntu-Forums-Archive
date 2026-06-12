---
title: "No copy progress meter in Files app"
date: 2023-05-11
forum: General Help
---

### Post by temporos on 2023-05-11
When I copy large files between drives (internal or external) in the Files app, there is no meter or indication of the progress of the copy operation. It appears as if the file has immediately copied, even if the file is several GB in size.

For example, when I copy a 1 GB file from my internal SSD to an external SD card, it should take several seconds to fully copy to the card, but Files says the file is immediately copied. Then, when I attempt to eject the SD card, Ubuntu shows a warning that says files are being written, and the drive shouldn't be removed. When I try later, after the file has had enough time to copy, I can eject the SD card just fine.

Why is there no progress meter in the Files app when performing a large file copy operation?

I'm using Ubuntu Desktop 22.04.2 LTS.

---

### Post by Dennis N on 2023-05-12
There is a progress circle that appears on the window top bar. Also, if you click on the circle, you get a popup showing a progress bar and speed. Please see the screenshot &#8595;

The computer has finished transferring data and reports completion, but writing all bytes from the SSD drive cache may not be finished, so you can't remove the drive.

---

### Post by temporos on 2023-05-12
> **Dennis N said:**
> There is a progress circle that appears on the window top bar.

No, that's the problem. That circle doesn't appear. I remember that circle from earlier, but I haven't seen it in a couple months now.

---

### Post by TheFu on 2023-05-12
> **temporos said:**
> No, that's the problem. That circle doesn't appear. I remember that circle from earlier, but I haven't seen it in a couple months now.

Linux/Unix systems use RAM for disk buffers.  You can see how much is being used with the 'free -hm' command.  The time it takes for the GUI to think the copy is completed is very different from the time it takes to actually write all the bits to storage.  To my knowledge, there's no way for the GUI to access this final, completed, information, since it happens well below the user-layer.  All Unix systems do this.

As end users, we can force all the buffers to be flushed either by asking the OS to **umount** the storage or by entering the '**sync**' command, twice.

From the sync manpage ... check your system :
```
NAME
       sync - Synchronize cached writes to persistent storage

SYNOPSIS
       sync [OPTION] [FILE]...

DESCRIPTION
       Synchronize cached writes to persistent storage

       If one or more files are specified, sync only them, or their containing file
       systems.

       -d, --data
              sync only file data, no unneeded metadata

       -f, --file-system
              sync the file systems that contain the files
...
```
When I was learning Unix, my mentor said to type out sync twice - not to copy/paste the command so that 99% of the time, by the time I entered the command for the 2nd time, the first sync would be completed.  This was long ago when we didn't have 10GB+ files, but it was common to have 50 concurrent users on each system.

The goal of Unix GUIs is to give the control back to the end-user ASAP and let things that can take longer to complete in the background.  This is different from other OSes, but that should be expected, since they are different OSes.

---

### Post by temporos on 2023-05-15
@TheFu
That's really good insight, thanks. But it would be nice to see the progress of the copy process. The only way to know if the data write has been completed, I have to wait for the sync command to do its thing (with just a blinking cursor in the meantime). Depending on the files being copied, that can take a very long time with no indication of how much longer it'll take.

---

### Post by tea for one on 2023-05-15
> **temporos said:**
> No, that's the problem. That circle doesn't appear. I remember that circle from earlier, but I haven't seen it in a couple months now.
Have you changed your theme?

---

### Post by sudodus on 2023-05-15
If you want to see the real progress including flushing the buffers (from RAM to the target drive), you can use **[FONT=Courier New]watch-flush[/FONT]**.

It is a tool, that belongs to the [program package mkusb](https://help.ubuntu.com/community/mkusb) but when installed you can use it separately. It is a text mode program, that you run in a terminal window, and

- after the copy command has started,
- start **[FONT=Courier New]sync[/FONT]** in a terminal window
- and then **[FONT=Courier New]watch-flush[/FONT]**

and it will help you see the progress of flushing the buffers (fast or slow depending on the write speed of the target drive).

---

### Post by TheFu on 2023-05-15
> **temporos said:**
> @TheFu
That's really good insight, thanks. But it would be nice to see the progress of the copy process. The only way to know if the data write has been completed, I have to wait for the sync command to do its thing (with just a blinking cursor in the meantime). Depending on the files being copied, that can take a very long time with no indication of how much longer it'll take.

Feel free to code up a solution that provides this data so that GUIs can access it.  It has never been that big of an issue to me.  I know that flushing data to an NVMe SSD will be faster than flushing data to a cheap, no-name, free USB2 flash drive.  The amount of time needed will be dependent on how much data needs to be flushed.  Of course, on systems with huge amounts of RAM, the buffers will be larger, so it will appear to take longer.  There are negatives to having too much RAM in a system.
Having too many processes read/write to the same storage device, even just to check progress, can slow things down too.  USB storage, especially, has issues when multiple processes try to access the same device - it is a known problem with the USB-storage subsystem.  This problem is just one of the reasons why SATA and eSATA and SAS storage should be used before USB storage is, whenever possible.

Unrelated, but there are negatives when network buffers are too large too.

---

