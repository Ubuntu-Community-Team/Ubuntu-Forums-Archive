---
title: "Number of Partitions on Hard Disk?"
date: 2015-02-01
forum: General Help
---

### Post by sam-c on 2015-02-01
For a Normal HD and Ubuntu and closely related UNIX/Linux
What is the Maximum Number of OS and Partitions Advisable on the HD.
Please Comment
Thanks 
Uncle Sam;)

---

### Post by deadflowr on 2015-02-01
Depends on the size of the hard drive.
You can install Ubuntu on a partition size of 4Gb-6Gb, just about.
So divide that by the size of the hard drive, and there's your answer.
(Adjust the size to accommodate extra stuff you may or may not install)
So if you adjust the size to something like 25gb, divide that by the size of the drive.

Personally I tend to go with a max of 3 or 4 normally.
Too many just ends up confusing yourself.

---

### Post by Bashing-om on 2015-02-01
sam-c' Hello;

^^ deadflowr !

And we need a definition of " For a Normal HD " normality now needs a point of reference. We talking bios (legacy) partitioning, or the new standard EFI (GPT) ?

In bios (MBR) there is a limit of 4 primary partitions that can be addressed. What is done to allow more partitions is to make one of those 'primary' partitions an 'extended' partition as a container to hold additional "logical" partitions.

In the GPT partitioning scheme a separate /boot partition is required to address the other 127 possible partitions. 

no matter how you slice that apple
[INDENT][INDENT][INDENT]size matters
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2015-02-01
Very good source of information on Linux below.  Old Style scsi and sata drives=15, IDE=63 and GPT as quoted above.  The section at the link below under Logical Partitions.

[http://tldp.org/HOWTO/Partition/partition-types.html#logical](http://tldp.org/HOWTO/Partition/partition-types.html#logical)

On one computer with multiple hard drives, the number increases as shown at the link below using Grub Legacy to boot them all.

[http://6697275.blog.163.com/blog/static/3969367520078191839530/](http://6697275.blog.163.com/blog/static/3969367520078191839530/)

---

