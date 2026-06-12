---
title: "shell email clients"
date: 2008-03-13
forum: General Help
---

### Post by nycjeff on 2008-03-13
I'm wondering if there are any command line type email clients. 
Basically I'd like to check my email when I ssh into my home computer, but I'd rather not have to worry about graphical applications because I'll probably be on a palm TX. 
Any thoughts would be appreciated.

---

### Post by HermanAB on 2008-03-13
The best one is called "mutt".  The little doggy should be in synaptic.

Cheers,

Herman

---

### Post by nycjeff on 2008-03-13
Thanks a bunch. I'll give that a try.
-jeff

---

### Post by jimmyridge on 2008-03-14
sendmail its simple no frills


james@Acer-4315:~$ sendmail [email]cypherpunk@fuse.net[/email]
subject:test
test body test 
<Ctrl+D>

low an behold my thunderbirdclient shows

subject                  sender 
test                     [email]james@Acer-4315.fuse.net[/email]

oh wait your looking for clients isnt there a "mail" cmd for local junk installed?

like sometimes you login and its like "you have 3 new mail messages"

---

### Post by shazzy on 2008-03-14
On a similar note, I seem to remember a way to send messages between users at the command line.  I forget the name of the program but it's from the olden days when multiple users would log into the same computer from different consoles.  It's a little outdated but it might be fun for my high-schoolers to mess around with.

---

### Post by finer recliner on 2008-03-14
alpine

---

### Post by scottro on 2008-03-14
You're probably thinking of mail. 

For example, if we're on the same computer

mail shazzy

I'll see something like subject:

(I could also do mail -s 'hi there' shazzy

I then have a blank line where I can type my message.
When done ctl + D (on Fedora, this will then give a cc: line, I don't think that's universal, however.)
If you get that cc: just hit enter, and the mail is sent.  (If you don't get the cc then then mail was sent when you hit ctl+d.

As for mutt, I have a page on it that some have found useful.
[http://home.nyc.rr.com/computertaijutsu/mutt.html](http://home.nyc.rr.com/computertaijutsu/mutt.html)

With mutt, although it has limited pop and smtp functionality, you're usually better off with 3rd party software for sending and receiving.  Mutt started with the basic Unix concept, do one thing and do it well. 

At any rate, it's probably the most popular email program among Unix geeks.

---

### Post by netlogic on 2008-03-16
simple and available package for all distros is mutt, but pine/alphine kicks major ***.

---

