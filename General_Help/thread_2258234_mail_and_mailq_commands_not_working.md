---
title: "mail and mailq commands not working"
date: 2014-12-25
forum: General Help
---

### Post by chopra on 2014-12-25
Hi guys,

I'm trying to experiment with simple email programs from the comand line.  I've tried:

mail  [email]my_email_address@domain_name.com[/email]

I'm prompted for a Cc:, and then a subject.  After entering the subject, the curser is just at the left of the screen, and I type a message.  The only way to exit the application is to press enter, and then control D.  I get an exit code of zero (success) but the mail isn't arriving to my inbox of either emails, the primary, or the one I cc'd.

Not sure what I'm doing wrong.

Thanks, Chopra

---

### Post by chopra on 2014-12-30
Okay, I haven't gotten any responses yet, but let me add some details of what I've done since to maybe clarify the issue.

I tried, after reading an old thread here, (which now I can't locate: I was looking at a lot of threads) the command;
sudo  dpkg-reconfigure postfix

I was guided through a step-by-step process, and here's the output:

```


[sudo] password for chopra: 
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
setting synchronous mail queue updates: false
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: chopra-HP-Notebook-PC, HP-Notebook, localhost.localdomain, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 51200000
setting recipient_delimiter: ^
setting inet_interfaces: all
setting inet_protocols: all
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with the changes above.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 


```

I'm not sure if this is even the right thing to be doing for the mail program.  I'm not sure about a few things.  First, the man 5 aliases page told me to enter the following into the /etc/aliases file:
name: value

name is a local address (how do I find this?), and value is one of a number of options, including /file/name, and :include:/file/name.

I don't know what /file/name is.  The absolute path to a file named "name" in a directory named "file", right below the root directory?

The directions in the step-by-step process are confusing as well:



 Mail for the 'postmaster', 'root', and other system accounts needs to be  &#9474;  
 &#9474; redirected to the user account of the actual system administrator.        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If this value is left empty, such mail will be saved in                   &#9474;  
 &#9474; /var/mail/nobody, which is not recommended.                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Mail is not delivered to external delivery agents as root.                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you already have a /etc/aliases file and it does not have an entry     &#9474;  
 &#9474; for root, then you should add this entry.  Leave this blank to not add    &#9474;  
 &#9474; one.    


Then it gives me an option that says: "Root and Postmaster Mail Recipient"

Is this just my username?

As I said, I'm not even sure if this is the right path to be taking.

Thanks, Chopra

---

### Post by schragge on 2014-12-30
If all you want is to get mail off the system say to your gmail account then Postfix seems like an overkill. Try [SendEmail](http://manpages.ubuntu.com/manpages/trusty/en/man1/sendemail.1.html) instead. [Here](http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html) is a howto. Other common options are [ssmtp](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html), [nullmailer](http://www.troubleshooters.com/linux/nullmailer/), [dma](https://wiki.mageia.org/en/Dma_Dragonfly_Mail_Agent), [esmtp](http://esmtp.sourceforge.net/manual.html), [msmtp](https://code.google.com/p/google-gadgets-for-linux/wiki/MSMPTQuickStart). Sure, you can configure a full-blown MTA like Postfix, Exim4 or sendmail as a relay-only one, but it usually isn't worth the trouble for typical home desktop computer. Or are you trying to install a multi-user mail server?

---

### Post by chopra on 2014-12-30
Hi, thanks for the reply.  I am not trying to install a multi-user mail server, as I am not sure what that is.  Does that just mean more than one user can send email?
I am the only user of my machine.  The how to page you sent me, there's an option for Debian Lenny and Debian Etch.  I'm not sure which one, if either I have.  I though 12.04.5 LTS was based on Wheezy.

Chopra

---

### Post by schragge on 2014-12-31
Yes, sure, Ubuntu 12.04 is based on Debian Wheezy, and the howto is pretty old. So what? I don't think the using of SendEmail has drastically changed since then.

[highlight]Update[/highlight]
Just installed it on vivid with
```
sudo apt-get install sendemail
``` and sent a test email. It still works. Actually, to be able to send mails through the smtp.gmail.com server you need to enable [access for less secure apps]("http://access for less secure apps") in your Google account. And contrary to what the howto says, you should specify the full Gmail account name including the @gmail part on the command line. You also need to specify the port 587 on smtp.gmail.com. So, the full command line would look like this:
```
sendEmail -f your.account@gmail.com -t your.account@gmail.com -u 'Mail subject' -m 'Mail text' -s smtp.gmail.com:587 -o tls=yes -xu your.account@gmail.com
```

The output of *sendEmail --help networking* contains more information about this.

---

### Post by nerdtron on 2014-12-31
> **chopra said:**
> Hi guys,

I'm trying to experiment with simple email programs from the comand line.  I've tried:

mail  [EMAIL="my_email_address@domain_name.com"]my_email_address@domain_name.com[/EMAIL]
I get an exit code of zero (success) but the mail isn't arriving to my inbox of either emails, the primary, or the one I cc'd.

Not sure what I'm doing wrong.


And what is the mail.log says when you send the email? does it successfully send the email?

---

### Post by chopra on 2015-01-01
> **nerdtron said:**
> And what is the mail.log says when you send the email? does it successfully send the email?

I don't have a mail.log file in my home directory anywhere. What directory should I look under for it?

Chopra





> **schragge said:**
> Yes, sure, Ubuntu 12.04 is based on Debian Wheezy, and the howto is pretty old. So what? I don't think the using of SendEmail has drastically changed since then.

[highlight]Update[/highlight]
Just installed it on vivid with
```
sudo apt-get install sendemail
``` and sent a test email. It still works. Actually, to be able to send mails through the smtp.gmail.com server you need to enable [access for less secure apps]("http://access for less secure apps") in your Google account. And contrary to what the howto says, you should specify the full Gmail account name including the @gmail part on the command line. You also need to specify the port 587 on smtp.gmail.com. So, the full command line would look like this:
```
sendEmail -f your.account@gmail.com -t your.account@gmail.com -u 'Mail subject' -m 'Mail text' -s smtp.gmail.com:587 -o tls=yes -xu your.account@gmail.com
```

The output of *sendEmail --help networking* contains more information about this.


Ahh, the problem is coming into more focus.  I entered the command you mentioned (although I don't have a gmail account anymore, I used hotmail in place), and it prompted me for a password, which it displayed on my screen as plain text.  Regardless of what password was entered, it had this error message:

Jan 01 21:55:04 hp-notebook sendemail[4917]: ERROR => No TLS support!  SendEmail can't load required libraries. (try installing Net::SSLeay and IO::Socket::SSL)

---

### Post by schragge on 2015-01-01
Ok, install the libraries:
```
sudo apt-get install lib{net-ssleay,io-socket-ssl}-perl
```
BTW, the log files are in /var/log

---

### Post by chopra on 2015-01-02
> **schragge said:**
> Ok, install the libraries:
```
sudo apt-get install lib{net-ssleay,io-socket-ssl}-perl
```
BTW, the log files are in /var/log

Okay, well, that got me further.  According to the message, it says email was sent successfully.  However, I didn't recieve it, and when I looked at the mail.log file, it said connection timed out.  In fact, that's what the log has been saying for all of my attempts with mail as well as sendemail.

Here's the output:
Jan 02 20:30:06 hp-notebook sendemail[4840]: NOTICE => Authentication not supported by the remote SMTP server!
Jan 02 20:30:06 hp-notebook sendemail[4840]: Email was sent successfully!

And here's the log file's message:
Jan  2 20:31:37 HP-Notebook postfix/smtp[4846]: connect to mx1.hotmail.com[65.55.92.136]:25: Connection timed out

---

### Post by schragge on 2015-01-03
Hmm, not sure if it's relevant here, but instead of *mx1.hotmail.com* I'd try *smtp.live.com*

---

### Post by chopra on 2015-01-06
> **schragge said:**
> Hmm, not sure if it's relevant here, but instead of *mx1.hotmail.com* I'd try *smtp.live.com*

Okay, this is odd.  I just recieved the message in my inbox today.  I never entered mx1.hotmail.com, I entered my email at hotmail.com.  Anyway, the message went through, it just took a really long time.  That still doesn't explain why mail and mutt weren't working, but at least I can send emails.  Could any of this be related to hardware or installation?  I recently purchased a brand new laptop, and am going to install Ubuntu 14.04 on it, (this one has 12.04.05), so this may solve the problem.

Thanks, Chopra

---

### Post by schragge on 2015-01-06
Well, I'd rather suspect Microsoft servers delaying mail delivery from unconfirmed IPs. See [https://mail.live.com/mail/troubleshooting.aspx](https://mail.live.com/mail/troubleshooting.aspx) and also [this answer]("http://answers.microsoft.com/en-us/outlook_com/forum/oemail-osend/why-are-the-emails-sent-to-microsoft-account/b64e3e4a-0d93-40c8-8e28-4be849012f9c") from Microsoft.

> **chopra said:**
> I never entered mx1.hotmail.com, I entered my email at hotmail.com.
How that? I mean the part I marked [COLOR=red]red[/COLOR] below
```
sendEmail -f your.account@hotmail.com -t your.account@hotmail.com -u 'Mail subject' -m 'Mail text' [COLOR=red]-s smtp.live.com[/COLOR] -o tls=yes -xu your.account@hotmail.com
```

---

### Post by chopra on 2015-01-07
Excellent! That last part got the email sent immediately! Thanks for your help.

---

