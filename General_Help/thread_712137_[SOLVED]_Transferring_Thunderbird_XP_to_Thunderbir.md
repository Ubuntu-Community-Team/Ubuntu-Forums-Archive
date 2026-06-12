---
title: "[SOLVED] Transferring Thunderbird XP to Thunderbird Ubuntu"
date: 2008-03-01
forum: General Help
---

### Post by iheartubuntu on 2008-03-01
Ive checked the various threads related to this... Ive got a bunch of mail in Thunderbird XP id like to view in Ubuntu here. Seems the easiest way to do this is to share the XP folder.  But, Where do I select this option in Thunderbird on my Ubuntu? I cant quite figure it out. Thanks!

Here are a couple threads that sounded useful, but I still dont understand how I link my XP directory up with the Thunderbird on Ubuntu.

[http://ubuntuforums.org/showthread.php?t=603639](http://ubuntuforums.org/showthread.php?t=603639)

[http://ubuntuforums.org/showthread.php?t=446368](http://ubuntuforums.org/showthread.php?t=446368)

---

### Post by alenis on 2008-03-01
You have to mount th eshared folder somewhere in your file system (e.g. /media/mail), then use 

sudo thunderbird -profilemanager

and create a new profile, choosing the shared folder as storage for mail, setting, etc.

---

### Post by gobbles414 on 2008-03-01
shirteesdotnet,

You may be making this too difficult for yourself. Does your email account allow [IMAP]("http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol") instead of [POP]("http://en.wikipedia.org/wiki/Post_Office_Protocol")? Using IMAP, you can access all of your emails from any computer's email manager. For example, I'm using IMAP to access my Gmail accounts in Ubuntu's Evolution and Vista's Windows Mail. And of course, I can still access my emails via the Gmail website. Obviously, you'll need transfer your address book contacts manually. Does this help?

---

### Post by iheartubuntu on 2008-03-01
> **gobbles414 said:**
> shirteesdotnet,

You may be making this too difficult for yourself. Does your email account allow [IMAP]("http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol") instead of [POP]("http://en.wikipedia.org/wiki/Post_Office_Protocol")? Using IMAP, you can access all of your emails from any computer's email manager. For example, I'm using IMAP to access my Gmail accounts in Ubuntu's Evolution and Vista's Windows Mail. And of course, I can still access my emails via the Gmail website. Obviously, you'll need transfer your address book contacts manually. Does this help?

Hey, Yah, I have IMAP for gmail enabled and working, but I have a bunch of old mail folders in XP that I could NOT transfer to my IMAP account, so I want to get it working here and see if I can transfer my mail to IMAP account in Ubuntu's Thunderbird. Even still, Id like everything over here in Ubuntu now. Its all part of the weening myself off of MicroShaft.

---

### Post by iheartubuntu on 2008-03-01
> **alenis said:**
> You have to mount th eshared folder somewhere in your file system (e.g. /media/mail), then use 

sudo thunderbird -profilemanager

and create a new profile, choosing the shared folder as storage for mail, setting, etc.

Thanks. This sounds helpful. I now how to figure out how to mount my shared directory so it is seeable in Thunderbird profiles.

---

### Post by alenis on 2008-03-01
Install samba, if not already present in your system, and type 

mount -t smbfs //servername/sharename   /mountdirectory -o username=mywindowsusername, password=mywindowspassword

to make the mount permanent you have to edit fstab adding a line similar to the following

//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0

Don't change anything else in fstab!

---

### Post by gobbles414 on 2008-03-01
> **shirteesdotnet said:**
> Hey, Yah, I have IMAP for gmail enabled and working, but I have a bunch of old mail folders in XP that I could NOT transfer to my IMAP account, so I want to get it working here and see if I can transfer my mail to IMAP account in Ubuntu's Thunderbird. Even still, Id like everything over here in Ubuntu now. Its all part of the weening myself off of MicroShaft.

Hmm... What folders won't it transfer? In Thunderbird, have you tried dragging these folders into the Gmail folder structure? Is Thunderbird configured properly? You seem like a smart person. But just in case you didn't know about it, there's an official Gmail help document for configuring IMAP in Thunderbird. Click [here]("http://mail.google.com/support/bin/answer.py?answer=77662&topic=12814"). Instead of a shared Windows folder, you could just backup your emails to a CD-R or USB flash drive and then import them into Thunderbird in Ubuntu. Then -- if all goes well -- Ubuntu's Thunderbird with upload all of the folders to Gmail, and you can download those folders into Windows' Thunderbird.

---

### Post by iheartubuntu on 2008-03-01
> Hmm... What folders won't it transfer? In Thunderbird, have you tried dragging these folders into the Gmail folder structure? Is Thunderbird configured properly? You seem like a smart person. But just in case you didn't know about it, there's an official Gmail help document for configuring IMAP in Thunderbird. Click [here]("http://mail.google.com/support/bin/answer.py?answer=77662&topic=12814").

Yup. I tried this which would be the easiest way. For some reason my Thunderbird on XP has a bug and wont allow me to drag and drop the folders into my IMAP account. The Thunderbird forums didnt offer a work around either.
> 
Instead of a shared Windows folder, you could just backup your emails to a CD-R or USB flash drive and then import them into Thunderbird in Ubuntu. Then -- if all goes well -- Ubuntu's Thunderbird with upload all of the folders to Gmail, and you can download those folders into Windows' Thunderbird.

I did back up my info and have a folder on my desktop here in Ubuntu but what I understand is Thunderbird XP mail folders arent compatible with Thunderbird linux folders. Id love to do this, how do I import my folders?

---

### Post by iheartubuntu on 2008-03-01
My ultimate goal here is to get those folders from XP into Ubuntu's Thunderbird, then attempt to drag and drop the folders into my IMAP account, which I cant do in XPs Thunderbird because of the bug.

Can I export my folders, accounts, or emails in XP then import them here? I'll even use Evolution. Doesnt matter.

---

### Post by gobbles414 on 2008-03-01
shirteesdotnet,

> Yup. I tried this which would be the easiest way. For some reason my Thunderbird on XP has a bug and wont allow me to drag and drop the folders into my IMAP account. The Thunderbird forums didnt offer a work around either.

Have you tried creating new folders in the Gmail folder structure, and then dragging the messages themselves into those new folders?

> I did back up my info and have a folder on my desktop here in Ubuntu but what I understand is Thunderbird XP mail folders aren't compatible with Thunderbird Linux folders. I'd love to do this, how do I import my folders?

I could be wrong, but I believe that the two Thunderbirds are comaptible with one another. According to [this]("http://www.mozilla.org/support/thunderbird/faq#export") from the Thunderbird support FAQ's:
[I]
**How do I export e-mail messages to another mail program or computer?**

Thunderbird's mail files are in the standard plain text "mbox" format, which almost all mail programs can use or import. Many proprietary mail programs have a function to import from Eudora, which also uses the "mbox" format; this function should read your Mozilla mail files properly.

Your mail files are inside your profile (see the [Profile Folder]("http://www.mozilla.org/support/thunderbird/profile")), in the Mail and (if you use IMAP) ImapMail folders. Each mail folder (Inbox, Sent, etc.) is stored as two files — one with no extension (e.g. INBOX), which is the mail file itself (in "mbox" format), and one with an .msf extension (e.g. INBOX.msf), which is the index (Mail Summary File) to the mail file. Tell the other program to import mail from the file with no extension.

If you want to transfer a mail file to another Mozilla profile or another installation of Mozilla, simply put the mail file into the other installation's Mail folder.[/I]

Maybe you can use the export tool in Windows' Thunderbird and the import tool in Ubuntu's Thunderbird to achieve similar results. And I believe that Evolution can also import emails from Windows' Thunderbird as well.

---

### Post by iheartubuntu on 2008-03-01
Thanks for everyone troubles here. I went into XP, and Thunderbird there had an update. I did that and now dragging and dropping my folders into my gmail IMAP works great!

And I set up an account in Evolution and actually like it better than Thunderbird.

---

### Post by gobbles414 on 2008-03-01
> **shirteesdotnet said:**
> Thanks for everyone's troubles here. I went into XP, and Thunderbird there had an update. I did that and now dragging and dropping my folders into my Gmail IMAP works great!

And I set up an account in Evolution and actually like it better than Thunderbird.

That's great news! Things to be aware of regarding Evolution: The user interface takes some time to learn. I haven't discovered a way to sort my address book entires alphabetically by last name as I compose a new email -- the address book itself sorts by last name very easily. Conveniently, Ubuntu's Software Update tool will automatically download updates for your Evolution software. And of course, Evolution has a calendaring feature whereas Thunderbird doesn't.

Remember to always keep your software and operating systems up-to-date. While that's especially important in the Windows world, it's worth remembering as you use Linux too.

PS: Remember to mark your question as "solved" so that others can find this thread as they browse the forums.

---

