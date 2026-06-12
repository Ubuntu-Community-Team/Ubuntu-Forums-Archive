---
title: "mdadm raid 5 -- suddenly raid array is &quot;recovering&quot; itself"
date: 2007-10-07
forum: General Help
---

### Post by kroenecker on 2007-10-07
My raid 5 array suddently began to rebuild itself.  Right now md0_resync is consuming a large amount of cpu.  This doesn't bother me, but I am worried about why this has happened.  Perhaps one of my disks is going bad?  Is there any other reason for this to suddenly start?  

Most importantly, what system log should I look in in order to determine if a disk is beginning to fail?

Thanks for your time.

---

### Post by dcstar on 2007-10-07
> **kroenecker said:**
> My raid 5 array suddently began to rebuild itself.  Right now md0_resync is consuming a large amount of cpu.  This doesn't bother me, but I am worried about why this has happened.  Perhaps one of my disks is going bad?  Is there any other reason for this to suddenly start?  

Most importantly, what system log should I look in in order to determine if a disk is beginning to fail?

Thanks for your time.

Check syslog and messages, and if there is a specific RAID log then check that.

You may want to install the **smartmontools** package.

---

### Post by kroenecker on 2007-10-07
dcstar,

Thanks for the reply.

Since posting I've looked into smartmontools and have done the following in order to prepare myself for disk failure:

**Smartmontools with Postfix and Gmail**

1) sudo apt-get install smartmontools

By default smartmontools doesn't really do anything (I don't think).  In order to enable smartd, open /etc/default/smartmontools and uncomment start_smartd = yes.

Open up /etc/smartd.conf and add lines that specify your devices:

/dev/sda -d sat -S on -o on -a -I 194 -m <my-external-mail>@gmail.com
/dev/sdb -d sat -S on -o on -a -I 194 -m <my-external-mail>@gmail.com
/dev/sdc -d sat -S on -o on -a -I 194 -m <my-external-mail>@gmail.com

Some of the details of these commands can be found here:
[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

For the -m parameter you can use "root" ie -m root.  This will then send the mail to your local root user (unless you tell your mail transfer agent to redirect this mail to another address).

2) sudo apt-get install mailx.  This allows you to read mail on your local system.  Simply type "mailx" to see if the current user has mail.  I don't actually use this, but installed it anyway.

3) sudo apt-get install postfix.  I'm not a MTA security expert by any means so I really don't know what the potential is for becoming a spam forwarder.  My machines are well firewalled so I don't think this is an issue.

Postfix configuration:

Note that if you ever want to reconfigure postfix you can run sudo dpkg-reconfigure postfix.

Setting up postfix for use with gmail was quite painless when I read the following blog:
[http://www.edafe.org/ubuntu/index.html](http://www.edafe.org/ubuntu/index.html)  "Redirecting Mail for the Local Root User"

> 
Redirecting Mail for the Local Root User

Postfix is Ubuntu&#8217;s default mail transfer agent (MTA) and can be configured to deliver mail using a relay host that requires SMTP authentication.

Get the necessary packages with the following command:
user@ubuntu:~$ sudo apt-get install postfix mailx

Begin to configure your Postfix installation by choosing satellite system as the general type of configuration. Enter the local machine name, eg. mycomputer.edafe.org, as the mail name and the SMTP server address of your email service provider, eg. smtp.relayhost.com, as the SMTP relay host.

Edit the file /etc/postfix/main.cf and add the following:
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
relay_domains =

Create the file /etc/postfix/sasl_passwd , again substituting smtp.relayhost.com with the address of the SMTP relay host and user:password with your respective login details:
smtp.relayhost.com user:password

Continue by executing the following three commands:
user@ubuntu:~$ sudo chown root.root /etc/postfix/sasl_passwd
user@ubuntu:~$ sudo chmod 600 /etc/postfix/sasl_passwd
user@ubuntu:~$ sudo postmap hash:/etc/postfix/sasl_passwd

Instruct Postfix to reload its settings with the following command:
user@ubuntu:~$ sudo /etc/init.d/postfix reload
Making Changes to the Alias Table

The aliases table provides a system-wide mechanism to redirect mail for local recipients.

Edit the file /etc/aliases to contain the following entries, substituting [email]user@yourdomain.com[/email] with the email address that you would like to redirect mail to:
postmaster: root
root: [email]user@yourdomain.com[/email]

Finally, update /etc/aliases.db using the following command:
user@ubuntu:~$ sudo newaliases

Mail for the local root user from now on will automatically be forwarded to [email]user@yourdomain.com[/email] , using smtp.relayhost.com as the relay host.
[www.postfix.org](www.postfix.org), help.ubuntu.com


Regarding aliases, I used my gmail address of course.  Be sure to carefully enter the values into main.cf.  Initially I typed sasl_password as opposed to sasl_passwd so it didn't work :P

Note that since you are using aliases, you can use -m root or -m <youradd>@gmail.com when sending a message via smartd.

Finally to test smartd, add -M test and restart smartd /etc/init.d/smartmontools restart.  This should immediately send an email out to the specified user/address.

If this doesn't work check /var/log/email.log to see what errors might have occurred.  If it does work, remove -M test and restart smartmontools.  

That's it.

---

### Post by sabaka33 on 2008-04-06
So did you figure out why this was happening? I got one of those 4-in-3 SATA bays and I can see when the array is accessed - there is a light for each drive on the front of the case.  I have cought it doing this maybe 5 or 6 times after I set it up, ran *mdadm --detail* to confirm what was happening.  It's been almost a year since I set up the array and I just saw it *recovering* again.  I will check out smartmontools tomorrow and also look into system logs/messages (once I find out how to :???: )

```
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Apr 30 22:12:28 2007
     Raid Level : raid5
     Array Size : ...
  Used Dev Size : ...
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Apr  6 01:59:32 2008
          State : clean,[COLOR="Red"] recovering[/COLOR]
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 48% complete

           UUID: ...
         Events : 0.44

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd

```

---

### Post by fjgaude on 2008-04-06
These random re-syncs are likely the result of disks that have random errors, maybe ones that have serious ones starting to happen.

I've run a raid5 with the same disks for about six months without any re-syncs. I do a speed test on them about once a day to make sure all is okay.

Drives built in the last three or so years should be very reliable, and that has been my experience. In the "old" days, you could experience a hard drive to fail every two years and have to be replaced, but not these days.

---

