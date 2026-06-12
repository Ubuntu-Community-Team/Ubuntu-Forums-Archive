---
title: "evolution exchange problem not showing all mail"
date: 2007-12-14
forum: General Help
---

### Post by vanndrage on 2007-12-14
i am having a problem with evolution using the exchange connector. evolution works great but it is now displaying all of my mail in my exchange connection. i have many sub folders to categorize all of my email in exchange and some of the folders display all items whether it is 1 or 2 emails or its 100 emails and then other folders may only show like 10 - 20 out of 50, the dates of the emails it shows is random also, some of the folders may be back in 2006 sometime or other folders may only show recent ones. i know the emails are all there on the server because i can log into my web based exchange and all the mail is fine there. i have 2 - 3gb of mail on the exchange server. any help would be very much appreciated.

---

### Post by qwill on 2008-01-02
I confirm having the same problem using evolution and the exchange plugin.

New emails are showing up correctly; however email already existing within the mailbox are not always shown.

The bug seams to appear when I previously opened outlook (on an other machine) and checked my email.

Qwill.

---

### Post by vanndrage on 2008-01-02
> **qwill said:**
> I confirm having the same problem using evolution and the exchange plugin.

New emails are showing up correctly; however email already existing within the mailbox are not always shown.

The bug seams to appear when I previously opened outlook (on an other machine) and checked my email.

Qwill.
This sounds right for the bug, because when i installed Ubuntu I was thinking I would be able to convert my PST to some other program like I read was possible on some different forums but found that it was going to be easier to just transfer my stuff into my exchange server and connect to it to get my emails. I put my PST into a xp machine w/ outlook 2003, connected to my exchange and transfered all emails, calendar and contacts to the exchange server. I then disconnected this unit and connected to my exchange server on my ubuntu machine, so outlook was opened on the exchange server prior to using evolution w/ exchange. Another issue that maybe you can confirm qwill if you are having is if you try to transfer any folders that contain subfolders from the exchange server to a local directory it does not copy any subfolders. If you try this only do it with TEST folders because when you do it, it takes away the folders from the exchange list.

---

### Post by saltydog on 2008-01-15
> **qwill said:**
> I confirm having the same problem using evolution and the exchange plugin.

New emails are showing up correctly; however email already existing within the mailbox are not always shown.

The bug seams to appear when I previously opened outlook (on an other machine) and checked my email.

Qwill.

My behaviour is a little bit different: evolution only shows old mail. New mails already checked by another computer (but still on the server) are not notified.

---

### Post by rodym on 2008-01-15
Check this post: [https://answers.launchpad.net/ubuntu/+source/evolution/+question/16787](https://answers.launchpad.net/ubuntu/+source/evolution/+question/16787) , your exchange cache in invalid, maybe due to the usage of outlook in between evolution-sessions. Good luck!

---

