---
title: "Thunderbird Takes Ages Copying Mail to Sent Folder"
date: 2013-03-12
forum: General Help
---

### Post by SillySod on 2013-03-12
As the title says really: when I am sending a message using Thunderbird, it pops up saying "delivering mail" which goes through pretty quickly, but then it comes up with "copying message to sent items folder" and this takes a very long time, sometimes 5 minutes.  It always seems to succeed though.

This is happening on my notebook when using our home wireless connection.  It seems to happen frequently now, I have noticed the frequency of it increasing over time.  I used to get this happening sometimes if I wasn't at home and using mobile broadband, but now it happens at home in the majority of cases.

I send plain text messages and even if I'm replying to a long thread, it's no more than a few K altogether so I don't think it's a message size problem.

Any ideas?

---

### Post by SeijiSensei on 2013-03-12
If you're using an IMAP connection, your Sent folder is likely on the remote server, not on your local machine.  If TBird cannot successfully log into the IMAP server, you'll see those long delays.  

One thing you can try to test this is by copying a few messages from one IMAP folder to another. Do you see similar delays?

---

### Post by rnerwein on 2013-03-12
hi 
 				 					[URL="http://ubuntuforums.org/member.php?u=698195"] 						 							[IMG]http://ubuntuforums.org/customavatars/avatar698195_3.gif[/IMG]
						 					[/URL] 				 				 					 						 	[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
ups i copied your avatar too. but you are wright. i am using TBird too and using IMAP. the mail is on my server but the message "copy .... bla bla still pops up".
ciao

---

### Post by alexandre-grojsgold on 2013-08-10
I was experiencing  the same problem and found a solutions that not only solved it  but also offered a more efficient way of sending mail.

 

 I configured Thunderbird client  to: (1) do not  save a copy of sent mail and (2) automatically send me a blind copy of each mail sent. In the mail server system I defined a filter that would place every mail received from myself into a separate folder called sent-mail. The way of defining such filter varies from server to server, but most mail systems offer this capability.

 

 A dirty workaround? Well, maybe. But if you look carefully a workaround that make sending of mail with bit achievements much faster: the client sends the mail and attached file only once! In the original configuration, TB sent the mail twice, first tome to the SMTP port, and then again to store it to a folder, through IMAP port.  

BTW, if you use gmail, you simply not need not configure TB to save a copy. Gmail server will do it automatically!

---

