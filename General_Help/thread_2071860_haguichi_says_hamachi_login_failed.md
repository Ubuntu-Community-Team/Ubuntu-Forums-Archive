---
title: "haguichi says hamachi login failed"
date: 2012-10-16
forum: General Help
---

### Post by Nikolai D. on 2012-10-16
Hi guys and girls,
I need to access my providers network, or my home network to configure the Outlook on my Ubuntu 12.04 install at my work PC with Home settings. Because this is currently only thing holding me from Using ubuntu at work. Im not an Outlook power user. Thunderbird is even good for me. Its just that i dont want to do email via webmail.
So to be able to access my home network i have installed Hamachi and Haguichi at home on my mac where i have Ubuntu 10.04 64bit (Super OS version actually). And it works. And at this work laptop Hamachi works on Windows. To prove the point that its not one of the ports disabled on the network or something. But on 12.04 64bit it says Cannot logon.
Any suggestions please?

Thanks in advace,
Nikolai

---

### Post by Nikolai D. on 2012-10-17
nobody? :)

---

### Post by Nikolai D. on 2012-10-29
still no any suggestions?:)

---

### Post by ztefn on 2012-11-03
Have you tried the solution from [this thread]("http://community.logmein.com/t5/Hamachi/Debian-hamachi-login-failed-error-8/m-p/75939#M5503") to fix the logging failed error? It worked for me when I got this error after upgrading from the legacy Hamachi client.
 
But for accessing your mail from anywhere isn't it simpler to use [IMAP]("http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol")? Or is the mail server not connected to the interwebs?

---

### Post by Nikolai D. on 2012-11-15
Hi Ztefn, im going to take a look at the link you posted right away.
Just wanted to say that the other day i was doing some research on the web. And found this that sounded like somethign that could help. But i still havent got it working yet. [http://community.logmein.com/t5/Hamachi/Can-t-login-or-connect-with-Linux/td-p/57406](http://community.logmein.com/t5/Hamachi/Can-t-login-or-connect-with-Linux/td-p/57406)

And yes, my home providers network is not accessible from my work. (Obviously?) :)

---

### Post by Nikolai D. on 2012-11-15
Just tried suggestion at ur link. Doesnt help. And i think ive already tried it before.

---

### Post by ztefn on 2012-11-15
> **Nikolai D. said:**
> 
And yes, my home providers network is not accessible from my work. (Obviously?) :)

So you want to read your home mail from work. Why can't you just add your home mail account to Thunderbird? You shouldn't have to be on the actual network, mail servers are usually reachable from anywhere by a public domain name such as pop.myprovider.be

---

### Post by Nikolai D. on 2012-11-20
No, not the personal email.
I want to setup our organisations Excange in my Outlook 2007 that ive installed on Ubuntu on my work Email. But the mail server the central administation have priveded me doesnt work. Or i cant setup email with it. I have called the CA for a view times. But they couldnt help me directly. Or the person who knew all the Exchange server stuff wasnt there. So i tought to try to set it up with the settings that are provided for employees using exchange at home.
I consider this being something more for my pleasure then actually serious work related issue to keep bothering them.
But i guess i try figure it out one more time with the right exchange server settings.

---

