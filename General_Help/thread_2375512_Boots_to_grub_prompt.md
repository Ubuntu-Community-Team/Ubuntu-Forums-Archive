---
title: "Boots to grub prompt"
date: 2017-10-25
forum: General Help
---

### Post by schnemart on 2017-10-25
Hi all
i upgraded from 14.04 to 16.04 desktop everything ok about a week ago
but today boots to grub prompt
tried booting of a USB stick and then ran
boot-repair
twice
these are the outputs
[http://paste.ubuntu.com/25813664](http://paste.ubuntu.com/25813664)

[http://paste.ubuntu.com/25814463](http://paste.ubuntu.com/25814463)

both times reported problem fixed but boots back to grub prompt
please help
regards martin

---

### Post by ajgreeny on 2017-10-25
Is this the same machine with which you had the problem back in June this year?

---

### Post by schnemart on 2017-10-25
I have had a similar problem but it might of been last year I can't remember  and I fixed

---

### Post by oldfred on 2017-10-25
Boot-Repair says this:
> The primary GPT table is corrupt, but the backup appears OK, so that will be used.

       [URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
 sudo gdisk /dev/sda
Command (? for help):
 launch gdisk, then type v,  then type w to save your changes, if verify does not look correct use q to quit.
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL] v    verify disk
w    write table to disk and exit

---

### Post by schnemart on 2017-10-26
Hi All
Thanks for your help 
This worked and fixed issue
I  feel a bit foolish I realise now that[I]  I had the same problem in june 2015 and asked and got the  answer on this forum

that said is this     showing that my HDD is on the way out and should  I but new HDD
or as this is a HYBRID SSD/normal   something may be wrong with SSD/hybrids

again thank you for your help
[/I]regards
Martin

---

### Post by oldfred on 2017-10-26
What does Smart Data say about drive?
It also can run lots of tests, but all I know is whether drive is good/bad.

Smart Data is in Disks (gnome-disks) and icon in upper right corner.

---

### Post by schnemart on 2017-11-01
Hi Thanks for your help I will  think I will get a new drive this one has been problematic
so I will close this off thanks for your help

---

