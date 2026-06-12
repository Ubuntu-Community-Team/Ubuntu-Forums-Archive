---
title: "Thunderbird mail address question"
date: 2015-08-14
forum: General Help
---

### Post by michael-piziak on 2015-08-14
I have my friend in my personal address book.

I created a message to email his cell phone, he is a verizon cell phone user, but since he's in my personal address book I simply type in "Tommy" and I send him a message to his cell phone easily.

By the way, I have thunderbird address book to send the message to his verizon phone using "his.phone.number@vtext.com."

He receives the message and then replies to me.

However, his message to me in my Thunderbird inbox does not have his name as "Tommy" but instead in my inbox it has "his.phone.number@vtext.com"

So, to make this long story short, why doesn't Thunderbird simply tell me I have a message from "Tommy" in my inbox instead of his phone number followed by @vtext.com

?

---

### Post by deadflowr on 2015-08-14
What's the saved address' display name?
If you set only the first and/or last names, you can use those to fill in the email you write.
But you need to set the display name of him/her for it to show when you get email from them.
Otherwise you'll only see the senders address in full.

At least that is how it is for me...
(if that makes sense)

---

### Post by michael-piziak on 2015-08-14
In this screenshot you can see my address list and you can see that I have given him a display name.

Please examine this and advise.

And much thanks for your help !

p.s. He is Tommy Cochran in my address book.

---

### Post by michael-piziak on 2015-08-15
bump

---

### Post by SeijiSensei on 2015-08-16
I don't believe that Thunderbird consults the address book on incoming messages.  It simply displays the contents of the From: header.  My guess is that there is no "full name" field in the header Verizon attaches, so you don't see it.

---

### Post by Vladlenin5000 on 2015-08-16
> **SeijiSensei said:**
> I don't believe that Thunderbird consults the address book on incoming messages.  It simply displays the contents of the From: header.  My guess is that there is no "full name" field in the header Verizon attaches, so you don't see it.

+1

Exactly. I've tested and it always gets it from the email's header, not the address book.

---

### Post by michael-piziak on 2015-08-16
Intriguing.  I'll mark this thread as solved.

---

### Post by deadflowr on 2015-08-16
Go to  edit >> preferences >> advanced >> Reading and Display - Display  check the box for *show only display name for people in my address book*.
see if that does what you are wanting.

---

