---
title: "newbie question"
date: 2005-05-28
forum: General Help
---

### Post by kimes on 2005-05-28
I've just start using linux environment..
and I'm so interested in mail server..
But I know nothing..  :) 

Anyway..
what email server like sendmail is set up basically in ubuntu hoary?
and where is configuration file?

Acutally I just wanna change my email address..
when I send something that mail tells that it is from localhost something..

---

### Post by roland on 2005-05-28
[QUOTE=kimes]

Acutally I just wanna change my email address..
when I send something that mail tells that it is from localhost something..[/QUOTE]

If I'm correct, you only wish to send e-mails properly on your computer. So what mail program do you use? For instance: Evolution, Mozilla Mail, Thunderbird, Pine, ... ? Sendmail is only the mailer, the mail program forms the user interface and it configures your email address. In other words: I didn't have to set up anything in sendmail, I only had to set up Mozilla Thunderbird on my own desktop to send e-mails properly from my own e-mail address.

---

### Post by thrift on 2005-05-28
If you already under the idea of a mail server and are just looking to understand what mailer is the default in Ubuntu, this may suit you better.

The default Mail Transfer Agent in Ubuntu Hoary is postfix.  It's init script is in /etc/init.d/postfix.

To see if it is currently running, you can open a terminal and do the following:
ps aux | grep postfix

If you recieve a couple lines that on the far right say things like qmgr,  pickup, smtpd, and proxymap.  You have it running right now.

If not you can start it by using the command:
sudo /etc/init.d/postfix start
<enter password>

or to stop it:
sudo /etc/init.d/postfix stop
<enter password>

It would help more if you would describe exactly what you are trying to do with it/why.

If you are trying to send mail via postfix and it is currently running, you can go to the command line and type:

mail [email]someone@somewhere.com[/email]
enter a subject
type your message
go to a new line and then put a single . and hit enter when you are done typing your message.
specify who to cc it to.

done.

I think that was what you were really looking for.

---

### Post by kimes on 2005-05-28
Thanks for the answers..

But what I was really looking for was just chaning my email address when I send something..

yhe.. actually I'm using mutt for my email client.. with gmail pop3 support..
I can fetch email from pop3 and also I can send some mails to anybody..

I tested how my emails look like, and released It shows up like the email is from localhost.. for example 'kimes@localhost' which is not what I intended..

I intended it is 'from [email]kimes@gmail.com[/email]' like something..
I thinks you guys can help me..

Thanks.. in advance..

---

### Post by thrift on 2005-05-29
This is kind of a hack, but you could change your hostname to be gmail.com.  That will work.  Other than that, the only way I know how to do it is to 

telnet 127.0.0.1 25

then use SMTP commands to send an email, but this is probably more than you are going to want to do for your average email.

There is probably a cleaner way to do this.  Can't you use google's SMTP server? That's what I do with evolution.

---

### Post by roland on 2005-05-29
[QUOTE=thrift]There is probably a cleaner way to do this.[/QUOTE]

I have never used mutt before (I'm a Pine user on the console), I found the following using "man muttrc" and google.

A simpler way of setting the from field is making a .muttrc file in your homedir with your favourite text-editor. Then add the line:

set from = [email]kimes@gmail.com[/email];

This should work. If you want to change the from-address "on the fly" when sending an e-mail, you can press *Esc* and then *f*, just before sending your e-mail. Now you can type in your own e-mail address.

---

