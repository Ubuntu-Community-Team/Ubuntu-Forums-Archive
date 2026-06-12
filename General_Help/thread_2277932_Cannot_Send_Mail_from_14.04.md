---
title: "Cannot Send Mail from 14.04"
date: 2015-05-12
forum: General Help
---

### Post by jason-aints on 2015-05-12
I searched the forums for my title and I am not finding exactly what I am looking for.  I am not using a program to send mail, such as Thunderbird or whatever.  I simply want to be able to send mail from my Ubuntu 14.04 DESKTOP version for logging.  I use a program called Logwatch (used alot in RHEL or CentOS) to monitor the server itself.  The program sends mail to the root user account on the machine, which I can check and see, and within the program conf file, I can add an external email address, but it never sends.

I'm familiar with the SMTP concept of sending mail, outgoing mail server authentication, etc.  I don't care to run this box as an SMTP server, but I understand that I need some sort of SMTP or MTA program to send mail into the real world.  I tried Postfix but couldn't get that to work, and the Logwatch program wants to use sendmail, so I installed that but I am having the same issue.  I am sure it is a step I am missing.

I also can't figure out how to get the 'mail' cmd from Terminal to work.  I use this command:
```
mail -s "test" | /usr/sbin/mail myemail@domain.com
```
it follows through the subject, CC, body, but when I try to hit either . or CTRL-D, it never sends the email.

Again, I am sure I am missing something, but I have Googled for what I want to do and can't seem to find this.  It seems like a simple setup, but maybe not.
I did find and follow these instructions, but it still isn't working with sendmail.  If I need to go back to Postfix, I can do that, I don't honestly care what I use, I just want some programs such as Logwatch to be able to email me.
[http://stackoverflow.com/questions/10359437/sendmail-how-to-configure-sendmail-on-ubuntu](http://stackoverflow.com/questions/10359437/sendmail-how-to-configure-sendmail-on-ubuntu)

---

### Post by Keith_Helms on 2015-05-13
I have my Xubuntu system running MythTV send me a daily status email with info on programs recorded, disk space used, etc.  I use a program called ssmtp.  That program uses your email provider to send the mail and doesn't require setting up an MTA on your home system.

After installing ssmtp, you have to set up /etc/ssmtp/ssmtp.conf

```
# root is the person who gets all mail for userids < 1000
root=***youremailaccount@yourmailprovider***

# Here is the gmail configuration (or change it to your private smtp server)
mailhub=***mail.messagingengine.com:587***
AuthUser=***youremailaccount@yourmailprovider***
AuthPass=***youremailpassword***
UseTLS=NO
UseSTARTTLS=YES
Hostname=***somebogusnameforyoursystem.com***

```

The items in bold and italics are the ones you'll need to configure.   Mailhub would be your email provider's smtp dns name and port.  I listed the one I use, but for somebody else it might be **something.gmail.com:nnn**.  For hostname you just need something that looks like a domain name - something.com.  Once you have that set up, you format a standard email with a To line, Subject line, blank line, and then the body.  You then send it with 

```
/usr/sbin/ssmtp *youremailaccount@yourmailprovider* < *name_of_file_containing_the_email*
```

My script is run by cron, so I had to specify the full path to the ssmtp command.

---

### Post by HermanAB on 2015-05-13
Look into nullmailer.  I used it in the past on servers.  Works fine.

---

