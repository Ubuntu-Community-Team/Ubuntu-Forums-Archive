---
title: "FTP script making improper emails"
date: 2014-08-24
forum: General Help
---

### Post by Cool_Javelin on 2014-08-24
I have a script triggered by cron every 15 minutes called '*UpdateNFeedPix2Web*,' and that script calls another script that handles an FTP to update a web page.

It works perfectly, however.

I am getting emails from my root every 15 minutes, and the only entries in the email (other then the headers) are responses from when I call the lcd (local change directory) command.

I change the directory 2 times in the FTP script, and I get 2 entrys in the email.

Here is a trimed down version of the script called from cron
```
#!/bin/bash
#create a variable that points to a log file
log=/home/mylogs/UpdateNFeedPix2Web.log

#start the log file
echo "Start " > $log

#change to the proper working directory
echo "changing to working dir" >> $log
cd /home/myWeb/Pages

...

#call the FTP script to do the dirty work
echo "Sending to Web" >> $log
/usr/local/sbin/UpdateMyWeb.ftp_script
```

And here is the first part of the *UpdateMyWeb.ftp_script* FTP script: (the names have been changed to protect the guilty)
```
#!/bin/bash

hostname="myhome.comcast.net"
username="myusernme"
password="mypassword"


ftp -in $hostname <<EOF
quote USER $username
quote PASS $password

binary

cd mywebpage/Images

lcd /blah/blah/Images

delete myimage.jpg
put myimage.jpg

lcd /blah/blah/Pages

...

```

Here is the email:
```
From root@gimli Sat Aug 23 22:25:07 2014
Return-path: <root@gimli>
Envelope-to: root@gimli
Delivery-date: Sat, 23 Aug 2014 22:25:07 -0700
Received: from root by Gimli with local (Exim 4.76)
        (envelope-from <root@gimli>)
        id 1XLQId-0001tw-BT
        for root@gimli; Sat, 23 Aug 2014 22:25:07 -0700
From: root@gimli (Cron Daemon)
To: root@gimli
Subject: Cron <root@Gimli> /usr/local/sbin/UpdateNFeedPix2Web
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1XLQId-0001tw-BT@Gimli>
Date: Sat, 23 Aug 2014 22:25:07 -0700

Local directory now /blah/blah/Images
Local directory now /blah/blah/Pages

```
Any ideas?

thanks, Mark.

---

### Post by bizhat on 2014-08-24
Add

```

 >/dev/null 2>&1

```

To end of your cronjob.

---

### Post by SeijiSensei on 2014-08-24
I don't have an "lcd" command on my machine.  There's no man page for it either. Is it an alias?

You get the email because whatever lcd is returns "lcd /blah/blah/Images" when it is run.  If you ran the script from the command prompt, you'd see that text appear on the screen.  Since cron doesn't have a terminal, it puts all the terminal output into an email and sends it to the default "root@gimli" address.  bizhat's suggestion pipes all the script's output to the /dev/null blackhole instead so there isn't anything for cron to mail.  The "2>&1" item re-routes any error text that might be written to the "syserr" device (2) to the primary "sysout" device (1), the one being fed to /dev/null.

---

### Post by Iowan on 2014-08-24
> **SeijiSensei said:**
> I don't have an "lcd" command on my machine.  There's no man page for it either. Is it an alias?It's an FTP command  for [COLOR="#FF0000"]l[/COLOR]ocal [COLOR="#FF0000"]c[/COLOR]hange [COLOR="#FF0000"]d[/COLOR]irectory

---

### Post by Cool_Javelin on 2014-09-11
Thanks BizHat, that seems to have worked.

Actually, I had that job making a log file anyway, so I redirected the stderr to append to the log file, and left stdout alone.

Great tip, 

Thanks,mark.

---

