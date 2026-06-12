---
title: "kmail import email from evolution"
date: 2006-12-24
forum: General Help
---

### Post by clivel on 2006-12-24
I have been using Evolution on Edgy, but having used Kmail in the past I prefer it. I installed Kmail, and am now trying to import my Evolution mailboxes.
I emptied the Evolution trash, expunged all folders, and I am now trying to use the KMailCVT import tool, it shows that it is starting the import, displays 0%, and then freezes.
Any help would be appreciated, Thanks.

---

### Post by spidie on 2007-05-02
I am seeing the same problem with latest Feisty Kubuntu and the evolution folders to import are the latest too. Has anyone had any success with this? I can import them as standard mbox individually - but I have a *lot* of folders and it will take me a while doing it this way!

The only other way I can think of to do it is setup an intermediate IMAP server and import the mail via that.

Thanks in advance to anyone that can help.

Steve

---

### Post by antid0te on 2007-06-28
Same problem here, the KMailCVT import tool going freeze when importing messages from Evolution :( The first folder imported successfully, after that it freeze..

---

### Post by eudemus on 2007-08-06
Yeah, same problem here too! How do we get this thread some attention?!!!!
Cheers

---

### Post by slewis01 on 2008-01-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/127519](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/127519) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've got the same problem - the bug is listed here[URL="https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/127519"]
https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/127519[/URL]

I think the more people that subscribe to this bug the greater chance of it being sorted - or someone telling us what we were doing wrong :)

---

### Post by Tari Narmolanya on 2008-01-23
hm, bug is still open as i can see.... what a shame... hopefully there will be a solution soon ... or does anybody get a solution in the meantime ?

---

### Post by elp99jcm on 2008-02-02
I don't have a solution as such but a workaround. This is based on Ubuntu 7.10. I have recently installed KDE and liked it so wanted to import mail from evolution to Kontact (KMail).

I noticed that the import froze when trying to import the XXX.ev-summary-meta where XXX is the folder name. Not sure what these are, I'm sure I could find out with a bit of surfing.

I created a temporary directory and copied the evolution mail folder
~/.evolution/mail/local

The in the copied folder I deleted all the ev-summary-meta files. Then I ran Kontact and imported from the copied directory. All messages and attachments are present.

Hope that helps for now, although a bug fix is clearly required.

---

### Post by Tari Narmolanya on 2008-02-03
unfortunately it doesn't work for me :(
The import starts as before and then nothing happens. I've attached 3 screens.
This one shows the Import-window with system-monitor in the background. The Process is running, but the import-dialog freezes up.
[[IMG]http://img208.imageshack.us/img208/1474/emailimport1mb9.th.jpg[/IMG]](http://img208.imageshack.us/my.php?image=emailimport1mb9.jpg)

This one shows you the importing status in kmail itself, it ends up with 6 Mails.
[[IMG]http://img179.imageshack.us/img179/4020/emailimport2tm1.th.jpg[/IMG]](http://img179.imageshack.us/my.php?image=emailimport2tm1.jpg)

And on the next one you can see my copied folder of evolution mail folder, did i miss something ?
[[IMG]http://img208.imageshack.us/img208/7641/emailimport3rc0.th.jpg[/IMG]](http://img208.imageshack.us/my.php?image=emailimport3rc0.jpg)

oh, before i forget that, when i start the import, i only choose the whole folder to import (.../local), no special file, is that correct ?

---

### Post by elp99jcm on 2008-02-03
When you import the copied directory, what does the dialogue box say? I can't read from the image you posted. It should tell you what file it is trying to import when it freezes.

---

### Post by Tari Narmolanya on 2008-02-03
it says nothing, it becomes blanc... as you can see on the screen.

---

### Post by elp99jcm on 2008-02-06
Just a though, are you sure you've deleted the files mentioned above from the inbox.sbd directory? I had some in there and they were the first files imported.

Evolution uses the mbox format, which should be standard. I have reading about the mbox standard on wikipedia. The files in the evolution folder with no extension appear to be the mbox files. You could try creating a directory with just these files in.

---

### Post by ACGarland on 2008-04-27
> **elp99jcm said:**
> 

I created a temporary directory and copied the evolution mail folder
~/.evolution/mail/local

The in the copied folder I deleted all the ev-summary-meta files. Then I ran Kontact and imported from the copied directory. All messages and attachments are present.


Thanks for posting this work-around. It worked for me too.

---

