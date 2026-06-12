---
title: "RAID Failure  Notification"
date: 2007-07-15
forum: General Help
---

### Post by mtdewulf on 2007-07-15
I have two file servers running Ubuntu Dapper.  One has a RAID-1 array and the other has a RAID-5 array both set up through mdadm. However, both servers are in another room and my only communication with them is through browsing files over the network.  I am worried that a drive in one of the servers may fail and I wouldn't know about it (well, I would know about the RAID-5, but likely not the RAID-1 if it works like it is supposed to).  Is there anyway I can get mdadm or Ubuntu to email me if there is a failure?  Also perhaps I could even get a weekly status email.

Also, as I hinted above, I believe that when a disk in the RAID-1 array fails, it should be transparent to the [network] user.  Is this true? Will normal operation continue for RAID-1 even in the case of drive failure or do you have to rebuild the array first?

Thanks,
Mike

---

### Post by keithweddell on 2007-07-15
If you reconfigure mdadm (sudo dpkg-reconfigure mdadm) you can set it to monitor the arrays and set an email  address for notification of problems.


Keith

---

### Post by JohnnySkidmark on 2007-07-15
I've noticed in */etc/mdadm/mdadm.conf* the following lines:
```
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
```

Looking at *man mdadm.conf* I also see the following configuration directives that may be of interest:
```
       MAILADDR
              The  mailaddr line gives an E-mail address that alerts should be
              sent to when is running in --monitor mode  (and  was  given  the
              --scan  option).   There should only be one MAILADDR line and it
              should have only one address.

       MAILFROM
              The mailfrom line (which can only be abbreviate at leat 5  char&#8208;
              acters)  gives  an  address  to appear in the "From" address for
              alert mails.  This can be useful if you want to explicitly set a
              domain,  as  the  default from address is "root" with no domain.
              All words on this line are catenated with  spaces  to  form  the
              address.

              Note  that  this  value cannot be set via the mdadm commandline.
              It is only settable via the config file.

       PROGRAM
              The program line gives the name of a  program  to  be  run  when
              mdadm --monitor detects potentially interesting events on any of
              the arrays that it is monitoring.  This program  gets  run  with
              two or three arguments, they being the Event, the md device, and
              possibly the related component device.

              There should only be one program line and it should be give only
              one program.
```

I can't tell you much more than that, though.  Email alerts of disk failures is something I've been meaning to get set up, myself.

---

### Post by hebetude on 2008-02-09
how can I reconfigure a package that is maintaining a lot of data.  I'd prefer changing some options and rebooting or whatever.  My setup is LVM ontop of a mdadm based raid-5. 

Anybody know of some decent tips&tricks to LVM/mdadm.  At the moment, I do a details every day to make sure the raid is still functioning.  It is setup with 2 new hard drives and one old, which makes me feel a bit safer that when 1 drive fails the other 2 will outlive the predecessor for a long period of time.

P.S. no ubuntu program should/will be setup to send events to root, there is no root in ubuntu.

---

### Post by mrsteveman1 on 2008-02-09
In raid-1 and raid-5 a single drive should be able to completely fail without causing the filesystems on those arrays to fail, so no one will notice unless you read logs or have the system notify you.

The only raid level where a single disk can ruin the filesystem is raid-0

---

