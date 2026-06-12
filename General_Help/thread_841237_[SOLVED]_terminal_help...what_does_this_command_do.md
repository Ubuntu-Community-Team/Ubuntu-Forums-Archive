---
title: "[SOLVED] terminal help...what does this command do?"
date: 2008-06-26
forum: General Help
---

### Post by jmd9qs on 2008-06-26
hey guys, 

can anybody tell me what this does? hal-disable-polling --device /dev/cdrom

i started using powertop and it 'suggested' that i run this command...

---

### Post by brian_p on 2008-06-26
> **jmd9qs said:**
> hey guys, 

can anybody tell me what this does? hal-disable-polling --device /dev/cdrom

i started using powertop and it 'suggested' that i run this command...

```
man hal-disable-polling
```

---

### Post by jmd9qs on 2008-06-26
thanks... i forgot about the man pages... need to get back into that.

---

### Post by jmd9qs on 2008-06-26
however the man command doesn't have an answer for me

---

### Post by brian_p on 2008-06-26
> **jmd9qs said:**
> however the man command doesn't have an answer for me

Then you need to formulate the question more precisely.

---

### Post by jmd9qs on 2008-06-26
im brand new at this...pray tell, how would i formulate the question better? powertop tells me that 'hal' is what 'auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in'. i would like to know what the command is doing, so i don't mess anything up. i figured that knowing what and why is probably good if i want to get better at running my system with the terminal.

---

### Post by Claus7 on 2008-06-26
Hello,

I had no idea with the subject until I saw your post. I read the man pages, and what I made out about this command is that : you can control a daemon which is responsible for the "auto mount" of devices. If a device malfunctions then you are promted to use this command in order to mount it.

Regards!

---

### Post by steveneddy on 2008-06-26
It makes the "hardware abstraction layer" [hal] not waste precious processor time asking the cd/rom drive if it has a disc ready to play every few seconds, thereby reducing the drain on your battery power of your laptop.

---

### Post by jmd9qs on 2008-06-26
thanks claus...please tell me, what did you type to recieve the man page? i tried the full command and it didn't work...

---

### Post by Claus7 on 2008-06-26
Hello,

I typed :

```
man hal-disable-polling
```

and this is the output :

HAL-DISABLE-POLLING(1)                                  HAL-DISABLE-POLLING(1)



NAME
       hal-disable-polling - disable polling on drives with removable media

SYNOPSIS
       hal-disable-polling [options]


DESCRIPTION
       hal-disable-polling  can  be used to to disable and enable media detec&#8208;
       tion on drives with removable storage. For more information about  both
       the  big  picture  and  specific  HAL properties, refer to the HAL spec
       which can be found in /usr/share/doc/hal-doc/spec/hal-spec.html depend&#8208;
       ing on the distribution.


OPTIONS
       The following options are supported:

       --udi  The UDI (Unique Device Identifier) of the device object.

       --device
              The device file of the drive.

       --enable-polling
              Enable polling instead of disabling it.

       --help Print out usage.

       --version
              Print the version.


NOTES
       This program requires super user privileges.


RETURN VALUE
       If  the requested operation was successful, this program will exit with
       exit code 0.


