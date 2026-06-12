---
title: "email on multiple computers"
date: 2008-04-26
forum: General Help
---

### Post by gairy_s on 2008-04-26
I am now using Ubuntu on both my laptop and my desktop, and I almost have my daughter converted. I also took an old PC and turned it into a home server (Samba). I am still a noob to Ubuntu, so I know this is probably a dumb question. I'm not sure how to set this up. I wanted to use fetchmail on my server to get my mail from my ISP, but what do I do from there. I know POP3 downloads the emails to the local computer and deletes then from the server. I wanted to use Evolution on both, and have both use the server, however I need to access my emails on my laptop when I'm out. Could someone please explain how to do this, or give me some suggestions? Thank you in advance.

---

### Post by tamoneya on 2008-04-26
the easiest way is to use IMAP.  Check to see if your ISP offers it.  I have three email accounts and two computers.  I use IMAP with all three and thunderbird on both computers.  It works flawlessly.

---

### Post by gairy_s on 2008-04-26
Unfortunately I use Comcast, so it's a POP3 server.

---

### Post by tamoneya on 2008-04-26
forward all of your mail through gmail and then configure gmail to send mail through comcast.  Then use gmails IMAP service in order to not have to worry about the difficulties caused by pop3

---

### Post by HermanAB on 2008-04-26
You can configure any POP client to 'Leave Mail on Server' for a period of time.  To keep a desktop and laptop mail client in the same state, it is usually sufficient to make the 'leave' or 'keep' 10 days or so.  That will allow both systems adequate time to download the mail without overflowing the mailbox on the server.

---

### Post by gairy_s on 2008-04-27
Thank you all for you immediate response. I went to bed and stated thinking about this because I still have a Windows partition on my laptop because Boson NetSim that I need for school won't run in Wine. Then I thought about Thunderbird and sharing the profiles through the server. I found a post about how to do it.
[http://ubuntuforums.org/showthread.php?t=203524]("http://ubuntuforums.org/showthread.php?t=203524")
I want to thank all of you for answering me and giving me some good ideas.

---

### Post by gairy_s on 2008-04-27
tamoneya, I've done a lot of reading in the past few hours, and I believe I would better benefit from your suggestion. If I am on the road and have to access my email from another computer, gmail has a web-interface, so that would cover one area I've been trying to figure out. Would it be possible to get you to go into greater detail? Sharing profiles using IMAP would be nice, but using Gmail should cover everything I need. Thank you in advance.

---

### Post by dondad on 2008-04-27
> **gairy_s said:**
> tamoneya, I've done a lot of reading in the past few hours, and I believe I would better benefit from your suggestion. If I am on the road and have to access my email from another computer, gmail has a web-interface, so that would cover one area I've been trying to figure out. Would it be possible to get you to go into greater detail? Sharing profiles using IMAP would be nice, but using Gmail should cover everything I need. Thank you in advance.

I have 5 different e-mail addresses that all end up in my gmail account. I then set up imap with gmail and thunderbird so that I can use thunderbird, or I can use the web interface to see it from anywhere. Gmail has some settings to periodically check other accounts and download the mail to gmail. My others are all pop accounts, so gmail gets the mail and then deletes it from the servers. All of the gmail stuff stays there and syncs with thunderbird. Works great.

You can also set it up so that as mail comes in from the other accounts, it gets a label attached so that you can tell which account it came from. It is also nice because, although the default is to reply or compose from the gmail address, you can pick any address that you use to use as the reply or send address.

---

### Post by gairy_s on 2008-04-27
I have set up one account so far, and grabbing the mail was straight-forward. I'm about to do the others in a minute. One question though. If I create folders in Thunderbird to organize my mail, will this reflect to Gmail? The reason I am asking is that I have 2 dual-boot computers, and depending on where I am at and what I am doing, when I check email in all of the clients, do I have to separate for each one? Or when I do it to one client, will it feed back to Gmail that I have created folders and then relay this to my other clients? This is the first time I have used an IMAP e-mail server before, so I'm not sure how it works.

Also, is there a way to forward my contacts to gmail? I only have contacts set up on one of them.

---

### Post by gairy_s on 2008-04-27
Found it and yes, folders to appear in gmail when you create them in Thunderbird. But I did save two contacts in the Collected Addresses folder of my contacts in Thunderbird and they didn't show up in Gmail.

---

