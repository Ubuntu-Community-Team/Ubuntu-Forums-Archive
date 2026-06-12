---
title: "Problem in Thunderbird &quot;From&quot; field of &quot;Yahoo Groups&quot;"
date: 2014-12-03
forum: General Help
---

### Post by Sadi58 on 2014-12-03
This happened the other day when I did a fresh install of Ubuntu 14.10 64-bit in the hope of obtaining a better performance from my current system, which was incrementally upgraded in the last couple of years.
Because I didn't have this problem in my last configuration (probably the same Thunderbird version), I thought it might be related with a system-wide setting, although this sounds a bit odd to me.

**Problem**:
Suddenly I've starting seeing **Yahoo Group name** in the **From** field instead of the actual sender.

**Background:**
[COLOR=#333333][FONT=Lucida Grande]I think in May 2014 [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**Yahoo Groups**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] have changed the way they display information in message headers, particularly relating with [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**From/Sender**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] information.
[/FONT][/COLOR]_[COLOR=#333333][FONT=Lucida Grande]OLD FORMAT had this item in the Message Source:[/FONT][/COLOR]_
[COLOR=#333333][FONT=Lucida Grande]**From: User Name <user@mail.address>**[/FONT][/COLOR]
_[COLOR=#333333][FONT=Lucida Grande]NEW FORMAT has [/FONT][/COLOR]__[COLOR=#333333][FONT=Lucida Grande]this item in the Message Source[/FONT][/COLOR]__[COLOR=#333333][FONT=Lucida Grande]:[/FONT][/COLOR]_
[COLOR=#333333][FONT=Lucida Grande]**From: "User Name [EMAIL="user@mail.addres"]user@mail.addres[/EMAIL]s [Group]" <Group@yahoogroups.com>**[/FONT][/COLOR]
_[COLOR=#333333][FONT=Lucida Grande]and also this new item, which is the same as the OLD FORMAT [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**From**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] field:[/FONT][/COLOR]_
[COLOR=#333333][FONT=Lucida Grande]**X-Original-From: User Name <user@mail.address>**[/FONT][/COLOR]

I used to see (I guess between about a week after this started and this "fresh install") the NEW FORMAT **From** details as above, but after this fresh install I suddenly began seeing only the name of my Yahoo Group in the **From** field, which is very inconvenient especially when people don't sign their messages, and also when you want to sort the messages by sender, etc.


[LIST=1]
[*]Please can people using the latest TB under the latest Ubuntu receiving mail from Yahoo Groups inform me if they have the same situation or not?
[*]Please can somebody help me do something about this problem?
[/LIST]

---

### Post by amanchesterman on 2014-12-03
I don't receive mail from members of Yahoo Groups so I can't help you with question 1.
Regarding question 2, TBird stores the email addresses of incoming message senders in your Address Book -- I think they appear in the 'Collected Addresses' section. If you select the address of someone who has sent you mail you can edit the details using the 'Properties' button. There is a 'Display' field in which you can enter the name you want displayed in your Inbox and there is an option to 'always prefer display name over message header': this will ensure that instead of the Yahoo Group name you see the name by which you recognise the person. It means, of course, that you have to edit the Properties for each individual who sends you mail, but it might be a way forward if there aren't too many of them.

---

### Post by Sadi58 on 2014-12-03
Thanks a lot! I should have thought this!

Apparently, this *NEW FORMAT* **From** field info meant that Thunderbird began ignoring all Yahoo Group members different names and automatically displaying merely the Group Name as it was already recorded in my address book for that address, i.e. yahoo group address.

All I needed was simply **unchecking "*Always prefer display name over message header*"** :-)

Now in the **From** field I see each sender as "**User Name [EMAIL="user@mail.addres"]user@mail.address[/EMAIL] [GroupName] <GroupName@yahoogroups.com>**"

Stupid Yahoo Groups ; - )

---

