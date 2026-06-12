---
title: "Data recovery from virus affected hard drive from Windows machine."
date: 2008-01-10
forum: General Help
---

### Post by vishnumrao on 2008-01-10
Hi all,

I have a friend's hard drive from his virus affected Windows machine. I wish to try to do data recovery, by plugging as a secondary drive on my Ubuntu machine. 

Two questions:
1. Are there any precautions that I need to take so that the virus does not affect my data?
2. Once I recover the data how can I cleanse it from the virus. I am afraid that, I might copy over the virus files too while doing the recovery, which will again screw up the windows machine.

Thanks in advance,
Vishnu Rao.

---

### Post by erpo on 2008-01-10
These days, worms pose more threat to Windows machines than viruses. I know of no worms (or viruses for that matter) that affect both Windows and Linux machines, so you should be safe. Nevertheless, don't use wine to execute any programs on your friend's drive. You shouldn't have to do that during data recovery anyway.

To try to remove (or at least detect) the infected files, you could try clamav. I've never used it, so YMMV. Also, not all antivirus programs are able to "cleanse" all files. Some files you may have to delete.

Good luck.

---

### Post by bodhi.zazen on 2008-01-11
> **vishnumrao said:**
> Hi all,

I have a friend's hard drive from his virus affected Windows machine. I wish to try to do data recovery, by plugging as a secondary drive on my Ubuntu machine. 

Two questions:
1. Are there any precautions that I need to take so that the virus does not affect my data?
2. Once I recover the data how can I cleanse it from the virus. I am afraid that, I might copy over the virus files too while doing the recovery, which will again screw up the windows machine.

Thanks in advance,
Vishnu Rao.

Well, a few thoughts.

First, your Ubuntu install will be just fine. If you are worried about it , just boot a live CD.

Second, wine really can not run Windows viruses.

Third, the best method of data recovery is, well, restore from backup :lolflag:

If you are going to attempt data recovery, IMO, the first step is to identify the virus / worm etc. If you use Linux tools you need to be careful as : 
1. IMO there are a lot of false positives and 
2. The linux tools are not so good at cleaning such things. They are typically designed with the idea that they run on mail servers and the only option is usually to delete the file.

You may be best off copying the data and scanning it with a Windows scanner.

---

### Post by bodycoach2 on 2008-01-11
I highly suggest using a Helix for this purpose:
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

Helix has tools specifically for this problem. Helix is a Forensics type of Linux distro, and a tool most IT people should have on hand.

More than likey, the personal data hasn't been effected. You can run a scan on individual files and folders with Helix. Move those files to another hard drive. Once you've rescued the files, Dban the compromised drive:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
I recommend using the autonuke option after a malware attack.

You can then reuse the drive for any purpose. I recommend having your friend use Ubuntu, of course. 

Tell your friend:
If you run a Windows install disc backwards, you hear Satanic sayings. But what's worse is that if you run it normal, it installs Windows!

---

### Post by vishnumrao on 2008-01-11
Thanks guys for your inputs. 
Here is what I will try. Using a live cd and copy the data to a external usb drive. And then scan for virusses on a windows machine.

> **bodycoach2 said:**
> Tell your friend:
If you run a Windows install disc backwards, you hear Satanic sayings. But what's worse is that if you run it normal, it installs Windows!

I have been trying to get him to try Ubutu. Maybe this is a hard lesson for him. I hope he tries Ubuntu now.

Once again thanks.

Vishnu Rao.

---

### Post by vishnumrao on 2008-01-11
I tried using the Gutsy cd as a live cd. But I am unable to access the partition. There are a couple of restore partitions which I am able to access. 

My friend had mentioned that there was a boot sector virus(I have no clue what it is.). Please see the attached screenshot for the error that I am getting.

Any suggestions.

---

### Post by bodhi.zazen on 2008-01-12
You will have to force a mount. How to do this is on the screen :

```
sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
```

---

### Post by vishnumrao on 2008-01-12
Master roaster, 

Thanks for your input. Forcing mount did not work either. On a hunch that there might be bad sectors, I tried a gparted live cd and tried to run a check on the drive. Yes, it has bad sectors too. So what are my options. I do not enough free space or an extra drive to clone this drive to another drive. There is just about 50 Gb of stuff on this 250 Gb drive.

---

### Post by bodhi.zazen on 2008-01-12
To be honest, you might consider data recovery from windows.

Options on Linux would include testdisk :

[Test Disk wiki](http://www.cgsecurity.org/wiki/TestDisk)

And photorec : 

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Or a disk like bodycoach2 mentioned.

---

### Post by vishnumrao on 2008-01-12
Ok. I created 250 Gb of free space in my main drive that has Gutsy. I intend to use [this tutorial written by aysiu]("http://www.psychocats.net/ubuntu/partimage"). My question is once I create the image in a backup directory will I be able to access the contents in the image from within Ubutu?

---

### Post by vishnumrao on 2008-01-12
I want to be Windows free. Wish to work it out using only linux based options. But thanks for the suggestion.

---

