---
title: "Correction to Evolution email setup"
date: 2008-07-09
forum: General Help
---

### Post by Ray Shive on 2008-07-09
Apparently I set up the send receive protocols incorrectly. Now I can neither sen nor receive email NOR can I find a way or a place to correct my settings. Thank you for any help.

---

### Post by Titan8990 on 2008-07-09
Let me look into my crystal ball and see what email service you are using, what kind of servers they have, and how your Evolution is currently set up....

---

### Post by Ray Shive on 2008-07-09
> **Titan8990 said:**
> Let me look into my crystal ball and see what email service you are using, what kind of servers they have, and how your Evolution is currently set up....
Did I detect a small note of sarcasm? <grin>

It's Yahoo! Plus Email

I used . . .

Plus.pop.mail.yahoo.com and . . 
Plus.smtp.mail.yahoo.com

I think. But again, I can't find a way to even check what I used, let alone correct anything or change it.

---

### Post by Titan8990 on 2008-07-09
I don't have any experience with that particular service. Some just won't allow you to use your own MUA. 

To change you setting in Evolution you go to CTRL+SHIFT+S -> Click on Your Account -> and Click Edit button on the right.

A quick way to check if things are working correctly is to have Evolution "check for supported authentication types" (will be a button under recieving options). If it fails to reach the server or does not cross some AUTH types off the list then you are probably not hitting the right server or something is blocking you from doing it.

---

### Post by plucky on 2008-07-09
You need to add port numbers to your servers in Evolution i.e
```
Plus.pop.mail.yahoo.com:465
Plus.smtp.mail.yahoo.com:995
``` and also select **SSL** secure connection for both POP and SMTP servers.

Good Luck

---

### Post by Ray Shive on 2008-07-09
> **plucky said:**
> You need to add port numbers to your servers in Evolution i.e
```
Plus.pop.mail.yahoo.com:465
Plus.smtp.mail.yahoo.com:995
``` and also select **SSL** secure connection for both POP and SMTP servers.

Good Luck

Thank You!!

---

### Post by Titan8990 on 2008-07-09
Don't forget to mark your thread as solved :).

---

### Post by Ray Shive on 2008-07-09
Yes I'd like to but I don't see where that option is offered. I am the greenest of newbies here. Sorry.

---

### Post by plucky on 2008-07-09
> Yes I'd like to but I don't see where that option is offered




[color=red]Thread Tools[/color] at top of page

---

