---
title: "Migration to Thunderbird from evolution in UB13.10 - Help Required."
date: 2013-11-17
forum: General Help
---

### Post by pkane2 on 2013-11-17
Hi All,
This is my first post here, so please be gentle.
I am a relative novice to linux, and have for many years been using the Outlook mail client on windows.
I migrated by Outlook folders etc, to evolution and have been testing evolution (3.8.4) for about 6 months and have found that evolution may not meet my needs. 
I have installed Thuderbird (24.1.0) and want to give that a test to see if that better suits my needs.

My issues are this.
I have Mail folders ( nested) on my local drive. It appears that these are no longer in the mbox format and are now in maildir format. I wish to transfer these folders over to Thuderbirds local folders.

I have looked and followed a few different methods below of doing this but none have worked for me.
[LIST=1]
[*]Copy folder to imap account. ( Evolution crashes on drag and drop, or is unable to find the folder in imap when using the copy to folder command) 
[*]Using the maildir2mbox script. ( Script runs in terminal and I can see the emails being read, but there is not an output mbox file created. The prompt after it finishes the script auto fills with maildir2mbox 62;9;c) 
[*]Using the python script md2mb.py ( Just creates and mbox file but with nothing in it.) 
[/LIST]

So any help and pointers here would be greatly appreciated.
Thanks.

Paul.

---

### Post by Y^2om&amp;#7sgP on 2013-11-19
Hi there

If you select all emails in any folder then right-click, you will have the option to save as mbox.

The bad news is that you have to do this for each folder individually :(

---

### Post by plucky on 2013-11-19
See 

[Switching from Evolution to Thunderbird](https://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=migrating%20from%20evolution%20to%20thunderbird&as=s)

Good Luck

---

### Post by Y^2om&amp;#7sgP on 2013-11-19
@plucky

I'm missing something.  I checked the url and it doesn't mention Evolution....except in the url itself :(

---

### Post by howefield on 2013-11-19
> **hattpa said:**
> I checked the url and it doesn't mention Evolution....except in the url itself :(

Point 4...

[4 Switching from Evolution to Thunderbird]("https://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=migrating%20from%20evolution%20to%20thunderbird&as=s")

---

### Post by Y^2om&amp;#7sgP on 2013-11-19
> **howefield said:**
> Point 4...

[4 Switching from Evolution to Thunderbird]("https://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=migrating%20from%20evolution%20to%20thunderbird&as=s")

Oops, sorry,. looks like I've an issue seeing that at work.  It flashes up, but then collapses and I couldn't see the various points only those relating to Outlook :(

Have managed to get there by refreshing and then cancelling before it fully loads the page....

Only thing would be that Evolution no longer uses mbox it has to be manually saved as such.

---

### Post by pkane2 on 2013-11-19
Guys,
Thanks for the responses, and apologies for not following up sooner.

I have read the article, and many like it, and have not found them to work, automatically.
As I mentioned in the OP , various tools do not work for me to convert  evolution nested mail folders and structure direct into to thunderbird.
I  would love know if anyone has successfully done this with the current  versions of ubuntu,evolution, and thunderbird. Most of the information I  have seen, and tried is with older versions of this software in mind.
Hattpa
I know that you can copy the mail contents of a folder to mbox then import that into thunderbird (TB), but you have to create the nested table structure into TB then import the individual mbox into that folder. Like you mentioned,with  multi-level nested folders this would be both time consuming and very tedious. I was hoping to have this process automated. 

plucky
The link states, 
[h=2]"Importing Evolution Messages[/h] Thunderbird and Evolution use the **_same_** file format (called mbox) to  store your mails, so its not difficult to import them manually. "

This statement is outdated as evolution does not use mbox anymore.



So the search for a solution goes on.

---

### Post by pkane2 on 2013-11-19
Would this work?
Does anyone know, if I backed up evolution, then uninstall current version of evolution which uses maildir format. Then install an earlier version of evolution which is of mbox format. Will the earlier version of evolution be able to read the maildir format backup.
If so would it then back able to be exported in mbox format as per the thunderbird support pages "import evolution messages" link suggests.
Does anyone know which version of evolution supports mbox format.

---

