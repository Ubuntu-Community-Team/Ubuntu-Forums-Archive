---
title: "Messages vanishing in Thunderbird"
date: 2007-01-27
forum: General Help
---

### Post by WebDrake on 2007-01-27
Hello all,

I have an odd problem with Thunderbird: some of the messages that are plainly there, if one looks at the mailbox file in a text editor, are not visible in the relevant folder.

Before going on, I *know* that messages are maintained in the file if they are deleted within Thunderbird, and that it is necessary to compact folders.  I don't believe these messages were deleted, I think Thunderbird is not displaying them properly, or that perhaps there is something wrong with the file.

An additional odd factor is that the file/folder in question is used to store messages from a mailing list.  I have not been receiving any new messages from this list for some time.  My suspicion is that the two problems are related and Thunderbird is failing to add new messages to this file (the latest in the file---and it is not displayed in Thunderbird---is dated 6 December).

Can anyone advise?  I'm using Tb 1.5.0.9 on Ubuntu 6.10.

Many thanks,

     -- Joe

---

### Post by NT4usB on 2007-01-27
Check message view setting:
View>Messages>All

Compact the folder
File>Compact Folders

File permissions changed recently on your profile folder/files so your user can no longer write to it?

Create a new profile and see if the problem persists.
```
mozilla-thunderbird --profilemanager
```

ed: have you looked under Local Folders to see if they're being saved there?

---

### Post by phossal on 2007-01-27
> **NT4usB said:**
> File permissions changed recently on your profile folder/files so your user can no longer write to it?

That's a good guess. Or if he backed up, copied and pasted, or otherwise messed with ~/.thunderbird.

---

### Post by WebDrake on 2007-01-27
Thanks for the suggestions and ideas. :KS
> **NT4usB said:**
> Check message view setting:
View>Messages>All

Compact the folder
File>Compact Folders

Neither of the above as far as I can see.

> **NT4usB said:**
> File permissions changed recently on your profile folder/files so your user can no longer write to it?
Permissions are identical to other similar files/folders which still work fine.

> **NT4usB said:**
> Create a new profile and see if the problem persists.
```
mozilla-thunderbird --profilemanager
```
Didn't help. :-(

> **NT4usB said:**
> ed: have you looked under Local Folders to see if they're being saved there?
Local Folders is empty.

(At least) the last two emails in the file (visible in a text editor) persist after compacting the folders, but are not visible in Thunderbird itself.  New messages have not been arriving for some time.  I would assume simply that there was an error in my subscription to the mailing list if it wasn't for the "missing" emails.

I just had a look at the .msf file and it contains reference to stuff after the dates in the actual mailbox file.  It looks like there's discrepancies between the two.

Since it's just a mailing list record I'm tempted to simply delete the two files and let them be recreated empty....

If it might help in tracking down the source of the error I'm quite happy to post the relevant files here, since after all it's only a record of the git list for the last few months.

---

### Post by phossal on 2007-01-27
Here's a suggestion: copy out ~/.thunderbird and rename it. [Download Thunderbird]("http://www.mozilla.com/en-US/thunderbird/") from mozilla.com (essentially you're reinstalling it), and extract it. Then run it. Recreate the profile. if things work, you can transfer individual files from the old ~/.thunderbird.

---

### Post by NT4usB on 2007-01-28
> **WebDrake said:**
> ...

(At least) the last two emails in the file (visible in a text editor) persist after compacting the folders, but are not visible in Thunderbird itself.  New messages have not been arriving for some time.  I would assume simply that there was an error in my subscription to the mailing list if it wasn't for the "missing" emails.

This sure sounds like the View setting is set to unread.
Are emails you send to yourself showing up?

> 
I just had a look at the .msf file and it contains reference to stuff after the dates in the actual mailbox file.  It looks like there's discrepancies between the two.

oops, forgot that one. 
Delete the .msf files (these are index files) and they will rebuild next time you open Thunderbird. (uh, close TB before deleting them)

If creating a new profile and setting it up with your mailing list info didn't work, I have to suspect it's something outside Thunderbird causing it. 
Are you running any plugins or themes? Is Junk Mail filter nailing them?

Reinstalling TB won't help as it will use your old profile information (where 99% of the problems usually reside.)

---

### Post by phossal on 2007-01-28
> **NT4usB said:**
> Reinstalling TB won't help as it will use your old profile information (where 99% of the problems usually reside.)

Isn't that in ~/.thunderbird? That's why he would *remove* it before reinstalling.

---

### Post by NT4usB on 2007-01-28
Yea, you did say reinstall **and** create a new profile.
General consensus is reinstalling usually doesn't fix anything that just creating a new profile wouldn't. 
More often, it adds frustration since most users are unaware of the separation of program and profile so they think they're starting fresh when they reinstall.
You can run TB in safe mode which disables themes and plugins but I don't think it will change anything.
```
(/path/to/thunderbird/) mozilla-thunderbird --safe-mode
```
Lots of discussion at:
news.mozilla.org

