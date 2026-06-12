---
title: "Evolution mbox error"
date: 2008-01-03
forum: General Help
---

### Post by Alt69 on 2008-01-03
Hi, i have rebuilt my desktop and while in the process of rebuilding, I changed the name of user where my evoulution mailbox pointed to. I had a generic user id, but have now switched to a named user. I had backuped up the mailbox and restored it under the name of the user.

When I am sending or recieving messages I get the following error:
"Failed to append to mbox:/home/public/.evolution/mail/local#Sent: Cannot get folder: /home/public/.evolution/mail/local: No such file or directory. Appending to local 'Sent' folder instead."

I did not recreate the public folder on the new image. What I would like to do is have the email append to "mbox:/home/user1/.evolution/mail/local#Sent:". The directory for user1, does exist.

While, the desired outcome of appending to the "local folder", is what I am looking for as the user is logged in with their id. However, I would like to stop getting this error by changing where the mailbox points to.


Any suggestions on how to do this?

thanks

---

### Post by dcstar on 2008-01-03
> **Alt69 said:**
> Hi, i have rebuilt my desktop and while in the process of rebuilding, I changed the name of user where my evoulution mailbox pointed to. I had a generic user id, but have now switched to a named user. I had backuped up the mailbox and restored it under the name of the user.
.........

Backing up and "restoring" does not change the user permissions of files.

Change the files you restored to the correct owner permissions and things should be better.

---

### Post by spleencheesemonkey on 2008-02-15
To save some time configuring my evolution on my usb install, i backed up the settings/mailbox from my desktop pc to put onto usb install. it seemed to be a pretty good decision until i send an email from my usb install when i get the following message:

Failed to append to mbox:/home/<username>/.evolution/mail/local#Sent: Cannot get folder: /home/<username>/.evolution/mail/local: No such file or directory
Appending to local `Sent' folder instead.

this is because my home directory on my usb install is /home/ubuntu/ but my desktop pc install does not have the same path.  

Does anyone have any suggestions of how to get evolution to point to a different directory to store the sent items?

Hope this makes sense.

---

### Post by dcstar on 2008-02-15
> **spleencheesemonkey said:**
> To save some time configuring my evolution on my usb install, i backed up the settings/mailbox from my desktop pc to put onto usb install. it seemed to be a pretty good decision until i send an email from my usb install when i get the following message:

Failed to append to mbox:/home/<username>/.evolution/mail/local#Sent: Cannot get folder: /home/<username>/.evolution/mail/local: No such file or directory
Appending to local `Sent' folder instead.

this is because my home directory on my usb install is /home/ubuntu/ but my desktop pc install does not have the same path.  

Does anyone have any suggestions of how to get evolution to point to a different directory to store the sent items?

Hope this makes sense.

You can make a softlink called what the application needs to anything you are actually using.

---

### Post by spleencheesemonkey on 2008-02-16
Thanks for your reply.

How does one go about creating a soft link?

Have a funny feeling that it may be beyond me - but if you have a link/information as to how to do this, it will be interesting to see.

---

### Post by chantra on 2008-03-07
$ sudo ln -s /home/myuser /home/erroruser

where erroruser is the name in the popup message

---

### Post by chantra on 2008-03-20
I fixed the issue as per 
[http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox]("http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox")

hope this helps

---

