---
title: "testdisk + USB partitions lost"
date: 2013-03-16
forum: General Help
---

### Post by professor-g on 2013-03-16
Hi All,

Need help recovering data on a USB stick.
Have tried multiple times on my own with testdisk - with no success.

Device + History:
KINGSTON DT R500 USB (16GB USB-2)
When saving a file a few days ago, it just decided to hang and do nothing, then disappeared.
Thus far have done nothing to further corrupt.

Suspect I need to define/size partitions for it.

Current Status:
USB doesnt come up on my machine (running ubuntu 12.04).
dmesg shows the following (and that partition table is KAPUT)

--
[58813.840044] usb 1-3: new high-speed USB device number 5 using ehci_hcd
[58813.975802] scsi10 : usb-storage 1-3:1.0
[58815.015144] scsi 10:0:0:0: Direct-Access     Kingston DT R500          PMAP PQ: 0 ANSI: 0 CCS
[58815.015771] sd 10:0:0:0: Attached scsi generic sg6 type 0
[58815.886886] sd 10:0:0:0: [sdf] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[58815.887504] sd 10:0:0:0: [sdf] Write Protect is on
[58815.887509] sd 10:0:0:0: [sdf] Mode Sense: 23 00 80 00
[58815.888131] sd 10:0:0:0: [sdf] No Caching mode page present
[58815.888136] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[58815.891126] sd 10:0:0:0: [sdf] No Caching mode page present
[58815.891130] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[58815.894881]  sdf: unknown partition table
--

Tried on a windows machine - USB appears on there.
Used testdisk 6.14 + 6.13, they want the machine to go online - which that machine cannot.

Used testdisk 6.10 successfully (log file attached)

First attempts with search did nothing.
Refined geometry to have 1 head 1 sector - did search, the deeper search.
Nothing.

I paste relevant portion of the .log file below
(tried attaching log file, it wont allow)

Please advise what to do next.

Thanks,

G.

--
search_part()
Disk /dev/sdb - 8388 KB / 8192 KiB - CHS 16384 1 1
file_read(5,16,buffer,3(3/0/1)) read err: Invalid argument
file_read(5,1,buffer,3(3/0/1)) read err: Invalid argument
file_read(5,1,buffer,4(4/0/1)) read err: Invalid argument
...
[truncated section]
...
file_read(5,1,buffer,16402(16402/0/1)) lseek err Invalid argument
file_read(5,1,buffer,16520(16520/0/1)) lseek err Invalid argument

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
file_read(5,16,buffer,0(0/0/1)) read err: Invalid argument

Partition: Read error
Store new MBR code
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
--

---

### Post by varunendra on 2013-03-16
Did you try PhotoRec in full disk scan mode?

Since it looks for headers and doesn't care for partition table, it may have more chance of recovery.
Alternatively, you may try trial version of a commercial software - Get Data Back (my previous most favourite, after trying a bunch of top rated apps), although I have recently had more luck with testdisk/photorec.

Trial version of any commercial software will scan and give you a list of files it can recover. Some can even let you save files upto a specific size. But if you haven't tried photorec yet, give it a go first. It's super fast and has been most promising in my personal experience.

---

### Post by professor-g on 2013-03-16
Hi Varun,
Thanks for quick reply.
Tried photrec - but not as intensively (i.e. obsessively compulsively).
How does one select full disk scan mode.
G.

---

### Post by varunendra on 2013-03-16
It asks itself before actually starting the scan, you must have answered that screen (free/whole).

---

### Post by professor-g on 2013-03-16
> **varunendra said:**
> It asks itself before actually starting the scan, you must have answered that screen (free/whole).

Doesnt provide that option.
It also adds note/warning that the partitions must be correctly sized to allow for recovery.
It is clearly NOT correctly sized as it shows the whole drive as having no partition at all and having a total size of 8Mb and not 16Gb

Dont want to resize and write partition-sizes without getting advice first.

---

### Post by varunendra on 2013-03-16
Did you try deeper search in testdisk on Ubuntu ? Just yesterday someone mentioned in their thread that its windows version does not perform so well.

---

### Post by professor-g on 2013-03-16
> **varunendra said:**
> Did you try deeper search in testdisk on Ubuntu ? Just yesterday someone mentioned in their thread that its windows version does not perform so well.

As said in my original message, Ubuntu cannot recognise/see the drive (see dmesg paste-in).
Interestingly Windows can.

testdisk on linux is thus not possible

Thanks again for your help Varun.
G.

---

### Post by varunendra on 2013-03-16
Not arguing, but at least the drive IS seen by Ubuntu -
> **professor-g said:**
> 
[58815.894881]  **[COLOR="#FF0000"]sdf[/COLOR]**: unknown partition table

It only can't see the partition since the partition table is corrupt, and testdisk is all about recovering/correcting partition table.

That's why I'm asking you - did you even run testdisk? I'm sure it will detect the drive. Don't worry about the drive not showing up in the file browser, as it only shows those which it can get basic info about.

