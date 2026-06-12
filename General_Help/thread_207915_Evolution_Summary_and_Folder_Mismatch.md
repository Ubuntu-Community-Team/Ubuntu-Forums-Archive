---
title: "Evolution: Summary and Folder Mismatch"
date: 2006-07-02
forum: General Help
---

### Post by mhinton539 on 2006-07-02
I've begun seeing the following error message from evolution mail whenever it checks for mail, or when I select or move away from the main Inbox:

[INDENT]Error while Storing folder 'Inbox'.
Summary and folder mismatch, even after a sync[/INDENT]

...and sure enough, as I browse through Inbox, I notice that the message pane and the summary pane get out of sync as I go. (Rather disturbing when they are: if I hit Delete now, what will be deleted? The message highlighted in the summary, the message displayed in the message pane, or something quite else?) Hmmmm...

What would be the cause of this? I've been using Evolution a while, and this just cropped up recently. (As an emergency measure, I'm temporarily using Kontact.) And how do I recover from this regrettable state of affairs?

Thanks for hints or help!
--Mark

---

### Post by xrchris on 2006-07-02
This comes and goes and is a long standing bug. 

I just close and reopen the application and all is fine.

---

### Post by mhinton539 on 2006-07-02
[QUOTE=xrchris]This comes and goes and is a long standing bug. 

I just close and reopen the application and all is fine.[/QUOTE]

Ah, if only it were so simple! The folder/summary sync issue I'm facing is retentive. I can exit evolution -- sounds oddly profound ;) -- and relaunch, and the problem persists. I can shutdown and reboot the computer and relaunch evolution, and the problem persists.

Something must have been corrupted in a database index, perhaps? But if so, how can I cause the indices to be rebuilt? Arrgghh.

--Mark

---

### Post by tom-ubuntu on 2006-10-16
Got now the exact same error for a while. It does not disappear with closing and reopening. Did you find a solution? Thanks!

---

### Post by Jorge on 2006-10-16
May I suggest a brutal solution (meanwhile the Evolution team fix this bug)?

I had the same problem so :
1. I rename (from inside Evolution) the folder as "Name-Old", and create a new one "Name" (I need it to have the same name, but  maybe you don't, so skip this step).
2. I selected all the messages in the old folder and copy them.
3. I pasted the selected messages into the new folder.
4. This is the ugly part: I quit Evolution and, using the file manager, I  erased every single instance of the "name-old" files.

Of course: do a backup before. This is not a regular procedure.

Have luck!

---

### Post by walmartshopper67 on 2006-10-27
I ran into this awhile ago - here's what I did (as posted somewhere around here):
Well, I found a way to get rid of the error once it shows up: deleting the file ~/.evolution/mail/local/Inbox.ev-summary (it may be in a different folder on your machine, if so just $sudo locate -u ; locate Inbox.ev-summary) You also may have to restart, then it should work.

I found a bit about it here - [http://bugzilla.gnome.org/show_bug.cgi?id=213072](http://bugzilla.gnome.org/show_bug.cgi?id=213072)

---

### Post by showe1966 on 2006-11-06
This has happened to me twice now.
It has always been after I got huge quantities of e-mail in my in box.
I tried the deleting summary files trick, and it did nothing for me.

I have found that a way of fixing the problem is to open evolution and, before the inbox has a time to update, go to the trash folder.
Then, click over the trash folder in the folder navigator bar and select "emtpty trash".

Once the trash has emptied, everything is okay again.

The more worrying point is when are we going to have to start calling it Microsoft ® Evolution ® now that the Suse has been sold......

---

### Post by nossifer on 2006-12-07
i keep a pretty tidy inbox, so i didnt mind deleting everything.  i did, it still happened.  i shut down Microsoft Suse Evolution ;) and everything came back AOK.  the bonus.... everything was back just teh way it should have been had nothing happened.

i am not sure if this happens for everyone.

---

### Post by secretspicy15 on 2007-02-16
Alright! I had this problem a week or two ago and it went away after a little while; i'm not sure what i did that time. Today I was getting it again, so i looked on here and the emptying the trash fix worked great! no drastic measures needed. Just restart evolution and empty the trash before it trys to send/recieve... all is well! thanks for the fix!
--TJ

---

### Post by utkjamie on 2007-02-19
I suddenly began having the same problem with the "summary and folder mismatch" errors. After restarting Evolution several times I noticed that I'd lost several hundred emails out of my inbox, many important and unread. Fortunately, after freaking out for a bit I deleted the summary files, restarted Evolution and they all magically reappeared (and there was joy and great celebration!).

---

### Post by dcstar on 2007-02-20
> **utkjamie said:**
> I suddenly began having the same problem with the "summary and folder mismatch" errors. After restarting Evolution several times I noticed that I'd lost several hundred emails out of my inbox, many important and unread. Fortunately, after freaking out for a bit I deleted the summary files, restarted Evolution and they all magically reappeared (and there was joy and great celebration!).

If you experience some file corruption then you may want to check your hardware and see if Write Caching is enabled for your hard drive(s).

Turning it off should improve integrity (at the expense of performance), have a look at some of the posts here for the ongoing debate:

[http://freshmeat.net/projects/hdparm](http://freshmeat.net/projects/hdparm)

---

### Post by Bionic_Beefpile on 2007-03-01
Just another confirmation that the "Empty Trash" fix worked for me.  Odd...

---

### Post by Keweenaw on 2007-03-28
The empty trash fix worked for me as well (it was the first fix I tried.)

Thanks to showe1966 and everyone else who contributed fixes.

---

### Post by darundal on 2007-04-08
The summary file trick didn't work for me, and neither did the empty trash trick. Anyone else have any workarounds?

---

### Post by movil on 2007-12-10
Try to do this:
Deleteing the file ~/.evolution/mail/local/Inbox.ev-summary should solve this
"mismatch". At least for the Inbox.
I saw this solution on launchpad. It worked out for me.

Also there is another post that says [SOLVED] here:
[http://ubuntuforums.org/showthread.php?t=206826](http://ubuntuforums.org/showthread.php?t=206826)

---

### Post by Mike-97470 on 2007-12-11
I just had this problem today after I had done a bunch of inbox cleanup and was trying to empty the Trash.  (I'm guessing there were more than 50 messages in the Trash.)

The error message mentioned that one of my folders (the "Friends" folder) had a summary/folder mismatch. (This repeated after Evolution was relaunched.)

After I moved about 1/2 of the Trash into a Temporary folder, I was able to empty the Trash.  I then moved the Temporary stuff back into the Trash and emptied that, then deleted the Temporary folder.

---

### Post by chamstar on 2008-05-09
Ï backed up my .evolution folder before a reinstall. After I put the folder back I started getting the same errors all the time, after viewing emails, send/receiving etc. Renaming the summary file did the trick!!

$:~/.evolution/mail/local$ mv Inbox.ev-summary Inbox.ev-summary.old

---

### Post by transporter_ii on 2008-07-02
I know this is an old topic, but I just had this happen to me, so it is still an issue.

I fixed it by creating a new folder under inbox, called "temp" and moving all the messages in my inbox to this folder. Did a "send and receive" e-mail after that and no longer got the mismatch error. I then moved all the e-mails back to the inbox and still no longer got the message.

Not saying it won't come back, I'm just saying that the error message stopped the minute I did the above.

---

