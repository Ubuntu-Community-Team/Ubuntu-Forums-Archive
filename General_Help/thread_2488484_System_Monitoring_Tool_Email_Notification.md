---
title: "System Monitoring Tool Email Notification"
date: 2023-07-06
forum: General Help
---

### Post by wyattwhiteeagle on 2023-07-06
Would email delivery still be successful if sent to a local email client such as Thunderbird or Trojita?

I use Monitorix, a system monitoring tool.

I want to receive a daily email notification alerting me of any problems or telling me everything is ok.

I want to receive email notifications even when not connected to Wifi or internet alerting me of problems or telling me everything is ok.

---

### Post by MAFoElffen on 2023-07-06
> **wyattwhiteeagle said:**
> Would email delivery still be successful if sent to a local email client such as Thunderbird or Trojita?

I use Monitorix, a system monitoring tool.

I want to receive a daily email notification alerting me of any problems or telling me everything is ok.

[COLOR=#ff0000]I want to receive email notifications even when not connected to Wifi or internet alerting me of problems or telling me everything is ok[/COLOR].
Any email notifications, whether from a self-hosted mail server or using a smtp service to send to an external mail server, either would have to be connected to the internet via some route. It can not go via magic to notify you (without some kind of connection). That just isn't possible in this realm, so I might be a bit confused how you see that working. LOL

In my maintenance scripts I include emails to my admin email that give status. They are kicked off by crontab... 

Not familiar with Monitonix. Looks handy. Here is the link to their doc's man page where they discuss emailed reports: [https://www.monitorix.org/manpage.html#67](https://www.monitorix.org/manpage.html#67)

---

### Post by wyattwhiteeagle on 2023-07-06
> **MAFoElffen said:**
> Any email notifications, whether from a self-hosted mail server or using a smtp service to send to an external mail server, either would have to be connected to the internet via some route. It can not go via magic to notify you (without some kind of connection). That just isn't possible in this realm, so I might be a bit confused how you see that working. LOL


In my maintenance scripts I include emails to my admin email that give status. They are kicked off by crontab...


Not familiar with Monitonix. Looks handy. Here is the link to their doc's man page where they discuss emailed reports: [https://www.monitorix.org/manpage.html#67](https://www.monitorix.org/manpage.html#67)


I didn't know if that would work or not.
I thought maybe it might work since Thunderbird or Trojita need to be installed.


You mention maintenance script.
Would it be better if I incorporated something like that to have a text file exported to a Desktop directory and cleaned weekly or when I correct an issue?

---

### Post by MAFoElffen on 2023-07-06
Me being a System Admin , I had my scripts alert me in real time via emails, and SMS messages.

If you are talking about weekly instead of real time, then that system would be fine with it's alerts. ldap is going to batch send it's alerts when it regains it's internet connection, right?

---

### Post by wyattwhiteeagle on 2023-07-06
> **MAFoElffen said:**
> Me being a System Admin , I had my scripts alert me in real time via emails, and SMS messages.

If you are talking about weekly instead of real time, then that system would be fine with it's alerts. ldap is going to batch send it's alerts when it regains it's internet connection, right?
I'm not yet receiving any notifications as I don't have that configured.
I wanted to get experienced insight so that I can make a somewhat educated decision about which is best for what I'm wanting to do.

---

### Post by MAFoElffen on 2023-07-06
In my experience, for audits, reports and general job status's, those saved to my admin directory, wherever was fine. I had one directory for shared access for the admin group. In that directory was folders for the admin journals, reports, etc.

If something was over a certain threshold, and I wanted it to be pointed out to me, then I sent myself an email to the admin email account. That was the first thing I checked in the morning, and every so often during the day. My smartphone would notify me of mail alerts to that account...

If something was a failure or an emergency, I had myself texted, so I knew right away. Server failures. Disk went south. Power failure. Corrupted data. Space issue. Things like that, I wanted to know right away. 

I used textbelt.com. About 10 years ago, they had 75 texts a day free. Nowadays, they are not as generous... Only one text a day without a paid subscription. You can use curl to send the message to them, which then gets forwarded as a SMS text... They have been around for a while. I guess now there are probably a lots of other alternatives.

---

### Post by wyattwhiteeagle on 2023-07-06
> **MAFoElffen said:**
> In my experience, for audits, reports and general job status's, those saved to my admin directory, wherever was fine. I had one directory for shared access for the admin group. In that directory was folders for the admin journals, reports, etc.

If something was over a certain threshold, and I wanted it to be pointed out to me, then I sent myself an email to the admin email account. That was the first thing I checked in the morning, and every so often during the day. My smartphone would notify me of mail alerts to that account...

If something was a failure or an emergency, I had myself texted, so I knew right away. Server failures. Disk went south. Power failure. Corrupted data. Space issue. Things like that, I wanted to know right away. 

I used textbelt.com. About 10 years ago, they had 75 texts a day free. Nowadays, they are not as generous... Only one text a day without a paid subscription. You can use curl to send the message to them, which then gets forwarded as a SMS text... They have been around for a while. I guess now there are probably a lots of other alternatives.

What does a maintenance script like that look like and how would I make sure it runs automatically from cron and survives a reboot?

---

### Post by MAFoElffen on 2023-07-08
Really? You don't run script from crontab?
```

*/1 * * * * cd /home/mafoelffen/Scripts && /bin/bash job001.sh

```

Sample code for script job001.sh
```

#!/bin/bash
## MAFoElffen, <mafoelffen@ubuntu.com, 2023.07.07
## Example script to check boot space
#     Checks space left in /boot partition
#     If over 80% used, email me
#     If over 90% used, text me
#  Kicked off by crontab
#  Uses 'mail' command from Ubuntu package 'mailutils'

################
## Variables
################
USED=$(lsblk -o name,mountpoint,fsuse% | grep '/boot' | sed 's/%//g' | awk '{print $3}')
MOUNT_TEST=$(/usr/bin/mount | grep '\ on /boot\ ')
ADDRESS"mafoelffen@ubuntu.com"
SUBJECT=""
REPORT="/home/mafoelffen/Admin/report.txt"
PHONE="7801234567"
MESSAGE=""
exit_code=0

################
## Functions
################

function MailMe() {
    /usr/bin/mail -a $REPORT -s "$SUBJECT"  $ADDRESS < /dev/null
}

function TextMe() {
    curl -X POST https://textbelt.com/text \
       --data-urlencode phone=$PHONE \
       --data-urlencode message=$MESSAGE \
       -d key=textbelt     
}

function MountTest() {
    if [ -z $MOUNT_TEST  ]
    then 
        exit_code=1
        MESSAGE="Boot partition not mounted on Server01"
        TextMe
        exit_code=1
    fi
}

function CheckAvailable() {
    if [ $exit_code -eq 0 ]
    then
        if [ $USED -ge 90 ]
        then
            MESSAGE="Out of space on boot partition of Boot on Server01!"
            TextMe
        elif [ $USED -ge 80  ]
        then
            SUBJECT="Running low on space. Boot Server01"
            MailMe
        else
            SUBJECT="Job Completed Successfully."
            MailMe
        fi
    else
        SUBJECT="Something went wrong during job#001"
        MailMe
        exit_code=1
    fi
}


################
## Main
################
MountTest
CheckAvailable
exit $exit_code

```
I do the same kind of thing on Windows Servers maintenance scripts in PowerShell.

---

### Post by TheFu on 2023-07-08
There is 2 types of email.
[LIST=1]
[*]MTA-to-MTA (sendmail, postfix, exim)
[*]Client-to-MTA (thunderbird, Evolution, etc)
[/LIST]

Most Unix utilities want to use the sendmail interface into the local MTA to send email anywhere.  There's no way to have Thunderbird send anything.  SMTP server -to- SMTP server email is unauthenticated and usually goes over port 25/tcp.

Almost all CLI-based tools will look for the sendmail interface running locally on the same system.  This local MTA can be configured to only work alone, never sending email anywhere else or it can be setup to send email externally. Typically, ISPs will block external email unless you sign up to have external MTA-to-MTA (port 25/tcp) emails allowed.  ISPs won't allow this for residential accounts.  What they may do is have an email relay server that their customers can use - which is an MTA-to-MTA connection over port 25/tcp.  This way, they will be able to monitor email coming from a specific client account and can quickly shutdown spammers.

Authenticated SMTP connections can be used with ports 465/tcp and 587/tcp, however, most MTAs don't support sending emails that way if the sendmail interface was used.  Only fat clients can do that.

BTW, always remember that sending email uses SMTP.  Receiving email by a client is either IMAP or POP.  Receiving email via SMTP is a server-to-server (mta-to-mta) connection.

So the first question is, where do you want the emails to be sent by the monitoring system?  If just local, then you'll use a CLI-based email reader that knows about the mbox format (NOT Thunderbird) and only reads local mail from /var/spool/mail/ as the inbox.  If you want these monitoring emails to be sent off the system, then you'll need to configure an MTA (postfix, sendmail, exim) to transfer the mail to another server over port 25/tcp.  It is a really bad idea to send system logs or monitoring alerts outside your network. Remember, email is like a postcard, so anyone can read it along the way to the final destination.  Sending sensitive information outside isn't a good idea.

---

### Post by wyattwhiteeagle on 2023-07-09
Thanks a bunch

How would I create a script for crontab?
How would I make sure it runs automatically and survives a reboot?
Is there anything I need to add, change, or comment out with the autofs, fstab, and/or .conf files?
Which parts go into the crontab and which parts go into the personal custom scripts directory?
Where is the best location for that directory to be included in the backup?

I'm wanting to improve my computing practices by getting into the habit of efficiently using crontab, autofs or fstab, and working with .conf and .cfg files.

I'm not sure where to start.
I know I want to start with experienced insight and good, efficient "step-by-step How-To" tutorials.

I have a bash script to export a text file to the Desktop, but that script is configured to be ran manually from the Desktop.
Scripts like that work, but I need to improve not only the system but also my ways of doing things.

---

### Post by TheFu on 2023-07-09
> **wyattwhiteeagle said:**
> 
How would I create a script for crontab?

I don't want to be sucked into one of your 60 post threads..  You create a crontab script just like you create any other script, just don't using any GUI programs inside it and don't assume any specific environment variable already has been set, unless your script specifically set it.  Cron jobs need to run even if no user is logged in.

> **wyattwhiteeagle said:**
> 
How would I make sure it runs automatically and survives a reboot?


That's what cron does.

> **wyattwhiteeagle said:**
> 
Is there anything I need to add, change, or comment out with the autofs, fstab, and/or .conf files?

That would depend on how you solve things. I don't know.  You do things really weird, I've noticed.  Sometimes I see typos in stuff you post and are very wrong.

> **wyattwhiteeagle said:**
> 
Which parts go into the crontab and which parts go into the personal custom scripts directory?

That's a personal choice.  I like having 1 script called from the crontab for each task. If other scripts are needed, then the one called by cron will need to call the others.

> **wyattwhiteeagle said:**
> 
Where is the best location for that directory to be included in the backup?

It depends.  I put root-only scripts in ~root/bin/.  Sometimes there are sensitive things in scripts that no other users should see.  I put scripts only for my userid in ~/bin/.  I put scripts that other users might like to use in /usr/local/bin/.  

> **wyattwhiteeagle said:**
> 
I'm wanting to improve my computing practices by getting into the habit of efficiently using crontab, autofs or fstab, and working with .conf and .cfg files.

Practice.  Make mistakes. Learn from those mistakes.  Get a job using these skills in a team environment, get a mentor assigned and LISTEN.

> **wyattwhiteeagle said:**
> 
I'm not sure where to start.
I know I want to start with experienced insight and good, efficient "step-by-step How-To" tutorials.

That's not possible.  For 50 yrs, people have learned Unix buy getting training and writing scripts, reading books, discussing problems with peers.  A 30 second discussion can replace 50 posts in these threads.  _UNIX Power Tools_ and similar books are full of script examples along with "Why" they do things. Even a 20 yr old copy of that book for $0.50 would be useful.  Hit a used book store with $3 and you'll have more example scripting books/cookbooks than you'll get through.  Don't just read the books.  Type in the examples (don't copy/paste) and test each for working, make small changes to the script to accomplish a little more and a little less.  Then move onto the next example.  Whatever you do, don't pay more than $5 for these books.  People will sell them for $40, if you'd feel better paying that amount, but it isn't needed.

> **wyattwhiteeagle said:**
> 
I have a bash script to export a text file to the Desktop, but that script is configured to be ran manually from the Desktop.
Scripts like that work, but I need to improve not only the system but also my ways of doing things.

Yep.

I will not be following this thread. Good luck.

---

### Post by wyattwhiteeagle on 2023-07-09
> **TheFu said:**
> I don't want to be sucked into one of your 60 post threads


...


Yep.


I will not be following this thread. Good luck.
TheFu is awesome.
Though he was a little harsh, he didn't leave me empty-handed.

---

### Post by wyattwhiteeagle on 2023-07-09
I believe it's important for myself to quote TheFu's post...
> **TheFu said:**
> 
[QUOTE=wyattwhiteeagle;14149840]How would I create a script for crontab?
I don't want to be sucked into one of your 60 post threads.. You create a crontab script just like you create any other script, just don't using any GUI programs inside it and don't assume any specific environment variable already has been set, unless your script specifically set it. Cron jobs need to run even if no user is logged in.


> **wyattwhiteeagle said:**
> How would I make sure it runs automatically and survives a reboot?
That's what cron does.


> **wyattwhiteeagle said:**
> Is there anything I need to add, change, or comment out with the autofs, fstab, and/or .conf files?
That would depend on how you solve things. I don't know. You do things really weird, I've noticed. Sometimes I see typos in stuff you post and are very wrong.


> **wyattwhiteeagle said:**
> Which parts go into the crontab and which parts go into the personal custom scripts directory?
That's a personal choice. I like having 1 script called from the crontab for each task. If other scripts are needed, then the one called by cron will need to call the others.


> **wyattwhiteeagle said:**
> Where is the best location for that directory to be included in the backup?
It depends. I put root-only scripts in ~root/bin/. Sometimes there are sensitive things in scripts that no other users should see. I put scripts only for my userid in ~/bin/. I put scripts that other users might like to use in /usr/local/bin/.


> **wyattwhiteeagle said:**
> I'm wanting to improve my computing practices by getting into the habit of efficiently using crontab, autofs or fstab, and working with .conf and .cfg files.
Practice. Make mistakes. Learn from those mistakes. Get a job using these skills in a team environment, get a mentor assigned and LISTEN.


> **wyattwhiteeagle said:**
> I'm not sure where to start.
I know I want to start with experienced insight and good, efficient "step-by-step How-To" tutorials.
That's not possible. For 50 yrs, people have learned Unix buy getting training and writing scripts, reading books, discussing problems with peers. A 30 second discussion can replace 50 posts in these threads. UNIX Power Tools and similar books are full of script examples along with "Why" they do things. Even a 20 yr old copy of that book for $0.50 would be useful. Hit a used book store with $3 and you'll have more example scripting books/cookbooks than you'll get through. Don't just read the books. Type in the examples (don't copy/paste) and test each for working, make small changes to the script to accomplish a little more and a little less. Then move onto the next example. Whatever you do, don't pay more than $5 for these books. People will sell them for $40, if you'd feel better paying that amount, but it isn't needed.


> **wyattwhiteeagle said:**
> I have a bash script to export a text file to the Desktop, but that script is configured to be ran manually from the Desktop.
Scripts like that work, but I need to improve not only the system but also my ways of doing things.
Yep.


I will not be following this thread. Good luck.[/QUOTE]

---

