---
title: "df-hCommand with Cron"
date: 2016-01-02
forum: General Help
---

### Post by james_l2 on 2016-01-02
I have latest version of xUbuntu installed..

What I am trying to do is have a command **df -h **run every evening at 18:30hrs and email it to me.

Can someone help me with the steps.. and let me know if I am correct..

1. Sudo crontab -e
2. 30 18 * * * df -h | sendmail [EMAIL="me@myemail.com"]me@myemail.com[/EMAIL]
3. Save and exit


I'm learning to I'm wondering if this is correct?
Or do you link path to a .sh file..

I keep trying so I'm hoping someone can talk me through it.

---

### Post by nerdtron on 2016-01-02
Before you even put a command (or a script) on the crontab, you'll need to verify first if the command (or script) is running.
So first, you should run " df -h | sendmail [email]me@myemail.com[/email]" from the command line. Is the command successful? Did you received an email?

---

### Post by james_l2 on 2016-01-06
> **nerdtron said:**
> Before you even put a command (or a script) on the crontab, you'll need to verify first if the command (or script) is running.
So first, you should run " df -h | sendmail [EMAIL="me@myemail.com"]me@myemail.com[/EMAIL]" from the command line. Is the command successful? Did you received an email?


Good call!!

No, It's only 1 admin account on a laptop.. Any other info you can help with, sorry for newbie questions, but good call!

---

### Post by Habitual on 2016-01-07
logwatch?

---

### Post by james_l2 on 2016-01-08
> **Habitual said:**
> logwatch?

Hi,
Need to do it via Cron job.

---

### Post by nerdtron on 2016-01-10
First you need to fix the email problem, adding to cron job, scripting, etc will be easy after that. What have you tried already to make the email work? Are you sending using your own domain name or do you have an email account that will serve as a relay?

---

### Post by james_l2 on 2016-01-12
> **nerdtron said:**
> First you need to fix the email problem, adding to cron job, scripting, etc will be easy after that. What have you tried already to make the email work? Are you sending using your own domain name or do you have an email account that will serve as a relay?

I'll be doing this to sort email.. 
It's then the cron throws me off, the steps. 
[http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp](http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp)

---

### Post by nerdtron on 2016-01-12
So you have completed your email setup? If so, then create a script for it.

Example:
```
#!/bin/bash
echo "This is the body of the email" | mail -s "This the subject of the email" me@myemail.com
echo `df -h` | mail -s "Those are back ticks not single quote" me@myemail.com

```

Now save that file for example in /home/username/mail_script.sh
Make it executable:
```
chmod +x /home/username/mail_script.sh 
```

Now before you put in the crontab, you first test if the script runs:
```
/bin/bash /home/username/mail_script.sh 
```

If the email is successfully sent, then create a crontab entry for it:
```
 crontab -e 
```

Now add an line with the following:
```
 30 18 * * * /bin/bash /home/username/mail_script.sh 
```

Save the crontab.

Note: using gmail as a relay for your email alerts is a bad idea. Google will detect your activity and will block you. I've done it before.

---

### Post by james_l2 on 2016-01-14
> **nerdtron said:**
> So you have completed your email setup? If so, then create a script for it.

Example:
```
#!/bin/bash
echo "This is the body of the email" | mail -s "This the subject of the email" me@myemail.com
echo `df -h` | mail -s "Those are back ticks not single quote" me@myemail.com

```


Note: using gmail as a relay for your email alerts is a bad idea. Google will detect your activity and will block you. I've done it before.


Hi, and thanks for taking the time for such a detailed reply.

Can you explain the first part please, the two echo sentences. This is the body, this is subject, these are back ticks. Is this how the email will be shown as in what the email subject will be 
Sorry for the questions if they are stupid.

---

### Post by ian-weisser on 2016-01-14
> **james_l2 said:**
> Can you explain the first part please, the two echo sentences. This is the body, this is subject, these are back ticks. Is this how the email will be shown as in what the email subject will be 

Play with the 'mail' command and get comfortable with how it works,
It's not difficult. Use 'mail' to send an e-mail to yourself.
Also see 'man mail' for the manual page, which explains a lot about how to use the 'mail' command.

The echo and backticks are simply ways to properly enter a mail command using a script. Clever scripting is a separate skill from using single shell commands.
I think nerdtron's scripting was wonderfully concise and clear, an excellent solution.

You must learn three skills to do what you want: Shell commands, scripting those commands, and cron.
It may perhaps be easier for you to learn each skill separately. That you will better understand, and will be better able to maintain what you create.

---

### Post by nerdtron on 2016-01-14
> **james_l2 said:**
> Hi, and thanks for taking the time for such a detailed reply.

Can you explain the first part please, the two echo sentences. This is the body, this is subject, these are back ticks. Is this how the email will be shown as in what the email subject will be 
Sorry for the questions if they are stupid.

As you have guessed this is correct. These two echo lines are basic construct for the "mail" command. The "mail" command will send emails to your configured SMTP server, which you should have configured separately (from the links you have provided on your earlier reply).

So basically the left part of the command, echo, will be the body, and the right part, mail -w, will be the subject of the email. 
On the second command, you'll see i used backticks ( ` ) instead of double quotes and you'll notice that "df -h" is inside the backticks. This means that the "df -h" will be executed, and it's output will be echoed, effectively making it the "body" of the email.

Try the commands on the command line to test them.

---