---

### Post by phossal on 2007-01-28
> **NT4usB said:**
> General consensus is reinstalling usually doesn't fix anything that just creating a new profile wouldn't. ...they think they're starting fresh when they reinstall

If you install Thunderbird from the website, by removing ~/.thunderbird, you effectively *are* starting fresh. That's the point. I'm not sure what you're talking about. By "create a new profile", I just meant "start over from scratch, enter your info, try to get mail". lol

---

### Post by NT4usB on 2007-01-28
You're right. I'm stuck in windows thinking where the profile resides in a separate path from Thunderbird. 
nuking .mozilla-thunderbird/... will remove all the profile info.
My point is, if you create a new profile and it works, you can move over the stuff from your old profile (until it breaks) and:
1. figure out what's breaking it.
2. save (most or all) of your old stuff.

---

### Post by phossal on 2007-01-28
> **phossal said:**
> Here's a suggestion: copy out ~/.thunderbird and rename it. [Download Thunderbird]("http://www.mozilla.com/en-US/thunderbird/") from mozilla.com (essentially you're reinstalling it), and extract it. Then run it. Recreate the profile. [SIZE="1"][COLOR="SlateGray"]**if things work, you can transfer individual files from the old ~/.thunderbird.**[/COLOR][/SIZE]

That's a good idea. We said *essentially* that 6 hours ago. ;) It must've worked for him, too, because he hasn't been back. Together, I think we managed to help the guy already.

---

### Post by WebDrake on 2007-01-28
> **phossal said:**
> That's a good idea. We said *essentially* that 6 hours ago. ;) It must've worked for him, too, because he hasn't been back. Together, I think we managed to help the guy already.
Didn't actually try that yet, because I don't want to go the "full nuke" option until absolutely necessary.  I emphasise that the problem is with this one folder, not anything else.

What I have just done is to delete (well, move....) the offending mail file/folder, and redo the filters, so that if there is no problem with the mailing list itself, new mail should be able to come through.  It's certainly not getting hit by junk mail filtering, there are no list emails in my Junk folder.

If I don't get any new mail, I will contact the mailing list owner to confirm there's no issue.  I should have done this earlier, but the stuff I found inside the mailbox file made me want to check on other potential issues before doing that.

---

### Post by phossal on 2007-01-28
> **WebDrake said:**
> Didn't actually try that yet, because I don't want to go the "full nuke" option until absolutely necessary.

Serious miscommunication: If you download Thunderbird from mozilla, it comes down in, like, a .tar file. You can right-click and extract it to your desktop (and leave it there). That gives you ~/Desktop/Thunderbird. When you run the startup script, *~/Desktop/Thunderbird/thunderbird*, it launches the program, and if there isn't a ~/.thunderbird file hidden in your personal directory, it creates one. 

I don't know about "nuking" anything. All I suggested was that you rename the entire file from /home/<user>/.thunderbird to something else, and download a new Thunderbird from the web.

Then, set up the account for the mailing list again. If that works, you know there is a problem with *some* file in the ~/.thunderbird, or ~/Desktop/Thunderbird file. You don't *lose* anything. You're just putting boundaries on the problem. You can slide the older ~/.thunderbird file back over the newer one - if you get troubles, you've isolated the problem further.

The whole process would take ten minutes or less.

---

### Post by WebDrake on 2007-01-28
> **phossal said:**
> Serious miscommunication: If you download Thunderbird from mozilla, it comes down in, like, a .tar file. You can right-click and extract it to your desktop (and leave it there). That gives you ~/Desktop/Thunderbird. When you run the startup script, *~/Desktop/Thunderbird/thunderbird*, it launches the program, and if there isn't a ~/.thunderbird file hidden in your personal directory, it creates one. 

I don't know about "nuking" anything. All I suggested was that you rename the entire file from /home/<user>/.thunderbird to something else, and download a new Thunderbird from the web.

Then, set up the account for the mailing list again. If that works, you know there is a problem with *some* file in the ~/.thunderbird, or ~/Desktop/Thunderbird file. You don't *lose* anything. You're just putting boundaries on the problem. You can slide the older ~/.thunderbird file back over the newer one - if you get troubles, you've isolated the problem further.

The whole process would take ten minutes or less.
OK.  I had assumed you meant recreating my Thunderbird profile from scratch and importing old mail (a bit of a major effort as I have multiple accounts).  I'll be back with results.

---

### Post by WebDrake on 2007-01-28
Well, it looks like after all that it was just something with the mailing list---resubscribing meant new emails started showing up, even if the "missing" messages visible in the file but not in Tb itself still fail to appear.

I still don't understand why there should be these "missing" mails, given that I compacted the folder (and wouldn't have deleted them anyway) but I guess that's something I should take direct to the Thunderbird folks.  Those emails didn't show up even in the newly-downloaded binary direct from Mozilla.

I feel a bit of a fool as I've probably led everyone a merry dance to nowhere, but with any luck this discussion will be useful to someone else.

---

