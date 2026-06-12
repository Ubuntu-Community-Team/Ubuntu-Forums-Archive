---
title: "Mistakingly reformatted USB drive, now need help."
date: 2014-03-18
forum: General Help
---

### Post by Heeter on 2014-03-18
Hi all,

I know that I am grasping at straws here, but I do need assistance.

I have a USB drive that was originally formatted to EXT4. I loaded it with a bunch of files.

I mistakingly reformatted it to EXT4 again. Is there any hope of retrieving those files?

Thanks

Heeter

---

### Post by Dave_L on 2014-03-18
There's a utility "photorec" (Recover lost files from harddisk, digital camera and cdrom), included in the package "testdisk", which is in the repositories.
[http://manpages.ubuntu.com/manpages/precise/en/man1/photorec.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/photorec.1.html)

I don't know if it can recover files after a reformat, but there's no harm in trying.

---

### Post by varunendra on 2014-03-19
If you have just reformatted it, nothing else, there is a pretty good chance that you'd be able to recover the whole partition (earlier one) with all the contents.

Please install testdisk -
```
sudo apt-get install testdisk
```

Then follow this guide to see if it can list the previous partition and the files in it : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If it can (refer to the 'P' key option after deeper search), you can choose to 'Write' that partition table to get the files back, or just copy the selected files to another place.

---

### Post by Heeter on 2014-03-24
THAT Worked!!!!

Thanks guys for you help....

Not only it recovered 46GIGs that I lost when reformatting to EXT4, but it recovered stuff from previous reformats from NTFS from the same 750GIG disk. It extracted 317GIGs of data!!! I got a few days of going through data now..............

I just donated to the writer of this application.

Thanks all,

Heeter

---

### Post by varunendra on 2014-03-24
> **Heeter said:**
> I just donated to the writer of this application.

..one of the **BEST** things we could do to thank and appreciate what we get from FOSS !!

I applaud your kind gesture. =d>

Please also mark the thread as **[SOLVED]** now to make it more useful for others. It indicates that the thread contains a possible solution to the problem mentioned in the Thread Title. :)

---

