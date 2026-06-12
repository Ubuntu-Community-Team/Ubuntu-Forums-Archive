---
title: "Evolution; Import - File type broken"
date: 2007-07-02
forum: General Help
---

### Post by tak1150 on 2007-07-02
I'm trying to migrate to Evolution from T-bird due to SCIM incompatibilities.

In Evolution, when I go

File --> Import

I get to the window where they are asking for the e-mail file to be imported and the file type.
(see attachment)

This still happens when I have a proper file selected as well.

Thanks!

---

### Post by tak1150 on 2007-07-05
Bump - 

Help! :sad:

---

### Post by michaelwigle on 2007-07-19
I don't have a solution but I am hoping to move my wife from Outlook to Evolution and ran into the exact same problem with the file type being greyed out and therefore you can't go to the next step. I too would greatly appreciate if anyone knows how to file a bug report or can help with this problem.

---

### Post by tak1150 on 2007-08-24
Anybody?

---

### Post by tak1150 on 2007-10-19
I tried this with the Evolution that was shipped with Gutsy and still the same problem.... Anybody?

---

### Post by Psychobudgie on 2007-11-04
BUMP

Same here, cannot import mailbox's as the filetype is greyed out.
Any sort of help would be appreciated. Using Gutsy here.

---

### Post by tak1150 on 2007-11-17
Thank you, michaelwigle and Psychobudgie!

I am not alone and I know I'm not dreaming! There must be somebody smart out there that had the same problem and fixed it! If you are that person, please post :)

Tak

---

### Post by FokkerCharlie on 2007-11-27
Hi

I have just run into the same problem.

Any solutions yet?

Charlie

---

### Post by tak1150 on 2007-11-27
> **FokkerCharlie said:**
> Hi

I have just run into the same problem.

Any solutions yet?

Charlie

