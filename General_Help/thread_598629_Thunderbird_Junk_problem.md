---
title: "Thunderbird Junk problem"
date: 2007-10-31
forum: General Help
---

### Post by scottishnarn on 2007-10-31
I'm using 7.10 with thunderbird 2, with my email kept on a imap server running on another Ubuntu box (6.10). When I access email in windows with thunderbird if I select a message and mark it as junk it automatically gets moved to my junk folder. However, in Ubuntu using the same version of thunderbird when I mark a message as junk it just sits in my inbox marked as junk. I have the box ticked in the settings for the account to move messages to the Junk folder. 

(Under the advanced server settings I have set the IMAP server directory to INBOX. as required by courier imap server so everything is not a sub folder of INBOX, same as in the windows version.)

Any ideas about any other settings I might try?

Thanks

---

### Post by skyjacker on 2007-10-31
> **scottishnarn said:**
> I'm using 7.10 with thunderbird 2, with my email kept on a imap server running on another Ubuntu box (6.10). When I access email in windows with thunderbird if I select a message and mark it as junk it automatically gets moved to my junk folder. However, in Ubuntu using the same version of thunderbird when I mark a message as junk it just sits in my inbox marked as junk. I have the box ticked in the settings for the account to move messages to the Junk folder. 

(Under the advanced server settings I have set the IMAP server directory to INBOX. as required by courier imap server so everything is not a sub folder of INBOX, same as in the windows version.)

Any ideas about any other settings I might try?

Thanks I use strictly Unbunu and have the same problem.  If you find a solution, please post it for others to see.

---

### Post by volksman on 2007-10-31
If you use IMAP you need to set the setting on a per account basis....Go into TB and hit the Edit -> Account Settings

Under the account in question hit the "Junk Settings" and adjust accordingly...

---

### Post by scottishnarn on 2007-10-31
Found the solution. It's amazing after struggling with this for months, as I finally post a question it's then I find the solution. 

First, I did have the settings in the account bit set correctly, it was the bit under preferences that I needed to edit.

Go to Edit -> Preferences 
Then Privacy -> Junk
Select When I mark messages as Junk Move them to the Accounts Junk folder.

Why this setting is hidden here I'll never know, I must have selected this in my windows setup years ago and forgotten when it came time to sort it out under linux.

---

### Post by skyjacker on 2007-10-31
> **scottishnarn said:**
> Found the solution. It's amazing after struggling with this for months, as I finally post a question it's then I find the solution. 

First, I did have the settings in the account bit set correctly, it was the bit under preferences that I needed to edit.

Go to Edit -> Preferences 
Then Privacy -> Junk
Select When I mark messages as Junk Move them to the Accounts Junk folder.

Why this setting is hidden here I'll never know, I must have selected this in my windows setup years ago and forgotten when it came time to sort it out under linux.
 Interesting, I set this same item up the day I installed T-bird, and mine still does not work right.:confused:

---

### Post by avantgardaclue on 2007-11-20
> **skyjacker said:**
> Interesting, I set this same item up the day I installed T-bird, and mine still does not work right.:confused:

Same here, someone must know the answer!!!

Please.....

---

### Post by avantgardaclue on 2007-11-28
Go to tools -> add-ons -> get extensions -> download Thunderbayes to you desktop and install... bingo works now! (Important to download to your desktop first and NOT run from server) :)

---

### Post by Wim69 on 2007-12-21
What worked for me is: change the setting under Edit, Preferences, Account Settings, Junk Settings and then Move new junk messages to: Other, and select the Junk folder of the account (in my case, Local Folders).

Offcourse I did all settings mentioned above...

Marking a message as Junk immediately moved the message to the Junk folder!

Regards,

Wim.

---

### Post by olavjunior on 2008-02-07
I've done all the above (except thunderbayes) 

When I mark a massage as junk, it moves it automatically to the junk-mail folder. But I get like 20 junk mails a day which are automatically marked as junk by the adaptive filter, and these are **not** automatically sent to my junk folder. Very annoying!

---

### Post by avantgardaclue on 2008-02-08
I finally installed spamato and now i have no problems what so ever, works beautifully!

---

### Post by olavjunior on 2008-02-14
> **avantgardaclue said:**
> I finally installed spamato and now i have no problems what so ever, works beautifully!

Good for you! I've just installed spamato, but I can't see it working yet..

But whyyy can't the filter & rules natively in thunderbird work??? It just don't do what it's supposed to do! (move the spam-mails to spam)

---

### Post by avantgardaclue on 2008-02-15
If i recall, it takes a fews days worth of training to get it working properly.

Can't explain why tbird's own spam filter doesn't work, but now i don't care!!:)

---

### Post by olavjunior on 2008-02-15
How do you train it? Just move the junk to spamato's folder?

---

### Post by olavjunior on 2008-02-16
EDIT: Deleted (stupid me)

---

