---
title: "mailed read in Evolution stays unread on server"
date: 2008-01-31
forum: General Help
---

### Post by pytheas22 on 2008-01-31
When I read mail in Evolution, it remains marked as unread on the server.  In other words, if I read my mail in the morning using Evolution, and then a few hours later check my mail on a public computer using webmail, all the messages that I had read in Evolution earlier are marked as unread--and if I don't read them in webmail, they will appear again as unread the next time I check mail in Evolution.  If I restart Evolution things seem to synchronize, but sometimes I let it go for days and get frustrated when I have to sort through a hundred messages a second time because Evolution apparently doesn't update information with the server until it gets restarted.

The only option that I can find in preferences that looks like it would be related to this is "Automatically synchronize remote mail locally."  I have it checked but it makes no difference.  If anyone knows of a way that I can make make Evolution update changes continually with my mail server besides restarting the program frequently, please let me know.

---

### Post by aonegodman on 2008-02-02
I think I'm having the same problem, not sure.

When Evolution gets my email I go through it and delete them, but it appears that it is grabbing the same mesages over and over again.

I now have over 6700 email mesages in my INBOX on Evolution and most are duplicate sets of downloads.

The only way I can stop it is to shut down Evolution. I need help too.  :(

---

### Post by pytheas22 on 2008-02-02
Your problem might be the same but I'm not sure.  Evolution for me doesn't keep downloading messages second and third times; it just downloads them again if I check my mail on another machine without restarting Evolution first.

As a possible solution, you could try using Thunderbird instead.  That program was unstable for me, but I think I am an exception, as it's a very popular mail application.

Better, if anyone knows how to make Evolution synchronize continuously with the mail sever, post please!

---

### Post by dcstar on 2008-02-03
> **pytheas22 said:**
> When I read mail in Evolution, it remains marked as unread on the server.
...........
The only option that I can find in preferences that looks like it would be related to this is "Automatically synchronize remote mail locally."  I have it checked but it makes no difference.  If anyone knows of a way that I can make make Evolution update changes continually with my mail server besides restarting the program frequently, please let me know.

You have to specify if your are using POP or IMAP, I use POP access on 3 accounts in Evolution and have no problem at all.

---

### Post by Kevin Funnell on 2008-02-03
Check your Evolution Mail Account settings (Edit/Preferences/Mail Accounts) select the account you want to check (select Edit/Receiving Options), you may have the check box selected to leave messagesl on server. Old Kevin

---

### Post by accatagon on 2008-02-03
POP3 does not have any mechanism for marking messages as read. It has a mechanism for deleting messages, but is primarily intended for the same use as its name (Post Office Protocol) indicates: that is, it is meant to drop off the messages and delete them off the server. If you wish to have the more advanced functionality of marking messages of the server as read or unread, then use IMAP. Otherwise, you can set evolution to delete messages that it has downloaded, but I don't know if that's what you want.

---

### Post by pytheas22 on 2008-02-03
Thanks for the responses.

I'm using IMAP.  If I used POP (which I have the option to do) I wouldn't be able to leave mail on the server in order to access it from different locations, I thought.  Is this not true?  I frequently need to read mail from different computers and like to leave messages on the server so they can be accessed from anywhere.
> 
Check your Evolution Mail Account settings (Edit/Preferences/Mail Accounts) select the account you want to check (select Edit/Receiving Options), you may have the check box selected to leave messagesl on server.

I don't have an option for this.  Below is a screenshot of my receiving options tab.  Is it not the same as other people's?

---

### Post by prince_niceguy on 2008-02-04
I too am using imap with gmail and evolution keeps the mail unread and in case internet is down when closing evolution then the mails remains on the server as unread. This is really pain, not sure if it is a bug in evolution or not.

---

### Post by tgrimley on 2008-06-05
Is there any solution to this?

---

