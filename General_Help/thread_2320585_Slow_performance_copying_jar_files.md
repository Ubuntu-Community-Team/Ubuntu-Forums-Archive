---
title: "Slow performance copying jar files"
date: 2016-04-15
forum: General Help
---

### Post by l1nk2 on 2016-04-15
Hello all,
i'm experiencing a strange performance behaviour when i simply copy a java project from one directory to another. When it starts to copy the local jar files the speed is too slow, it takes about 3-5 seconds for each jar file. If i do the same at my old machine i don't have this problem.

Specs:
Ubuntu 14.04 LTS
Lenovo Workstation P500
256Gb SSD - i'm using only this one
32Gb RAM


Can you help me?

---

### Post by papibe on 2016-04-15
Hi l1nk2. Welcome to the forum ):P

How big are those files?

How are you copying them? Using the GUI, or with a command in the terminal?

Are you trimming your SSD manually, or using the system schedule?

Is that a Samsung EVO SSD? Did you upgrade your [firmware]("http://www.computerworld.com/article/2836082/samsung-delivers-fix-for-ssd-slowdowns.html") so it fixes the bug of slow access for files that you haven't touch in awhile?

Come here often, and have fun.
Regards.

---

### Post by ajgreeny on 2016-04-15
Are the source and destination folders on the same partition?

If not the system has to read from the first partition, then copy the data, and then finally write the data back to the second partition, rather than doing what is basically a rename.

---

### Post by l1nk2 on 2016-04-15
Hi,
the biggest file is ~1Mb...
I'm copying them with the command line: cp -rf from to
I haven't done any upgrade to the firmware... Do you know which version has the bug? How can i verify the firmware version?

---

### Post by l1nk2 on 2016-04-15
I'm on the same partition.
Thank you for your help.

---

### Post by papibe on 2016-04-15
To get your firmware:
```
 sudo hdparm -I /dev/sda | grep -i firmware
```
where '/dev/sda' is the name of the disk you are using (probably the same name if you only have one).

Here's the current Samsung tools for SSDs: [Samsung SSD downloads]("http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html") (The Windows version is a Live ISO).

If you want to check your disk performance, try these two commands, and paste your results:
```
dd if=source_file  of=./copy_file

rsync -vP source_file other_copy_file
```
Regards.

---

### Post by l1nk2 on 2016-04-18
Hello all.
The root cause for this problem was the company antivirus :evil:....
Since i stop the process everything works like a charm.

Thank you all for help.

---

