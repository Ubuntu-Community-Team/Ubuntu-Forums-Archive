---
title: "Cron Job Issue"
date: 2014-10-18
forum: General Help
---

### Post by ssott on 2014-10-18
(Ubuntu 14.04.01 + Webmin 1.710)

Hi Folks,
  I have the following script which i call burp-report which takes the result from a backup program, adds it to the file burp.txt then echos that to the body of an email message which gets sent to my email address (see below).

Now when i run this script from the command prompt it works exactly as i want, i then used webmin to setup a cron job to trigger it once a week on a Saturday morning (output from crontab below). 

30 10 * * 6 /home/me/burp-report     #Burp Weekly Report

When i "Save And Run", like the command line, it works perfectly, however when i leave it to trigger automatically it sends me the e-mail, correctly sets the subject as the current date / time but the message body remains empty. I discovered this is due to there being nothing in the burp.txt file at the end of the script triggered by cron.

What i cant understand is why, what is the difference between it being triggered automatically and being manually ran via the command prompt or via webmin scheduled cron jobs?

 #!/bin/bash
clear
rm burp.txt
burp -c /etc/burp/burp-server.conf -a S -C Laptop1 >> burp.txt
burp -c /etc/burp/burp-server.conf -a S -C PC-1 >> burp.txt
#echo "Weekly burp report : $(date)" | mutt -a burp.txt -s "Burp Report $(date)$
echo "$(cat burp.txt)" | mutt -s "Burp Report $(date)" -- [email]x@y.com[/email]

---

### Post by ian-weisser on 2014-10-18
Cron is designed to run headless. So 'clear' and 'mutt' and other display-related commands may not work as expected or crash the script.
Usually, you redirect output to a logfile.

Cron does not use your environment variables (DISPLAY, PATH, etc.) or bashrc. It's recommended to use full paths and avoid personal aliases. 

Generally, when troubleshooting cron scripts: Start clean, with a simple test for success ('touch /tmp/successfile'), and add each line one-by-one until you get to the failure.

---

### Post by ssott on 2014-10-18
> **ian-weisser said:**
> Cron is designed to run headless. So 'clear' and 'mutt' and other display-related commands may not work as expected or crash the script.
Usually, you redirect output to a logfile.

Cron does not use your environment variables (DISPLAY, PATH, etc.) or bashrc. It's recommended to use full paths and avoid personal aliases. 

Generally, when troubleshooting cron scripts: Start clean, with a simple test for success ('touch /tmp/successfile'), and add each line one-by-one until you get to the failure.

Hi,
  Thanks for the feedback, but i'm still a bit confused. The script works perfectly if ran from command line or when ran from Webmin's cron tab scheduler, just not when triggered by cron. 

mutt is an email program by the way and not a display related command.

I've done some more digging and changed / simplified things a bit for testing, and it seems to create the burp.txt file but it has no content, so it mails a blank file. 

If i change the script to simply:-

#!/bin/bash
rm home/me/burp.txt
burp -c /etc/burp/burp-server.conf -a S -C Laptop1 >> /home/me/burp.txt

The burp.txt file is created but with no content.  If i run the command 

burp -c /etc/burp/burp-server.conf -a S -C Laptop1

On its own, i get output from the command as expected, like so,

 burp status                                                2014-10-18 15:03:16

   Client: Laptop1
   Status: idle
   Backup list: 0000054 2014-10-18 09:55:11 (deletable)
                0000053 2014-10-16 17:53:47 (deletable)
                0000052 2014-10-15 18:15:00 (deletable)
                0000051 2014-10-14 19:21:31 (deletable)
                0000049 2014-10-12 13:55:06 (deletable)
                0000045 2014-10-08 18:20:59 (deletable)
                0000041 2014-10-02 19:24:27 (deletable)
                0000037 2014-09-27 14:35:06 (deletable)
                0000033 2014-09-23 18:15:03 (deletable)
                0000029 2014-09-12 17:55:07 (deletable)

So it seems to be the redirection of the command output to the file which is the issue.

I also tested 

#!/bin/bash
rm home/me/burp.txt
echo Test >> home/me/burp.txt

and

#!/bin/bash
rm home/me/burp.txt
echo date >> home/me/burp.txt

