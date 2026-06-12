---
title: "from Windows to Ubuntu"
date: 2006-10-27
forum: General Help
---

### Post by Bo Rosén on 2006-10-27
Friends!
A friend of mine has at long last started to make serious noises about moving from windows to linux. He has some questions, probably the same most people have. Can he move his Firefox bookmarks from XP to Ubuntu, can he move his Thunderbird mail (and settings perhaps) to well, thunderbird?
I tried searching the forums, but probably used bad search terms as I didn't come up with anything very useful. Can someone point me inte right direction?

Thanks

---

### Post by dbott67 on 2006-10-27
> **Bo Rosén said:**
>  Can he move his Firefox bookmarks from XP to Ubuntu
Yes, just open the **BOOKMARKS** menu, click **MANAGE BOOKMARKS** and then select **FILE > EXPORT**.

This will create a 'bookmarks.html' file that can be copied to CD, floppy, USB, e-mailed... and then IMPORTED on the new system.  On the new system, open the **BOOKMARKS** menu, click **MANAGE BOOKMARKS** and then select **FILE > IMPORT** > **FROM FILE** and then browse to your 'bookmarks.html file.

> **Bo Rosén said:**
> can he move his Thunderbird mail (and settings perhaps) to well, thunderbird?

From [http://www.mozilla.org/support/thunderbird/faq#export](http://www.mozilla.org/support/thunderbird/faq#export)

    > Thunderbird's mail files are in the standard plain text "mbox" format, which almost all mail programs can use or import. Many proprietary mail programs have a function to import from Eudora, which also uses the "mbox" format; this function should read your Mozilla mail files properly.

    Your mail files are inside your profile (see the Profile Folder), in the Mail and (if you use IMAP) ImapMail folders. Each mail folder (Inbox, Sent, etc.) is stored as two files &#8212; one with no extension (e.g. INBOX), which is the mail file itself (in "mbox" format), and one with an .msf extension (e.g. INBOX.msf), which is the index (Mail Summary File) to the mail file. Tell the other program to import mail from the file with no extension.

    If you want to transfer a mail file to another Mozilla profile or another installation of Mozilla, simply put the mail file into the other installation's Mail folder.

-Dave

---

### Post by Bo Rosén on 2006-10-27
Oh. As simple as that :-)
Thank you!

---

