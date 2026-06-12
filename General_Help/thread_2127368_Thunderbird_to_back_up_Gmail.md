---
title: "Thunderbird to back up Gmail"
date: 2013-03-19
forum: General Help
---

### Post by parminides on 2013-03-19
I want to use Thunderbird to download my Gmail messages as an offline backup. I generally followed the directions at [http://www.webupd8.org/2011/03/how-to-backup-gmail-using-thunderbird.html](http://www.webupd8.org/2011/03/how-to-backup-gmail-using-thunderbird.html), although some of the steps were slightly different due to the age of the post.

But everything seemed to work. I started Thunderbird on my laptop and logged on to the email account I'd created. Thunderbird proceeded to download about 500 messages. Every time I quit and restarted Thunderbird, it would download about 500 additional messages. They were still in my Gmail. So far so good.

When I got home, I set up Thunderbird on my desktop (so I'd have 2 backups). I assumed that it would start downloading messages from the very beginning since Thunderbird on my desktop had no idea what my laptop had been doing. However, it didn't work that way.

It seems that my desktop started downloading messages where my laptop had left off. Apparently, the Gmail server is keeping track of my Thunderbird activity. This is a problem because I seek a single backup of all the messages in one place.

After some study, I discovered that the messages are stored in ~/.thunderbird/hreipadj.default/Mail/pop.googlemail.com/Inbox. Inbox is an actual file (not a folder) with the messages!

Other files in the pop.googlemail.com folder are Inbox.msf, Trash, Trash.msf, msgFilterRules.dat, and popstate.dat.

Is there a way for me to reset Thunderbird and/or the Gmail server and start over? Now that I know how it behaves, I can just download on one computer until it finishes. Alternatively, is there an easy way (or even a hard way) to merge the two Thunderbird inbox files, so that I will have a backup with all my Gmail messages together?

---

### Post by Slim Odds on 2013-03-19
It sounds like you're using POP. You should switch to IMAP.

---

### Post by parminides on 2013-03-19
Thanks for the quick reply but I need more detail than that. It's uber-critical that the messages remain on the Gmail server. I'm not just going to start changing things around willy nilly following suggestions offered without any explanation.

---

### Post by Slim Odds on 2013-03-19
Calm down....

IMAP is not going to run away with your computer. IMAP simply allows you to view and manage email that is on the server. It is much more capable than POP. POP is rather ignorant of messages on the server and that is why it much use "message ID #'s" to remember where it left off.

The Thunderbird client has settings that allow you do decide when messages get deleted from the server and when the body of the message get downloaded. YOU decide how that works.

You just have to enable IMAP from the Gmail settings (in the same screen that you used to enable POP).

Enjoy...

P.S. I just switched my linux desktop from POP to IMAP for Gmail just yesterday.

---

### Post by parminides on 2013-03-19
OK, OK. I'm calm. But I researched this issue of using Thunderbird to back up Gmail, and I came across multiple instances of people who accidentally lost all their Gmail messages and couldn't get them back. I really can't afford for that to happen to me. I will study IMAP vs POP some more. Right now, they're little more than two acronyms (that I don't even know what they stand for).

Thank you for your suggestion.

---

### Post by SuperFreak on 2013-03-19
I am not sure if this will help, but I set Gmail so any messages received are also forwarded to my Thunderbird account. It is in Gmail Settings/(Forwarding and POP/IMAP). This will not back up your Gmail archive but will work for future mail coming to Gmail. You could probably set up a folder in Thunderbird that receives all Gmail emails and only Gmail emals

---

### Post by xianbei on 2013-03-19
For "Archive" sync, check under Account settings > Copies & folders > Message archives > 

make sure that Keep message archives in... is checked. This works for my Gmail/Thunderbird on 12.10.

---

### Post by gifford on 2013-03-19
I think that what is causing the confusion is that the link described calls for creating a forwarding account for gmail. That would be the POP. It would allow for any gmail(which is IMAP) to also be forwarded to the created Thunderbird POP account.

If you allow Thundrbird to download gmail as an IMAP account, you would have mail physically on your computer. All that is required is to set up the gmail account as an IMAP in Thunderbird and set it to keep all mail. In Thunderbird settings for account settings, under synchronization and storage, be sure "don't delete any messages" is checked. So it would not matter from which computer you used, both the desktop and laptop would download the same messages.

---

### Post by pfeiffep on 2013-03-19
I strongly suggest that you consider Gmail's IMAP. I use Gmail to consolidate 3 email accounts:KS (yahoo, my isp, and gmail). 
Additionally I use Google Calendar so all my email and calendar info is available via web access from any PC  I choose to use since the email is stored on the server. 
Once you come to grips with IMAP you may designate certain folders to be available off line and available in Thunderbird. 
Calendar is an option in Thunderbird, however it is not available off line. 

One additional advantage is that my iPhone can access all the email and is synched with my Google Calendar and contacts.  If this sound interesting check out[ this link]("https://support.google.com/mail/troubleshooter/1668960?hl=en")

---

### Post by cross37 on 2013-03-19
I also use thunderbird and POP3 to backup my email.  Gmail remembers which emails have been downloaded via pop3 so that they will not be downloaded again.  Here is how to reset this and start over, making all the email downloadable again.  

Go to your GMail settings
Choose "**Forwarding and POP/IMAP**".
In the "POP Download" section, under "**1. Status**", select the radio button labelled "**[COLOR=#000000][FONT=arial]Enable POP for all mail[/FONT][/COLOR]**[COLOR=#000000][FONT=arial]** (even mail that's already been downloaded)**"
[/FONT][/COLOR][COLOR=#000000][FONT=arial]
If you don't want your email deleted from GMail after download, make sure that the "**2.  When messages are accessed with POP**" is set to "**Keep Mail's copy in the inbox**"[/FONT][/COLOR]

---

### Post by parminides on 2013-03-20
Thanks for all the replies. Sorry about my initial grumpiness, but I can't afford to lose all my messages on Gmail.

> **gifford said:**
> If you allow Thundrbird to download gmail as an IMAP account, you would have mail physically on your computer.

The email is physically on my computer now with the POP account. All the messages are in a huge file called  ~/.thunderbird/hreipadj.default/Mail/pop.googlemail.com/Inbox. I know they're there because I opened it in a text editor and looked.

> **cross37 said:**
> I also use thunderbird and POP3 to backup my email.  Gmail remembers which emails have been downloaded via pop3 so that they will not be downloaded again.  Here is how to reset this and start over, making all the email downloadable again.

[instructions omitted]  


This trick worked for me and more or less fixes my original problem. However, it would be nice if I could have complete but independent backups on my laptop and desktop. I will experiment with IMAP, which is what almost everyone recommends. So I won't mark the thread solved yet. 

Can I create separate IMAP and POP accounts in Thunderbird for the same Gmail account?

Thanks for all the help. As far as I know I haven't lost any messages yet.

---

### Post by pfeiffep on 2013-03-20
Not sure of your meaning of "separate imap and pop accounts" Accounts provide the ability to connect to mail servers via a protocol** [COLOR=#008000][SIZE=4]_P_ost _O_ffice _P_rotocol[/SIZE][/COLOR]** or**[SIZE=4] [COLOR=#008000]_I_nternet _M_essage _A_ccess _P_rotocol[/COLOR][/SIZE]**. 
So if you have one email address[SIZE=2]** user @gmail.com **Thunderbird will access the mail by using 1 of those 2 protocols. If you have another email account **user@isp.net** then you can configure Thunderbird to access isp.net with either pop or imap. 
So if I guessed correctly - The direct answer to your question about separate imap and pop accounts in Gmail is no if you want to use the same email address.

The method I outlined earlier will accomplish exactly[/SIZE]):P> "[COLOR=#000000]if I could have complete but independent backups on my laptop and desktop"  [/COLOR]
Here's a quick outline of how I would proceed:

[LIST=1]
[*]configure one of the two computers with thunderbird imap access (select the one with wired access if exists)
[*]arrange the email folders on that pc
[*]allow some time for the email to migrate (imap is a 2 way protocol)
[*]configure whichever folders you desire to have available 'off line'
[*]once you have the configuration the way your desire then all that should be necessary is to change to other computer's Thunderbird to imap (the folder heirarchy you created on first will migrate to second - no need to duplicate)
[*]You might need identify the folders you want for off line access again
[/LIST]

---

### Post by parminides on 2013-03-20
> **pfeiffep said:**
> So if I guessed correctly - The direct answer to your question about separate imap and pop accounts in Gmail is no if you want to use the same email address.

I did mean separate POP and IMAP accounts for the same email address.

Your outline of steps implies that POP and IMAP accounts for the same email address can coexist on separate computers. I know almost nothing about Thunderbird, but it's not clear to me why they couldn't coexist on the same computer. Both POP and IMAP are already enabled in Gmail.

However, that sounds like a recipe for losing some messages, so I'm not sure if I'll try to do it!

---

### Post by pfeiffep on 2013-03-20
Many email providers have both imap and pop access as a choice .... I do NOT suggest IMAP on one PC and POP on the other to access the same email account for a permanent solution!
On a single PC I believe that Thunderbird will only enable **one access method** to a single email account. 
This is a simplistic analogy - 
you can either drive your car to the bank OR you can take a bus to the same bank - at the same time you CANNOT take the bus and drive your car. 
imap and pop are only methods to access your email ... this has nothing to do with Thunderbird.

Might I suggest that you create a** test email account **at gmail and experiment with possibilities:popcorn:

---

### Post by parminides on 2013-03-20
> **pfeiffep said:**
> On a single PC I believe that Thunderbird will only enable **one access method** to a single email account. 
This is a simplistic analogy - 
you can either drive your car to the bank OR you can take a bus to the same bank - at the same time you CANNOT take the bus and drive your car.

I like that analogy. Admittedly, I am a Thunderbird novice (~24 hr of experience), but let me expand on it.

It seems to me that Thunderbird is the garage. The garage can have a bus (POP account) and a car (IMAP account). If I log onto the POP account, that's taking the bus to the bank (my email messages).

If Thunderbird allows multiple accounts, I don't see why in principle it wouldn't allow POP and IMAP accounts to the same gmail account. This assumes that the offline messages would be stored in different locations.

Of course, it's all theoretical since I'm afraid of things going fubar if I actually tested my idea!

> **pfeiffep said:**
> Might I suggest that you create a** test email account **at gmail and experiment with possibilities:popcorn:

That's a great suggestion. I will try that soon.

---

### Post by parminides on 2013-03-20
Just now I was looking at the settings for the POP account I created and saw something that really worried me. In the Server Settings, it had both options checked for "Leave messages on server," i.e., 1) "For at most 14 days" and 2) "Until I delete them."

One problem is that those options are inconsistent! Maybe (hopefully) "Until I delete them" trumps "For at most 14 days." But my guess is that it means that any messages I don't delete manually will be deleted automatically after 14 days.

Of course I can just deselect these options, but this is just the thing that really scares me and makes me wonder if that's how so many people lost their email.

I had selected in the Gmail settings to "keep Gmail's copy in the Inbox." I thought I was safe. Was Thunderbird really scheduled, by default, to delete *all* my messages from the Gmail server after 14 days, without my knowledge, just because I hadn't noticed those settings? That's scary.

Have I mentioned that I can't afford to lose the messages on the Gmail server?

---

### Post by Slim Odds on 2013-03-20
> **parminides said:**
> Thanks for all the replies. Sorry about my initial grumpiness, but I can't afford to lose all my messages on Gmail.



The email is physically on my computer now with the POP account. All the messages are in a huge file called  ~/.thunderbird/hreipadj.default/Mail/pop.googlemail.com/Inbox. I know they're there because I opened it in a text editor and looked.



This trick worked for me and more or less fixes my original problem. However, it would be nice if I could have complete but independent backups on my laptop and desktop. I will experiment with IMAP, which is what almost everyone recommends. So I won't mark the thread solved yet. 

Can I create separate IMAP and POP accounts in Thunderbird for the same Gmail account?

Thanks for all the help. As far as I know I haven't lost any messages yet.
Yes, you can do both. IMAP is definitely the modern one, POP is old.

Another advantage of IMAP is that it allows you to manage your mailbox from any of the computers and basically sync them. As an example, if you really do want to delete a email from your account, IMAP will allow that decision to propagate to each client in a very natural way (i.e., the deleted item will be removed from each client automatically when you sync). Whereas with POP, you would have to delete that same email from each client yourself. Things can get pretty disorderly that way. IMAP keeps it clean.

---

### Post by pfeiffep on 2013-03-20
> [COLOR=#000000]It seems to me that Thunderbird is the garage. The garage can have a bus (POP account) and a car (IMAP account). If I log onto the POP account, that's taking the bus to the bank (my email messages).[/COLOR]

My analogy breaks down ... the garage for a car has entirely different specifications than does one for a bus ... more significantly if the bus is already parked in the garage there's no room for the car.
 
The Synchronization and Storage page in account settings enable keeping all messages on a local PC while also keeping messages on the gmail server.
The advanced button provide fine grained control for folders to be available 'off line'
This seems like it would be a HUGE advantage to you since can't afford to loose any email ... it a 'real time back-up' of your email. If you choose to install Thunderbird on a second PC you would have 3 identical email containers. 

If you'd like we can take this off line in private messaging and I'll walk you through the steps

---