HISTORY
       Polling a storage drive is a necessary evil to  detect  when  the  user
       inserts or removes media. Human computer interaction studies have shown
       that a broad class of users expect their system to react within  a  few
       seconds  of  this.  Thus, the hald daemon polls through the hald-addon-
       storage addon (one instance for each drive with removable media).

       The purpose of the hald-addon-storage addon is simply to open the  spe&#8208;
       cial device file at a regular interval (either every 2 or every 16 sec&#8208;
       onds) to check for new media. This program tries  to  open  the  device
       file using the O_EXCL option which means that programs like cdrecord(1)
       that uses O_EXCL  automatically  prevents  the  hald-addon-storage  for
       interferring  by  continously  opening the device file. In addition, if
       the drive is locked using HAL (see hal-lock(1)) the  addon  also  stops
       polling.

       Unfortunately, polling a storage drive can have adverse side effects if
       the hardware and/or device driver for the hardware  is  malfunctioning.
       Additionally,  the  operating  system  kernel itself may offer multiple
       interfaces for the same device (e.g. /dev/sg0 and  /dev/scd0)  so  even
       O_EXCL  won&#8217;t  work.  Also,  polling a drive may decrease throughput in
       certain (odd and/or broken) configurations; for  example,  if  two  IDE
       drives  shares the same host (master/slave), bus traffic and contention
       caused by polling e.g. the optical drive (slave) can reduce  throughput
       to  the  hard disk (master) and/or interfere with CD burning on another
       optical drive (master). Finally, polling a  drive  incurs  an  overhead
       both  in  the host system (processes get woken up often, preventing the
       CPU to stay in a deep power saving  states)  and  it  may  prevent  the
       actual drive from reaching deep power states as well. As a result, more
       power is consumed and this affects battery life for laptops.

       Despite the existence of support for asynchronous media change  notifi&#8208;
       cation  in  recent MMC (Multi-Media Commands) specifications, virtually
       no optical drives are compliant  with  the  specification.  Fortunately
       newer  SATA  ATAPI  hardware seems to support Asynchronous Notification
       (AN) and at this time of writing (March 2007) work is underway to  make
       both  the Linux operating system kernel and HAL take advantage of this.

       It is the position of the HAL team that polling should  be  avoided  at
       all costs as long as it doesn&#8217;t heavily impact the user experience in a
       negative way. This tool is provided as a stop-gap measure to use  if  a
       system  is rendered useless due to bugs in drivers and/or hardware that
       is provoked by HAL polling the drive. If such a bug is  encountered  it
       should  be  reported  (see the BUGS section below) so it can be fixed -
       historically hald have triggered a number  of  bugs  in  Linux  storage
       drivers  and  related  subsystems  (such  as  USB) that have later been
       fixed.


