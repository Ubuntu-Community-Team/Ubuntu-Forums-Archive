---
title: "Evolution exchange account"
date: 2007-11-20
forum: General Help
---

### Post by aitorcalero on 2007-11-20
I am using Evolution as client for a Exchange mail server. I have successfully configured everything, and all seems to work fine, but now I am receiving Server messages warning about "mailbox full". How can I setup evolution to download all of my email locally. Some mail client has the option to "leave messages on server" or not, but I cannot see this option en evolution. I was also trying to create some filters but, it does not seems to work. :(
Is there anyone out there using Evolution with an Exchange Server? :???:

---

### Post by ephro on 2007-11-20
In the Evolution preferences edit your exchange account and check the box that says "Automatically synchronize account locally". This will automatically download all your exchange emails to your computer. This won't help you with your account is full problem. To do that you need to set up local folders on your computer and move messages to them so they are deleted from the exchange server itself. Try it by hand for a little bit, but then you should be able to make some rules in Evolution so that it will move all messages older than a certain time to your local folders, which will in turn allow you not to have to do it by hand anymore.


Ephro

---

### Post by aitorcalero on 2007-11-20
> **ephro said:**
> To do that you need to set up local folders on your computer and move messages to them so they are deleted from the exchange server itself. Try it by hand for a little bit, but then you should be able to make some rules in Evolution so that it will move all messages older than a certain time to your local folders, which will in turn allow you not to have to do it by hand anymore.


But, how can I do this? Just right-clicking and selecting "Copy content locally...."? That how all my folders are already configured...

---

### Post by ephro on 2007-11-20
Just select multiple messages in you Inbox for example (click on one, then hold shift and click lower) then drag the selection to a local folder. This will remove it from the exchange server and permanently store them locally.

Think of it as moving a file from one hard drive to another. Copying it will still be leaving it on the exchange server, so you need to move the email.


Ephro

---

