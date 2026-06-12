---
title: "Need Evolution Help with Exchange Server"
date: 2007-01-24
forum: General Help
---

### Post by SuperMike on 2007-01-24
After waiting way, way too long for this, my office finally switched me over to a newer MS Exchange Server and the OWA appears compatible with my Evolution. I got Evolution to download and send mail okay tonight with wild surprise. However, I need a bit of help still:

1. I see "On This Computer" and "<name withheld in this forum>@<company name withheld>.com". The latter is pointing to my mailbox on the mail server. How do I just have one inbox and everything goes into that?


2. With this Exchange connection, how do I have my mail automatically download from the mail server and stay down on my workstation, not kept on the mail server?


P.S. If I can get this working, then I am finally free of having to use my Windows workstation at my day job.

P.P.S. The animated smilies in this forum are ugly and annoying. Are they trying to encourage people to call Ubuntu Live Support instead? :)

---

### Post by SuperMike on 2007-01-24
I also tried the following options and can't seem to get them to work?

Can't download mail from server and keep it off server.

Can't add a rule to move mail off server into "On This Computer" folder.

---

### Post by SuperMike on 2007-01-25
Both problems are resolved.

First, you have to rightclick the folders "Personal Folders" and "Inbox" and choose Properties and "Copy folder content locally for offline operation".

Second, you have to choose Edit, Preferences, Mail Accounts, click on your server mail, Edit, Receiving Options, and check off "Automatically check new mail", then "Automatically synchronize account locally", then "Apply filters to new messages in inbox on this server". They all must be checked to on position, not off.

Third, go to Edit, Message Filters, and choose "Incoming", click Add, type "Move Mail", Set it so that "Match All", "If any criteria are met", and "move to folder" are chosen and choose the local folder (not the server folder) on your computer. (Mine says "On This Computer", Inbox.)

When you do all this, your mail will automatically download and get forwarded properly to the local offline inbox. As well, your mail will be deleted properly from the mail server.

At that point, you can add your own rules on the local inbox so that you can do all kinds of necessary things.

---

### Post by SuperMike on 2007-01-25
Some extra notes about this resolved item:

* My Move All mail rule needed to be moved to lowest priority because I had other mail rules that needed to take place before this. Otherwise, the Move All mail rule sticks everything in my inbox without processing further rules.

* "On This Computer" wants to put folders under "Inbox". I didn't like that and I like them under "On This Computer". So, I had to drag and drop them there. But then they sorted in with the other items by alphabetical order. Therefore, I had to rename all the folders with "0_" + name so that they sort directly under the Inbox item in the list, grouped together.

* Trash gets a copy of everything moved by the rule. Don't know why that is. Not a huge deal, but one should note they need to Empty Trash routinely.

* The help file in Evolution talked about how to migrate my Outlook mail to it. However, that completely backfired. I downloaded SeaMonkey as well as Thunderbird and tried both. When I get to the point of clicking Import on Windows to import these PST files, the wizard simply locks up on me and goes no further, even after waiting a few hours. I also tried uninstalling both, finding all their residue folders and deleting them, and reinstalling SeaMonkey again and testing. That didn't seem to help. See, the SeaMonkey technique was going to convert the PST into a single mailbox file that I could then re-import into Evolution. So I just gave up and realized that if someone wants me to show them my old mail or find something for them, I'm going to have to go back to my Windows box to find it. And the most critical messages -- I cut and pasted the text from those into text files on Linux and saved them in a folder on my desktop. Oh well. At least all new messages will be okay.

P.S. Oh, and I hate this smilie --> :guitar: I hope the thread editor only shows it in the future when I click More. That's my vote, at least.

---

### Post by SuperMike on 2007-01-25
I noticed a problem with Tasks and with shutting down the app. Occasionally when I shut down Evolution it won't shut down completely. I had to do:

pstree -p | grep -i evolution

and then use 'kill' to kill each pid. Otherwise, when you try to open Evolution, it will not do anything.

Another issue I found was that when this occurs, any new tasks you have added will not have been saved and will be gone FOREVER. I was thinking that when you entered a task it would be saved in real time, but no, it appears it's saved only on a successful shutdown of the app.

Therefore, I don't recommend using "Tasks". It's broke at least in version 2.6.1.

---

### Post by SuperMike on 2007-01-26
More notes:

* If you're wanting a rule that receives a message on a certain subject or sender and then forwards a copy of the email to someone else, that feature doesn't exist. Huge oversight!

* I often have a need to connect from VPN and check my messages. Unfortunately, the Linux route to do this is much slower than the Windows route. With Windows, I just did an rdesktop over VPN from my Ubuntu at home, connected to a Windows workstation, and downloaded messages. On the new Evolution system, however, I have to VPN from Ubuntu and use this technique to get into my Evolution:

1. ssh -X -U <user you use at office> <ip address of Ubuntu workstation at office>

2. Once in, do 'pstree -pah | grep -i evolution' and see those pid's? Good, use the 'kill' statement to kill those pids. You can't have more than one evolution open at the same time.

3. Now type 'evolution' and you'll get a Kerberos error but Evolution will load up. You can at least see your current inbox, but you won't be able to send/receive messages because of the Kerberos error. I wish that weren't the case, but oh well. If you want to send/receive messages, connect to your office's OWA account with your web browser.

So, as you can see, it sort of works, but is much slower than the rdesktop connection to a Windows workstation and it won't let you send/receive messages. I'd love to see this changed in a future Evolution, but oh well.

In fact, I'd love to see someone build a gateway in Perl or something where I can use my Thunderbird to connect on POP3/SMTP to it and it translates these requests into OWA commands much like Evolution does with its Exchange Connector plugin.

---

### Post by traneHead on 2007-01-29
Thanks for the thoughts, tips and tricks!

---

### Post by SuperMike on 2007-01-29
Unfortunately, in the end, I had to bail on the concept of using Evolution for these 3 reasons:

* For some strange reason when I clicked in my calendar, it would lock up Evolution.

* My calendar started showing double appointments. When I deleted one of the duplicates, it would delete both and send a notice back to people that I didn't want to be in their meeting, which was not what I expected.

* It was incredibly broken and slow over VPN. Sure, I could read mail, but not send or receive any new mail.

However, if Evolution fixes these things, I would definitely switch to it. For now, I'm going to have to continue to use rdesktop to Windows XP with Outlook. Darn it.

---

### Post by rhardie on 2007-04-23
Thanks, Super Mike.  My Exchange Server and Evolution work very well together on first try.

---

### Post by SuperMike on 2007-04-23
> **rhardie said:**
> Thanks, Super Mike.  My Exchange Server and Evolution work very well together on first try.

Using Dapper? I'm using Dapper because I stick with LTS versions as I'm a conservative individual when it comes to Linux. Perhaps you're using something later than that?

What about the other issues I expressed in this thread? Did you try those things?

Sure, I could get connected, and could download and send mail, but as you can see in the thread that the rest of the items were enough to make me quit using it. I would love to keep using it, but unfortunately it presented too many problems. I would be curious to see if these problems exist for you as well, so please go back through this thread and try some of the things I had mentioned if you get a chance.

---

### Post by aitorcalero on 2007-08-31
Thank you Mike, your tips finally made my Evolution to work properly with my Work Exchange Mail Server.

---

