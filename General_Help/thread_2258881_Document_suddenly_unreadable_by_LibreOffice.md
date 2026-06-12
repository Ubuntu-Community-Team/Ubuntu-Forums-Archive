---
title: "Document suddenly unreadable by LibreOffice"
date: 2014-12-31
forum: General Help
---

### Post by rdh61 on 2014-12-31
I have a quite large document (90 pages) which I was working on with LibreOffice Writer. I have been saving it in the .doc format. (I have since learned that that is not wise, but it always worked all right before). The last edit was on 24th December. When I tried to open it yesterday, I got 700 odd pages of # and ? signs with large spaces in between. In "properties" it says the document is an "OLE2 compound document", whereas I had always assumed it was a "Word document", as it was when I first saved it in the .doc format. Nevertheless, even if I try to open it in Windows with Microsoft Word, I can't. The really odd thing is that I have access to older .doc versions of the document (stored on Google Drive), which I previously opened and edited normally in LibreWord. But now they cannot be opened either (same corrupted text)! I find that mystifying. Please help. Many thanks.

---

### Post by bapoumba on 2014-12-31
Would you happen to have a local copy ? I have found that sometimes office docs (mainly presentations here, using Impress or spreadsheets using Calc) can get funky when stored on dropbox or ggogle drive.

Can you download a previous file and open it locally ?

---

### Post by rdh61 on 2014-12-31
I have a local file and I can also download and open previous edited versions. All appear as gobbledegook.

---

### Post by bapoumba on 2014-12-31
Ah.. Is there anything confidential in them ? You could either attach them here or email one to me (my nick at ubuntu dot com).

---

### Post by ajgreeny on 2014-12-31
Do you have LO set up to save a backup copy in the libreoffice backup folder which should be at **~/.config/libreoffice/4/user/backup/**

I have found it to be very useful once or twice when I have stupidly saved a copy of something I have just edited but also find I needed the original.

Can you open another .doc file that you know has worked fine in the past, or produce a new one yourself, then save it and open it again, to see if that works OK, or is it all .doc files that are now corrupt?

What about installing **abiword** yourself and trying that, to see if this is just a LO problem that you have, or sending the file to a friend (bapoumba as he suggests?)[SIZE=2] [/SIZE]to open for the same reason

---

### Post by vasa1 on 2014-12-31
> **bapoumba said:**
>  ... I have found that sometimes office docs (mainly presentations here, using Impress or spreadsheets using Calc) can get funky when stored on dropbox or ggogle drive.
...
That's scary. I store Calc spreadsheets (stored in LibreOffice's native format) on both Dropbox and Google Drive but have not yet encountered problems the few times I've downloaded and used them.

---

### Post by bapoumba on 2014-12-31
> **vasa1 said:**
> That's scary. I store Calc spreadsheets (stored in LibreOffice's native format) on both Dropbox and Google Drive but have not yet encountered problems the few times I've downloaded and used them.
Yep, scary. I got hit one day with a non-important file. All the very important ones, the ones I'd cry if I'd loose, I have local copies, sometimes several local copies. I use the clouds to share office files with colleagues at work or my own kids who study away from home, quite convenient (and yes, native LO format).

To be precise, it happened on several occasions while editing the files I had directly opened from the Dropbox folder. If I copy locally, open and work on, save, then copy the new version to Dropbox, I have no problem.

---

### Post by Holger_Gehrke on 2014-12-31
It might actually not be the file which is messed up but your  LO-configuration, specifically the import filters. Set up a new user, log in as that user and try to open the file.

---

### Post by ajgreeny on 2014-12-31
> **Holger_Gehrke said:**
> It might actually not be the file which is messed up but your  LO-configuration, specifically the import filters. Set up a new user, log in as that user and try to open the file.
My point exactly, hence my suggestion of trying to open the file or files with abiword or send them elsewhere for someone else to open.

Frightening, though, that all ones documents could be corrupted by something as commonly used as dropbox or google-drive, neither of which I use, but can see many reasons why I might at some time in the future.

---

### Post by rdh61 on 2015-01-01
Thanks for all the replies. I eventually realised that I was not following the correct procedure to revert to previous versions of the document on google drive. I have now managed to download a pretty recent uncorrupted version, which I'm happy with. I have saved it locally in several different places, as well as on google drive and dropbox! I do not believe it was google drive which corrupted the document. I believe the culprit was LO, in particular my having saved the document in non-native .doc format.

---

### Post by ajgreeny on 2015-01-01
I seldom use the .doc or .docx filetypes in LO and certainly don't save things that way unless I have to send them as an attachment to someone else.  However my wife who still needs to send documents to others has been saving LO files as xls and doc types as default for the last 5 or 6 years without any problems or difficulties of any kind, so I do not believe your final comment in post #10 is the cause.

Nevertheless, I am happy you got your files back without too much of a major problem.

---

### Post by whitesmith on 2015-01-01
This is a powerful argument for (1) using something like BackInTime to keep $HOME properly backed up (I do incremental backups of everything there hourly); and (2) **never** save in other than the native format of an application unless you find endless aggravation entertaining. Best regards.

---

### Post by Gordonbp531 on 2015-01-02
Then you should post a question on the LO mailing list [here]("http://www.libreoffice.org/get-help/community-support/") or the Nabble User forums [here]("http://www.libreoffice.org/get-help/nabble/") to see if anyone else has experienced this and if there's a bug filed.
FYI, LO although installed with Ubuntu, it's nothing to do with Canonical - if you have any questions about LO in the future then the users mailing list is the place to go.

I don't use GoogleDocs or Dropbox - I use [Owncloud]("http://owncloud.org/") (which is an open-source cloud solution) and haven't to date seen any problems like this, mainly I suspect because OwnCloud syncs my local folders from their original location, not from a special drive folder...

---

### Post by rdh61 on 2015-01-08
> I seldom use the .doc or .docx filetypes in LO and certainly don't save  things that way unless I have to send them as an attachment to someone  else.  However my wife who still needs to send documents to others has  been saving LO files as xls and doc types as default for the last 5 or 6  years without any problems or difficulties of any kind, so I do not  believe your final comment in post #10 is the cause.

Nevertheless, I am happy you got your files back without too much of a major problem.

Thanks. The file I was editing was the local one, not the cloud one, so sync was from local to cloud. My local file was corrupted as well, that is why I suspect LO.

---

### Post by rdh61 on 2015-01-08
> Then you should post a question on the LO mailing list [here]("http://www.libreoffice.org/get-help/community-support/") or the Nabble User forums [here]("http://www.libreoffice.org/get-help/nabble/") to see if anyone else has experienced this and if there's a bug filed.
FYI, LO although installed with Ubuntu, it's nothing to do with  Canonical - if you have any questions about LO in the future then the  users mailing list is the place to go.

I don't use GoogleDocs or Dropbox - I use [Owncloud]("http://owncloud.org/")  (which is an open-source cloud solution) and haven't to date seen any  problems like this, mainly I suspect because OwnCloud syncs my local  folders from their original location, not from a special drive folder...

Yes, I posted to the LO mailing list, too. I got many more useful replies here in much less time than I got from there, so if I have a problem with LO in future I'll post to wherever I think I'll find helpful and knowledgeable people, including here. Thanks for the info.

---

