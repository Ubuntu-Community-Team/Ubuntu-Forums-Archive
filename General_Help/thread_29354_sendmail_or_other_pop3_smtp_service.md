---
title: "sendmail or other pop3 smtp service"
date: 2005-04-24
forum: General Help
---

### Post by crazybill on 2005-04-24
I am presently using FreeBSD with sendmail as a POP3 and SMTP email server.

I was considering changing my email server from FreeBSD to a Ubuntu Linux machine. 
Some questions:
Is anyone else out there doing this? 
Are you using sendmail.. or antoher daemon?

I noticed that sendmail can be installed with apt-get install sendmail. If you have done this, what modifications have you made to the configuration files?

---

### Post by ifrflyer on 2005-04-24
Just as an idea, you might want to explore routing your mail 

fetchmail ->SMTP -> Postfix -LMTP -> Amavisd (Spam Assassin/Razor/ClamAV) -> LMTP - POstfix ->Maildir

And then doing IMAP using Courier-Imap.

It's a rock solid setup.

---

### Post by crazybill on 2005-04-24
ifrflyer,

Where can I get details on that?

---

### Post by ifrflyer on 2005-04-24
Well, I got lots of help on the IRC channels for each of the apps individually and then for the whole setup in general. 

I know that you can apt-get all the individual packages for the project. I also know that this is a fairly common setup for ISPs, so there are many people out there who have done it. 

You need to stay focused on getting each piece of the puzzle working and it is in fact fairly straightforward to configure.

Dramatic moments come with amavis and clam configuration, and postfix's main and master.cf files. Accept the defaults as often as possible unless you have a reason to change them.

You already probably have postfix installed. 

There's no order in which you must do it. 

1. Get postfix up and running, and its daemon running. 
2. Get amavisd and make certain you have the clam av and spamassassin modules. each has conf files whose defaults are fairly useful and almost work out of the box. 

3. Edit /etc/postfix/main.cf and master.cf to send the mail out from postfix to amavisd and specify that you want mail to go to maildirs, determine which one (I use $user/.maildir). Google "postfix amavisd config" and you'll find samples. 

4. Get fetchmail to poll your internet mail servers to get the mail and bring it back to postfix. 

5. Set up courier Imap to serve the mail locally. 

Additionally, I set up a dyndns pointer account to point to my mail server behind the firewall locally. You open your ssh port and use port forwarding to allow you to connect to your mail sever securely from any internet connection.  Once the setup is all working you do something like:

sudo ssh -c blowfish -L 143:localhost:143 -L 25:localhost:25 -l username dyndnsdomain.com -N -f

Believe me I did not come up with this on my own - i had *lots * of help. Once you run that command you'll get hit for the password, first for sudo and second for your server (make sure your server's sshd is running). Once connected, this forks into the background and will stay active.

Then set your mail client to look to localhost for mail, and voila! it's there. And the command above also provides compression as well, which apparently makes imap mail much, much faster. 

That help?

---

### Post by crazybill on 2005-04-24
That does help. I will give it a try. The devil is in the details. If anyone knows of some good help URLs on this, I would appreciate your posting them. If I get this working on Hoary, I will post. Thanks.

I have run sendmail almost faultlessly for years on the same old openBSD machine, using my own  anti-spam and anti-unauthorized SMTPmethods. All I have had to do is modify config files and put some other files in to be read by sendmail. I have not done this multi-program approach before, but it sounds interesting.  I will give it a try.

If anyone has other suggestions, I am open to hearing from you!

---

