---
title: "Problem on sending webmail"
date: 2017-04-22
forum: General Help
---

### Post by satimis on 2017-04-22
Hi all,

Firefox running on Ubuntu 16.04
Squirrel webmail
Godaddy server

Sent a webmail online with attachment about 20M.  The webmail sent without problem and received correctly by the recipient together with the attachment.  But there is no record on the Sent Folder.  I have tested 3 times having the same result.  Please advise how to fix the problem.

This problem has occurred in the past when I sent a webmail with big size attachment.

Regards
satimis

---

### Post by RobGoss on 2017-04-22
Hello and welcome, is this Squirrel web-mail on a hosted service?

---

### Post by satimis on 2017-04-22
> **RobGoss said:**
> Hello and welcome, is this Squirrel web-mail on a hosted service?
Hi,

Yes.  

It looks a little bid funny to me, the webmail sent.  There is no error message popup, only no record on the Sent Folder.

I have looked at 
-> Options on SquirrelMail

and couldn't discover any item there related.

Regards
satimis

---

### Post by RobGoss on 2017-04-22
I also use Ubuntu 16.04 along with Squirrel Mail, just sent a test email everything seems to check out OK, I went in to the sent folder and there was the email I sent to my other email address. I suggest giving your hosting service a call and see if they might assist you with trying to figure this issue out

You are using Squirrel Mail from your web browser correct? you don't have it installed on your desktop

---

### Post by satimis on 2017-04-22
> **RobGoss said:**
> I also use Ubuntu 16.04 along with Squirrel Mail, just sent a test email everything seems to check out OK, I went in to the sent folder and there was the email I sent to my other email address. I suggest giving your hosting service a call and see if they might assist you with trying to figure this issue out
Hi,

Thanks for your advice.

I suspect whether it is the config problem of SquirrelMail, because sometimes it worked and another failed without the sent webmails in the Sent Folder.  Disregarding whether successful or failure all webmails were sent out without problem and received by the recipients.

The attachment of the webmails are .pdf files of total size about 20M

> 
You are using Squirrel Mail from your web browser correct? you don't have it installed on your desktop
Yes.  I'm working on a Host box of VirtualBox machine.  I think I have to create a VM and install a mail client on it.

What will be your recommendation?  I have about 10 webmail accounts on SquirrelMail


Edit
===
A further thought I have >30 VMs on this box running Ubuntu16.04 desktop/Windows10 etc.  I prepare to install 2 mail clients on 2 Ubuntu16.04 VMs connecting the users on Godaddy's online webmails.

Which Mail client would you, folks, recommend?

Unity Mail ?
[http://www.omgubuntu.co.uk/2016/09/install-unity-mail-ubuntu-16-04-ppa](http://www.omgubuntu.co.uk/2016/09/install-unity-mail-ubuntu-16-04-ppa)

Trojita ?
Trojita Is a Super Fast Desktop Email Client for Linux
[http://www.omgubuntu.co.uk/2017/02/install-trojita-email-app-ubuntu](http://www.omgubuntu.co.uk/2017/02/install-trojita-email-app-ubuntu)

6 Email Clients for Ubuntu Users ?
[http://www.linuxey.com/6-email-clients-for-ubuntu-users/](http://www.linuxey.com/6-email-clients-for-ubuntu-users/)

etc.

Regards
satimis

---

### Post by RobGoss on 2017-04-22
I've only used about two of the listed email clients  Thunderbird, Evolution. They seem to be very good and have just about everything needed for sending and receiving emails.. I don't use them that much but they were the first two I tried out for my desktop

---

### Post by satimis on 2017-04-22
> **RobGoss said:**
> I've only used about two of the listed email clients  Thunderbird, Evolution. They seem to be very good and have just about everything needed for sending and receiving emails.. I don't use them that much but they were the first two I tried out for my desktop
Hi,

Thanks for your advice.

Thunderbird is already running.  Just tried it sending mail with large size files attached.  It worked sending the mail with a copy retained in the Sent Box.  For attached files with total size=52.8 MB the mail can't be sent with following warning;```

There are large files.  It might be better to use Filelink instead

```
What is Filelink?  Can the recipient obtain the files if I turn off the PC?

Beside I couldn't delete the copy mail sent in the Sent Folder.  Following link doesn't help;
[https://support.mozilla.org/en-US/kb/cannot-delete-messages](https://support.mozilla.org/en-US/kb/cannot-delete-messages)

I couldn't find "Application Basics section"

Any suggestion?

Thanks

Regards
satimis

---

### Post by RobGoss on 2017-04-23
You can read about Filelink here, [https://support.mozilla.org/en-US/kb/filelink-large-attachments](https://support.mozilla.org/en-US/kb/filelink-large-attachments)

---