And i do get a burp.txt file with the word Test in it or a text file with the current date/time in it as you would expect.

I can only assume the "burp -c /etc/burp/burp-server.conf -a S -C Laptop1" isn't running when triggered from cron or theres an issue with the redirection.

Any ideas?

---

### Post by ian-weisser on 2014-10-18
Could the burp output be on stderr instead of stdout?
>> redirects stdout.

---

### Post by ssott on 2014-10-18
> **ian-weisser said:**
> Could the burp output be on stderr instead of stdout?
>> redirects stdout.

Hmm, if so then why does

sudo burp -c /etc/burp/burp-server.conf -a S -C Laptop1 >> /home/me/burp.txt 

Work perfectly from the command prompt? :?

If it used stderr instead of stdout would the above not work?

Just a thought, these files are in my home dir, but im running the cron job as root.  I don't suppose that would make a difference would it as i explicitly define the path to the files i need in the script.

---

### Post by ian-weisser on 2014-10-18
> **ssott said:**
> Just a thought, these files are in my home dir, but im running the cron job as root.

Permissions can make a big difference.
Try running it from your terminal as root.
Or try your user crontab instead of root crontab.

---

### Post by nerdtron on 2014-10-18
```
30 10 * * 6 /home/me/burp-report     #Burp Weekly Report 
```

Cron jobs run on a different shell. Possible cause of error too. Try specifying the shell on the cronjob.

Change to:
```
  30 10 * * 6 /bin/bash /home/me/burp-report     #Burp Weekly Report 
```

Also cron runs on a different  directory so this line will not work:
```
 echo "$(cat burp.txt)" | mutt -s "Burp Report $(date)" -- [EMAIL="x@y.com"]x@y.com[/EMAIL] 
```

Since you are already specifying absolute paths, you should also put the complete path on the echo cat command. Or just like:
```
 cat /home/me/burp.txt | mutt -s "Burp Report `date`" -- x@y.com 
```

---

### Post by ssott on 2014-10-18
> **nerdtron said:**
> ```
30 10 * * 6 /home/me/burp-report     #Burp Weekly Report 
```

Cron jobs run on a different shell. Possible cause of error too. Try specifying the shell on the cronjob.

Change to:
```
  30 10 * * 6 /bin/bash /home/me/burp-report     #Burp Weekly Report 
```

Also cron runs on a different  directory so this line will not work:
```
 echo "$(cat burp.txt)" | mutt -s "Burp Report $(date)" -- [EMAIL="x@y.com"]x@y.com[/EMAIL] 
```

Since you are already specifying absolute paths, you should also put the complete path on the echo cat command. Or just like:
```
 cat /home/me/burp.txt | mutt -s "Burp Report `date`" -- x@y.com 
```

Hi,
  Thanks for the feedback - I have finally manged to sort this and its now working as i want, the issue was that i had to give the full path to the burp command within the script.

#!/bin/bash
rm /home/me/burp.txt
**/burp/src/burp** -c /etc/burp/burp-server.conf -a S -C Laptop1 >> /home/me/burp.txt
**/burp/src/burp** -c /etc/burp/burp-server.conf -a S -C PC-1 >> /home/me/burp.txt
echo "$(cat /home/me/burp.txt)" | mutt -s "Burp Report $(date)" -- [EMAIL="x@y.com"]x@y.com[/EMAIL]

It was suggested previously by ian-weisser that Cron does not use your environment variables (DISPLAY, PATH, etc.) or bashrc. Although, as im quite new to Ubuntu / Unix etc i don't think i appreciated exactly what that meant so i went about adding full paths to all the files but not the command itself.

Now i have that it within the script it works perfectly, strange i don't need the same for echo and mutt though.

Incidentally, none of the other changes you suggested were needed once that had been done including /bin/bash in crontab, but thanks for the suggestion.

Many thanks all for the support.

---

### Post by ian-weisser on 2014-10-18
> **ssott said:**
> so i went about adding full paths

Congratulations!
It's a wonderful feeling when you finally get a sticky cron job to work.
Happily, once working, I have found cron to be rock solid.

And with a bit of experience like this, it's dead easy to write the jobs.

---