BUGS
       Please send bug reports to either the distribution or the  HAL  mailing
       list,  see  [http://lists.freedesktop.org/mailman/listinfo/hal](http://lists.freedesktop.org/mailman/listinfo/hal) on how to
       subscribe.


SEE ALSO
       hald(8), lshal(1), hal-lock(1), open(2), [http://www.t10.org/scsi-3.htm](http://www.t10.org/scsi-3.htm),
       [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=halpolling](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=halpolling)


AUTHOR
       Written  by David Zeuthen <david@fubar.dk> with a lot of help from many
       others.




                                                        HAL-DISABLE-POLLING(1)

See also if you become root and then be able to see these man pages.

Hope this helped,

Regards!

---

### Post by brian_p on 2008-06-26
> **jmd9qs said:**
> im brand new at this...pray tell, how would i formulate the question better?

You have so below.

> powertop tells me that 'hal' is what 'auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in'. i would like to know what the command is doing, so i don't mess anything up. i figured that knowing what and why is probably good if i want to get better at running my system with the terminal.

Powertop is set up to save energy. Polling a device uses energy. I assume the suggestion to use hal-disable-polling is intended to improve energy efficiency. The man page says:

> It is the position of the HAL team that polling should  be  avoided  at all costs as long as it doesn't heavily impact the user experience in a negative way.

If disabling polling has an adverse affect on (say) burning a cd or dvd it can easily be reversed. I'd try it and see. There can be no permanent harm done.

---

### Post by brian_p on 2008-06-26
> **jmd9qs said:**
> thanks claus...please tell me, what did you type to recieve the man page? i tried the full command and it didn't work...

You need to have the hal package installed to get the man page.

---

### Post by steveneddy on 2008-06-28
> **Claus7 said:**
> Hello,

I typed :

```
man hal-disable-polling
```

and this is the output :

HAL-DISABLE-POLLING(1)                                  HAL-DISABLE-POLLING(1)



NAME
       hal-disable-polling - disable polling on drives with removable media

SYNOPSIS
       hal-disable-polling [options]


DESCRIPTION
       hal-disable-polling  can  be used to to disable and enable media detec&#8208;
       tion on drives with removable storage. For more information about  both
       the  big  picture  and  specific  HAL properties, refer to the HAL spec
       which can be found in /usr/share/doc/hal-doc/spec/hal-spec.html depend&#8208;
       ing on the distribution.


OPTIONS
       The following options are supported:

       --udi  The UDI (Unique Device Identifier) of the device object.

       --device
              The device file of the drive.

       --enable-polling
              Enable polling instead of disabling it.

       --help Print out usage.

       --version
              Print the version.


NOTES
       This program requires super user privileges.


RETURN VALUE
       If  the requested operation was successful, this program will exit with
       exit code 0.


HISTORY
       Polling a storage drive is a necessary evil to  detect  when  the  user
       inserts or removes media. Human computer interaction studies have shown
       that a broad class of users expect their system to react within  a  few
       seconds  of  this.  Thus, the hald daemon polls through the hald-addon-
       storage addon (one instance for each drive with removable media).

       The purpose of the hald-addon-storage addon is simply to open the  spe&#8208;
       cial device file at a regular interval (either every 2 or every 16 sec&#8208;
       onds) to check for new media. This program tries  to  open  the  device
       file using the O_EXCL option which means that programs like cdrecord(1)
       that uses O_EXCL  automatically  prevents  the  hald-addon-storage  for
       interferring  by  continously  opening the device file. In addition, if
       the drive is locked using HAL (see hal-lock(1)) the  addon  also  stops
       polling.

       Unfortunately, polling a storage drive can have adverse side effects if
       the hardware and/or device driver for the hardware  is  malfunctioning.
       Additionally,  the  operating  system  kernel itself may offer multiple
       interfaces for the same device (e.g. /dev/sg0 and  /dev/scd0)  so  even
       O_EXCL  won’t  work.  Also,  polling a drive may decrease throughput in
       certain (odd and/or broken) configurations; for  example,  if  two  IDE
       drives  shares the same host (master/slave), bus traffic and contention
       caused by polling e.g. the optical drive (slave) can reduce  throughput
       to  the  hard disk (master) and/or interfere with CD burning on another
       optical drive (master). Finally, polling a  drive  incurs  an  overhead
       both  in  the host system (processes get woken up often, preventing the
       CPU to stay in a deep power saving  states)  and  it  may  prevent  the
       actual drive from reaching deep power states as well. As a result, more
       power is consumed and this affects battery life for laptops.

       Despite the existence of support for asynchronous media change  notifi&#8208;
       cation  in  recent MMC (Multi-Media Commands) specifications, virtually
       no optical drives are compliant  with  the  specification.  Fortunately
       newer  SATA  ATAPI  hardware seems to support Asynchronous Notification
       (AN) and at this time of writing (March 2007) work is underway to  make
       both  the Linux operating system kernel and HAL take advantage of this.

       It is the position of the HAL team that polling should  be  avoided  at
       all costs as long as it doesn’t heavily impact the user experience in a
       negative way. This tool is provided as a stop-gap measure to use  if  a
       system  is rendered useless due to bugs in drivers and/or hardware that
       is provoked by HAL polling the drive. If such a bug is  encountered  it
       should  be  reported  (see the BUGS section below) so it can be fixed -
       historically hald have triggered a number  of  bugs  in  Linux  storage
       drivers  and  related  subsystems  (such  as  USB) that have later been
       fixed.


BUGS
       Please send bug reports to either the distribution or the  HAL  mailing
       list,  see  [http://lists.freedesktop.org/mailman/listinfo/hal](http://lists.freedesktop.org/mailman/listinfo/hal) on how to
       subscribe.


SEE ALSO
       hald(8), lshal(1), hal-lock(1), open(2), [http://www.t10.org/scsi-3.htm](http://www.t10.org/scsi-3.htm),
       [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=halpolling](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=halpolling)


AUTHOR
       Written  by David Zeuthen <david@fubar.dk> with a lot of help from many
       others.




                                                        HAL-DISABLE-POLLING(1)

See also if you become root and then be able to see these man pages.

Hope this helped,

Regards!

That basically what I said. It is just a summary of this entire man page, is it not? I just didn't think that the OP was looking for such a technical answer. :D

---

