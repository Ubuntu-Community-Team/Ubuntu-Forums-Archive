---
title: "Fstab troubles"
date: 2007-10-26
forum: General Help
---

### Post by keylime on 2007-10-26
Here's a fun one I'm having and it's driving me nuts involving fstab.

I have a volume that I made a syntax change to in fstab. When the system rebooted X tanked quite hard and I need to go back and add some text back in to the file to hopefully make it behave again.

The file contents currently are:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=0214ea38-64b1-42e9-98e7-15cca9566e5b / ext3 defaults,noatime,data=writeback
# /dev/hda5 -- converted during upgrade to edgy
UUID=4540baaa-a696-4af0-a0e3-60ca99c19683 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

I need to add the "errors=remount-ro 0 1" text back in, but, everytime I get to either the command line or the rescue CD to change the permissions, I get the "read only" file. 

Is there any way to append the file permissions either at the file or folder level, so I can modify this file back to working condition?

Thanks in advance.

---

### Post by taurus on 2007-10-26
Boot with the LiveCD and then open a terminal and run

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by keylime on 2007-10-26
OK, first hurdle jumped - ty very much taurus.

Now, 2nd hurdle. I have changed it back to the original line of text:

UUID= blah blah....... / ext3 defaults,errors=remount -ro 0 1

Now, if I wanted to add noatime, data=writeback to this line, a) is it possible and b), do I just tack on a comma and drive on?

Thanks again.

---

### Post by chrisccoulson on 2007-10-26
Yes, it would look like this:

```
UUID=0214ea38-64b1-42e9-98e7-15cca9566e5b / ext3 defaults,noatime,data=writeback,errors=remount-ro 0 1
```

---

