---
title: "ubuntu 16.04.2 desktop theme changes by itself ??"
date: 2017-03-29
forum: General Help
---

### Post by pretty_whistle on 2017-03-29
I have Ubuntu 16.04.2 with XFCE desktop environment installed.

I started with Ubuntu 16.04 and ran updates on 3-27-17 which gave me 16.04.2 upgrade.  When done with it, after restarting it and desktop came up the desktop theme had been changed by itself.  Icon colors different on desktop folders, text size under icons smaller, tops of system installed program windows were black theme instead of gray I had.

I went to various places to see if these theme settings had been changed as well and this caused it but nope, still the same.

I decided to try logging out and logging back in to see if that would reset it back - it did.

Then the theme changed again, the very next day on the 28th.

Next change though, for no reason this time and rather "suddenly" the desktop theme changed again but by itself this time - no restart or logging out or shutting down had precipitated it.  I was just sitting reading something and looked over and there it was when just a minute ago it was normal.  There was a difference this time as to the theme itself, it included a different wallpaper background for the desktop - a system included one, and the theme was different as well, the folders weren't the same color as with the first theme change but the text under the desktop icons were small again.  Also this time, unlike before, it "hid" system folders that were usually visible on my desktop : trash, file system, home folder, removable drives.

This time to hopefully reset it for good I tried this idea:  I logged out, logged back in, then restarted it.  This changed the theme back to where I had it.

Now, today is 3-29-17 and no theme change again so far, hopefully what I did keeps it in place this time.

I thought I'd post this though it's panning out ok so far for the following reasons:

1
Let users know what happened here and if it happens to them maybe this fix will work for them.

2
Question : should I report this as a bug?  Probably is my guess but let me know.....

3
If this fix I used isn't really a fix and it'll repeat itself given time, do you know of an actual forever fix for this?  Let me know.

4
Has anyone else had a theme change happen to them?

---

### Post by pretty_whistle on 2017-03-30
Update :

The 28th was the last time the theme changed, nothing since then.  Now it's 2 days since it last did it, hopefully that's good news since it did it day one, then day two, now nothing for 2 whole days....looking good so far....

---

### Post by RobGoss on 2017-03-30
Feel free to mark this thread as solved if you have fixed your issue, you can use the **Thread tool **at the top of this post

---

### Post by pretty_whistle on 2017-04-01
Update again:

As of today, the theme changing has stopped and I'd say it looks like for good (today is April 1, 2017), however not the topic of theme changing granted but I've not mentioned another "quirk" that started with running that update back on the 27th :

Just now is the 3rd time I've had a text document permanently delete itself "magically" as I tried to move it into another folder.  This started right after the updating was done.

Quirks around here....very odd....thought I'd mention it.....

So there's been two odd things :

1
Theme changing.  Stopped.

2
.txt files permanently deleting themselves when moving it into another folder. (though not every time, and seems random).

Weird.

---

### Post by pretty_whistle on 2017-04-01
Update again :

Now I just had a whole email thread delete itself...while it was open too.  I had it open after I sent it to my other gmail account in Thunderbird, then I stepped away for a bit, came back and now it's deleted.  I mean the whole thing is gone, not in trash in either POP3 account - not in the one I used to send it nor the one that received it, not in sent folder where a copy should be when I sent it, and not in the inbox of the account that received it either.

Then I looked in the Thunderbird folder where all emails are kept and it's not there either, not in the sent, inbox, nor in the trash.

I even resorted to looking where it shouldn't be, in the archive of each account - not in there either!

I tell ya, this is odd stuff.  Is this Halloween ghost haunting time?  Lol....
:/

Funnier, because Thunderbird email program is set to keep a copy of emails online in the web accounts, with this glitch it has managed to not allow it to keep a copy there either and deleted it instead! Update on this one :  Just went into my Thunderbird email program and found the setting for saving an online copy of everything had been changed to delete that copy if my desktop copy gets deleted, so this explains this part however this setting could only get changed if the update I did with Ubuntu made it do it...the update is still to blame plus this setting being changed doesn't explain the opened email closing by itself and then permanently deleting all the copies of it itself, including the one that would've normally landed in the trash in both POP3 accounts had I done it manually, so the update is causing this part of it.