It's bizarre. Nobody seems to be talking about this. I know it's not my fault b/c this happened with fresh installs of both Feisty and Gutsy. :(

---

### Post by FokkerCharlie on 2007-11-27
Hello, again!

I've found a workaround- happily, Thunderbird and Evolution both use the same format for storing mailboxes, so with a bit of rummaging, the process isn't too hard.

First, find your Thunderbird data, mine was in:
/media/disk/Documents and Settings/<user name>/Application Data/Thunderbird/Profiles/whdejusy.default/Mail
That's on a Windows XP partition, hopefully it's enough of a clue if that's not what you want to import from!

In that location I found a number of sub-folders, each of which contained files, named corresponding to folders I have in Thunderbird, eg 'Inbox', 'Sent' etc.  I found quite a few with a size of 0 bytes, which were obviously empty- so no need to copy them.

Make a renamed copy of these files, eg to 'InboxThunder', and copy them to your Evolution file location:

/home/<user name>/.evolution/mail/local
To see this folder, you'll have to select View>Show Hidden Files in the File browser.

Then open Evolution.  You'll see folders names 'InboxThunder' etc right there, with emails waiting snugly inside!

I hope that this is helpful to you.
Charlie

---

### Post by michaelwigle on 2007-12-13
Thanks for the update FokkerCharlie. That's a good solution for going between TB and Evo. Sadly, I'm trying to go from Outlook to Evo and Outlook uses a different file format. Although I think I've found a work around but it will take some doing. My wife is currently set to use POP and I'm going to create an IMAP connection and then move all her current local folders into the IMAP connection so all her mail is on the server. Then it won't matter what client she uses.

All the same, it sure would be nice to know why the option is there if it's going to stay greyed out and unavailable...

---

### Post by beckfield on 2008-01-06
> **FokkerCharlie said:**
> Hello, again!

I've found a workaround- happily, Thunderbird and Evolution both use the same format for storing mailboxes, so with a bit of rummaging, the process isn't too hard.

Charlie

Hi Charlie,
I'm having this problem as well.  Unfortunately, your workaround isn't working for me.  The InboxTBird folder appears in Evolution, but there's nothing in it.

Ken

---

### Post by FokkerCharlie on 2008-01-07
Hi Ken

Sorry this isn't going well for you!  Have you had a look around for any other *.mbox files that T-bird might have been using?  This could be the case if, for example, you had sub-folders in you inbox (as I do).  Keep your eye out for any large files in particular.

Can you tell us the size of the InboxTBird file that you copied across?

I have to admit, that I am close to the limit of my usefulness here, I'm not an expert!

Charlie

---

### Post by dominics on 2008-04-14
I was having some problems at first, while trynig to import mail folders into evolution from Thunderbird, until I realised I was looking at the wrong folders. 

It can be a little confusing, because Tbird creates so many folders. All you need to do is locate the folder named outlook mail.sbd, and open it, you then need to look for the folder named personal folders.sbd and then open it, you will find 2 of each file. attempt to open the one that doesnt have an extension at the end of the file name. 

You will then find yourself back at the original file type selection box and you will find the forward button is now active.

Hope this helps

Dom

---

### Post by btolle on 2008-04-22
> **tak1150 said:**
> I'm trying to migrate to Evolution from T-bird due to SCIM incompatibilities.

In Evolution, when I go

File --> Import

I get to the window where they are asking for the e-mail file to be imported and the file type.
(see attachment)

This still happens when I have a proper file selected as well.

Thanks!

You have to select a mailbox file to import from your Thunderbird files before the file type area will be functional.

I don't know if this will work with Outlook since Outlook uses a proprietary email file format.

---

### Post by btolle on 2008-04-22
> **tak1150 said:**
> I'm trying to migrate to Evolution from T-bird due to SCIM incompatibilities.

In Evolution, when I go

File --> Import

I get to the window where they are asking for the e-mail file to be imported and the file type.
(see attachment)

This still happens when I have a proper file selected as well.

Thanks!

You have to select a mailbox file that does not have an extensin to import from your Thunderbird files before the file type area will be functional. It must be a file, it cannot be a folder.

I don't know if this will work with Outlook since Outlook uses a proprietary email file format.

I had a slew of mailboxes and thousands of emails so I made a copy of my T'bird file folder and saved it to the Linux desktop and deleted any file that had an extension as well as any description files.

I individually imported the files such as inbox, sent, drafts, and any other system type mailboxes.

I copied the remainder of the files into my Evolution directory (a hidden directory).

Opened Evolution and all mails were there but they were all marked as "Unread".

Right clicked on each folder and selected "Mark all files as read" and "on current folder and subfolders". That marks all messages at once in that folder.

---

### Post by nagrover on 2008-04-23
hmmm, none of these solutions are working for me when trying to bring over Thunderbird email to Evolution.

For starters, even when trying to import from Evolution and after selecting the correct file from Thunderbird (~/.mozilla-thunderbird/gntl52dy.default/Mail/Local Folders/BCI), the file types dialog is still grayed out. I've tried just about every single file without an extension within my Thunderbird directory (all profile folders) and it is always the same.

Secondly, after reading about the "backdoor" way to import from thuderbird (command line move mbox from Thunderbird to Evolution) I've realized that Evolution does not have any folders within ~/.evolution/mail/local. It seems as though Evolution has changed the mail structure? For example, within the Evolution folder I see the following files (no folders) for the local Inbox:
Inbox, Inbox.cmeta, Inbox.ev-summary, Inbox.ev-summary-meta, Inbox.ibex.index, Inbox.ibex.index.data. If I create a folder within ~/.evolution/mail/local it does show up in Evolution but any attempt to use the folder results in an error message.

For the record I'm on Ubuntu 8.04 and using Thunderbird 2.0.0.12 and Evolution 2.22.1

Any help would be appreciated. I have a feeling I might have to wait for Evolution to fix this?

---

### Post by testdasi on 2008-07-12
Look inside the folder *.sbd and make sure you view in list mode so that you can see the file size. I had the problem at first but when I turned on list mode, I saw that those files I was trying to import was zero size. The actual data is in side the *.sbd folder.

---

