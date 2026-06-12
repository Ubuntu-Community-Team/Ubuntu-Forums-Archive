---
title: "MDADM - monitor my RAID array?"
date: 2007-08-18
forum: General Help
---

### Post by Jeinhor on 2007-08-18
Hi,

I would like to use madm to monitor my RAID array. It would be perfect if it could send a e-mail to a specific address when an error occured. How can I achieve this? I guess I have to specify a SMTP server somewhere?

Thanks in advance!

---

### Post by fjgaude on 2007-08-18
The man pages for mdadm are fairly clear: use sudo mdadm --monitor to send e-mail on "event".

       "If any devices are listed on the command line, mdadm will only  monitor
       those  devices.  Otherwise  all arrays listed in the configuration file
       will be monitored.  Further, if --scan is  given,  then  any  other  md
       devices that appear in /proc/mdstat will also be monitored."

Also see man mdadm.conf pages.

The e-mail address is located in the mdadm.conf file in /etc/mdadm folder under the label MAILADDR. I believe you can enter whatever e-mail address you like there replacing "root".

Maybe others have other suggestions.

Good raiding,

frank

---

### Post by Jeinhor on 2007-08-18
Ok, thanks for the reply.

I wonder how it works... no need to specify any SMTP server?

EDIT: Maybe anyone can give an example on how to setup mdadm to send e-mail to a particual address and do this even if I reboot the server (i.e. autostart the monitoring).

---

### Post by fjgaude on 2007-08-18
Yes, the monitoring command is automatically run if you tell it to. Do this and answer all the questions to suit your needs:

```
sudo dpkg-reconfigure mdadm
```

Many yes/no questions, then the e-mail address can be changed from "root" to something else. I suppose you wish to have an address that is outside of the server, eh? That might require you having something like sendmail running, not sure.

Others here know what more to do, help!

frank

---

### Post by Jeinhor on 2007-09-07
Thanks for the info.

I would very much like to know how to configure mdadm to send e-mail to an external e-mail address when a disk fails. Otherwhise all monitoring is useless, I still have to logon to the server in order to check the health of the RAID array...

Best would be if I could use a custom e-mail server (that is, not set up sendmail and instead only specify a SMTP-server).

Thanks in advance!

---

### Post by fjgaude on 2007-09-07
Maybe this thread has something for you (mocoloco):

[http://ubuntuforums.org/showthread.php?t=543605&highlight=raid](http://ubuntuforums.org/showthread.php?t=543605&highlight=raid)

This seems to work... I wonder if others have other ways?

frank

---

### Post by kevlaur on 2008-03-20
I feel your pain, here's a very easy way in which I set mine up:

1) I attached a Python script to this post: "smtpmail.py". Save it to your home dir or wherever(NOT on the RAID array you want to monitor though), "chmod 744" it, and edit it to contain your smtp server, username, password, etc...

2) Test the combination of mdadm and the script like so:
**sudo mdadm --monitor --scan --oneshot --test  --program /home/kevin/smtpmail.py**
Make sure you get a test email.

3) As root, in /etc/rc.d/init.d create a file called whatever you want, mine is called 'raid'.  In it I put the following lines:
[B]#Assemble raid array
mdadm --assemble --scan

#Mount raid array
mount /mnt/raid

#Monitor array
mdadm --monitor --scan --daemonise --delay 120 --program /home/kevin/smtpmail.py[/B]

4) Create a symbolic link like so:
**sudo ln -s /etc/rc.d/init.d/raid /etc/rc.d/rc5.d/S01raid**
This makes the raid array come up and be monitored before anything else.
Or, as an alternate(if available), execute the following to update the rc.d run levels automatically: 
**sudo update-rc.d raid defaults**

5) Sit back and enjoy how easy that was!  Pat yourself on the back!!!

     Cheers,
     -Kevin

---

### Post by fjgaude on 2008-03-20
Thanks, man... interesting... likely there are many ways to do this but your way is good!

---