Holy smoke!

:/

---

### Post by pretty_whistle on 2017-04-01
Update once again :

Now it's even worse.  I've decided to restore the backup of the computer I made before updating this thing but while I did tried to save a few items onto a flash drive that I had accumulated since then, I couldn't do one thing which was to drag and drop shortcuts from the applications menu 'personal folder' I made there into a folder for it on the desktop.  Also I had tried to drag a few shortcuts of programs into this same folder from the desktop itself into that folder and the same happened, which was this :

I tried to drag 8 shortcuts in there but only 3 got in there.  The others, once in there, turned into the same .desktop shortcut to the ala-cart program which is the Ubuntu search files tool.  I tried several times but it kept doing it.  Then when it looked like it finally worked, I tried to copy this folder of shortcuts onto the flash drive but there it goes again - turned all but 3 shortcuts in that folder into ala-cart.desktop shortcuts.

I gave up on this folder of shortcuts since it's failing so bad.

My system is getting worse as time passes, time for restoring that backup and then reporting this as a bug of some sort.

A bug in what exactly I cannot say.  I last had an update in August 2016 and then this latest one with the upgraded release of 16.04.2 included in it.  Who knows if it's that upgraded release or the various new kernels it updated at the same time that's caused this bug.  The devs can have fun with this one and figure out what's caused it.

Farewell for now.....

---

### Post by pretty_whistle on 2017-04-02
Ok, restored backup but guess what happened??  It followed me!!!!!

Seriously, it's been deleting folders left and right!  Ah!

Here's what I did:

1
Made backup of entire OS on 3-27-17.

2
Updated system 3-27-17 right afterwards.  Also removed old kernels per instructions here (done right after updating) :

[http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html](http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html)

Not sure, either before removal of old kernels or right after it everything started to go bad.

3
Today, 4-1-17, plugged in flash drive not used since months before updating (and had worked fine), copied a few things into to save.  Started to get, as per post above, a folder with erratic behavior in that drive itself, plus all the while erratic behavior on the desktop as per above post indicated already.

4
Unplugged that flash drive and set it aside.  Plugged in portable drive where OS backups are stored. I did all this while on the weird-acting desktop - perhaps the mistake here, should've waited for that till right after turning off computer and not while on the tainted OS (hope I don't pay for that one with the whole portable drive and backups to OS on it, all gone bad!!!)... Put in redo backup program on disk into tray, then rebooted computer to restore OS.

5
Restored OS ok.  Got to desktop.  Plugged in flash drive and copy/pasted it's saved stuff onto desktop.  Did this right away, did not wait around to see if the restored backup was possibly tainted from having plugged it in while on that tainted OS was in there so who knows on that one yet....  in any case, I copied folders from the tainted flash drive copy and took one folder and moved it around a bit and here we go - that one deleted itself.  Then I took an older copy of that same deleted folder from the non-tainted OS, pasted it onto the desktop where the other one deleted itself and moved it around a bit like I did with the other one (trying to test it by doing as I did before, moving it a bit) as a test and sure enough - deleted too.  Then I did this again with another non-tainted one, another copy of that same folder from the non-tainted OS and sure enough - deleted itself too!!