---

### Post by professor-g on 2013-03-16
True !!! You are correct !!!

Ubuntu DOES see it (hence dmseg results), but is not happy with its size.
Testdisk on Ubuntu DOES NOT see it.
is there any way to 'force' it to see it ... ?

Maybe defining / sizing a partition with the windows version?
But I dont know what sizes for the partition(s), sectors, etc... I should be using 

Any ideas?

G.

---

### Post by tgalati4 on 2013-03-16
USB and all flash drives in general should not be formatted with linux tools--sadly.  It looks like you created some partitions on your 16GB drive, but somehow during a reformat of a partition or the entire drive, the Cylinder, Head, Sector count (CHS) got messed up.  This is one area that Windows actually handles better--maintaining CHS counts on flash drives during a format.

When you have a problem with an SD card, the usual advice is to put it in a camera and reformat it.  That also resets the correct CHS when formatting, so it is usable again.

My advice, and I have done this:  Buy an identical USB flash drive.  Identify the CHS count.  Write it down!  Find a Windows machine and use the Format command with the appropriate CHS switches with the numbers that you discovered from a brand new flash drive.  The faulty drive should now be working.  Don't partition or format (mkfs) using linux unless you know what you are doing.  Unetbootin and other flash boot install methods are raw-writing an ISO image to an already-formatted (typically FAT or FAT32) flash drive, so that they work properly.  Other boot installers (like DSL, Tiny Core, Slitaz) create a data partition after a boot partition and they seem to work, but I don't know if they are ext4 or still vFAT.

I don't know of a way to fix the CHS count without a format--that is really what you need.  I would try testdisk and photorec under Windows and see if you can get any recovery.

---

### Post by varunendra on 2013-03-16
> **professor-g said:**
> Testdisk on Ubuntu DOES NOT see it.
is there any way to 'force' it to see it ... ?

While I believe there must be a way, I personally don't have the knowledge or experience of doing that. So I'm clueless at this point, sorry.
If you haven't already, I suggest you check the documentation/guides on testdisk's website for recovery in this situation. If nothing relevant is given there, then tgalati4's suggestion of manually entering values from an identical working drive is a good one.

Since partition table and data area are separate, even if you make a mistake in partition table, testdisk/photorec should be able to recover files once it gets a partition to work on. Just make sure not to do anything that 'writes' on the data region of the disk.


@ tgalati4,
> USB and all flash drives in general should not be formatted with linux tools--sadly. It looks like you created some partitions on your 16GB drive, but somehow during a reformat of a partition or the entire drive, the Cylinder, Head, Sector count (CHS) got messed up. This is one area that Windows actually handles better--maintaining CHS counts on flash drives during a format.
While I very much respect your knowledge and experience you share on the forums, I must say I strongly disagree with you on this point.

Apart from occasional compatibility issues that I have only seen on internet so far (but haven't experienced myself even with same apps/tools), I don't see anything wrong with how Linux tools handle these drives or partitions on them.

Besides HDDs, I must have put a Live OS on more than 3-4 dozen thumb drives + some memory cards so far. And for the last two years or more, the first thing I do with every thumb drive that comes into my hand is creating 3 primary partitions on it - 1st fat32 for storage, 2nd ext3 for casper-rw and 3rd fat32 for a live OS.

I have never suffered any compatibility issues with any of the devices I have handled so far. And that includes a variety of HD camcorders, both consumer and professional class still cameras, mobile phones, digital players and of course a wide variety of laptops/PCs. I have been frequently changing/deleting/recreating partition layouts on these drives whenever I need more space or there is some specific requirement, and no application or device has ever complained so far.

Even the cases that I see on the net/forums where a flash drive formatted on windows boots but not when formatted on Linux, I have noticed one thing that people forget to put the boot flag on the partition whereas windows does that by default. Then they tend to believe there is some 'unknown' discrepancy in formatting 'standards' in Linux tools.

As long as a 'standard' is well defined and available to all, I don't see anyone following it better than Linux tools. Problem arises when some particular app/device decides to follow the MS version of the 'standard', not the real standard. For example the 'acpi' standards of most motherboard companies, which in fact aren't acpi standards at all !

Sorry if I sounded like arguing, but Linux tools have earned so much trust of mine that I simply couldn't resist to express my difference of opinion.

---

### Post by tgalati4 on 2013-03-18
My experience has been otherwise.  I have successfully recovered SD cards and USB flash drives that were mangled by something within Linux.  Especially moving between Mac, Windows, and Linux.  While I also generally trust Linux partition and mkfs tools, there is something about flash drive controllers that can cause them to become unreadable after extensive partition manipulation within Linux.  And these are brand-name, well-respected names in flash drives.  So my experience may be an outlier, and perhaps alarmist, but that has been my experience.

Your observations are valid and your experience points to the safety of using Linux tools to handle flash drives.

---