Then I come here to post.  I have an older version of Chrome and it has that old speed dial thing that Opera had (don't know if still does though) where in a new tab, it has the ability to bookmark sites right there on the blank tab page instead of in a bookmarks folder and it sometimes has bookmarked things for me randomly causing me to have to delete them off.  So I saw about 5 of them again and went to delete them off and but after 2 the rest deleted themselves!!!!  Now this delete thing is doing it in Chrome speed dial too!

Sounds like a virus to me although I hear Linux isn't usually, if at all, a target - it's always Windows and Mac, however it's sure acting it.

People -

Give me your thoughts on this.  What is this, is it :

A
Virus, very rare.

B
Bug in updates/upgrade.

C
Removal of old kernels caused something.

D
Hard drive breaking/broken and it's displaying "symptoms".

E
Other???

I think personally it's got to be a bug but can't figure out how it can "migrate" like that, so that leaves me with hard drive failing.  Before I invest $$$ for new laptop, tell me what you think, ok?  Thanks everyone.

Some hard drive info to help out :

655440 bad sectors
489 GB &#8212; 446 GB free (8.8% full)
/dev/sda1
Partition type :  Linux (Bootable)
Ext4 (version 1.0) &#8212; Mounted at Filesystem Root
Hard Disk Model :  Hitachi HTS545050A7E380 (GG2OA7A0)
Size :  500 GB (500,107,862,016 bytes)
Serial Number :  TE854449D69PYW
Bought laptop :  about 2003 refurbished

You know something, the more I think about this the more I think the hard drive is failing because it's not like Linux to get a virus - have had this OS for 6 years and nothing.  And as far as a buggy update, I've had one once and had to restore the backup of the OS but it never ever "migrated" like this which means.....I'm afraid so and I bet I'm right .....$$$ time to buy a new laptop.... I'll Google it and see and also let you all have your input but I bet that's it.....

---

### Post by RobGoss on 2017-04-02
>  Sounds like a virus to me although I hear Linux isn't usually, if at all, a target - it's always Windows and Mac, however it's sure acting it. 

Nothing is impossible but I just don't think this is a virus, might be a glitch in the system  

I have never seen a issue like this but not to say it's not happening, I would not know what to recommend to fix this issue. If you feel the need to reinstall a fresh installation of Ubuntu it might get rid of these issues.

---

### Post by pretty_whistle on 2017-04-03
Ah ha!!  I do need a new computer!  Here's why I say this :

1
Looked up symptoms of hard drive failure, there's about 10 common signs - all of the above are on those lists.

2
Since my last post I realized 2 other things had been going wrong but I didn't make the connection till now - my pointer has been acting chronically unresponsive & odd for nearly 3 weeks &  1 certain USB port (on the opposite side of the computer from where the wireless mouse is plugged in) screwed up & has fried within 4 days 2 new USB computer lights that I plugged in that port.

Mind you, these 2 hardware issues in 2 different ports both acting up during the same time period?  No coincidence.  Now add in this telling fact : These hardware issues started before the updates were done.....so guess what this all adds up to?  Hard drive failure BIG TIME & IT GOT WORSE SINCE MY LAST POST.

New computer time!!  I should get it in the next 7 days.  In the meantime I'm not using that thing since it sits there acting like a drunk, wobbling while it walks...lol.

Thanks for replying.  And thanks to a family member who said it might be hard drive failure- I forgot that one though obvious! Lol.

Now I just have to sit & dread what may be coming next, which is did this hard drive issue, which cause 2 ports to mess up what was plugged in there also possibly fry my portable drive or the OS backups on it?  If so, I'll lose the backups & that means having to start from scratch...I dread the thought.  One thing's for sure, whatever the outcome I'll take the advice I've read - keep another backup online in storage so if the backup you have & the portable drive it's on gets damaged you'll still have the one in storage & can restore the system using that!  Oh well...live & learn....
fun fun fun   lol

---

### Post by RobGoss on 2017-04-03
I would also make sure you have anything important backed up if it is in fact a hardware issue you have know when it will decide to just stop

---

### Post by pretty_whistle on 2017-04-04
Rob,

I did & I did so rather quickly since I knew it might shut down at any moment & not come back on anymore.  Luckily I didn't have much to back up so it was  quick to do.  &#128512;  &#10024;

---

### Post by RobGoss on 2017-04-04
Glad you got it all backed up

---

