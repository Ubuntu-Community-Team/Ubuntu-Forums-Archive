---
title: "Is Edgy's most catastrophic problem fixed yet?"
date: 2007-03-16
forum: General Help
---

### Post by Jim March on 2007-03-16
I have a favor to ask: could somebody please put a file they don't care about on a USB drive, then do a "move to trash" on it.

And then see if it's actually in the trash, or completely gone.

What I'm hoping for is the latter.

The reason I abandoned Edgy (and Ubuntu) about five months ago is that somebody in the Ubuntu project tried to use the trashcan function on removable drives.  Problem is, if you unmount the removable drive without first completely emptying trash, your file system on your *primary* drive will come explosively unglued.  Within a few hours of my doing just that, I found 3,000+ random system file in my trashcan and everything getting more and more sickly.

In digging into the issue after a total backup and reinstall, it appears there was some debate among the developers on this point.  Some wanted to provide an easy un-erase feature on removable drives, others called it a disaster waiting to happen and noted that both MacOS and Windows does an immediate-delete on removable-drive file erases.

I sided with the latter camp, downloaded OpenSuse and moved on.

I'm considering switching back, after finding "minor issues" with every other distro.  And I miss the support forums here.  But...I'm looking for a distro I can load on friend's machines and support, and this one big black hairy bug is holding me back.

Did y'all realize this was a problem and fix it?  Or is there some setting possible that will eliminate the "trashcan function" on removable media?

As to the title of this post: something innocuous that WILL cause explosive instability and data loss in a repeatable fashion IS a "catastrophic" problem, no two ways about it.  Sorry if it tweaks anyone but...it's the truth.

Jim

---

### Post by FuturePilot on 2007-03-16
Are you saying that if you move a file to the trash from a USB drive and then eject it without emptying the trash that everything gets messed up? I've been using Ubuntu for close to a year now and have done exactly that countless times and have never encountered such a thing. What happens when you delete a file from a USB drive is it just moves it to a hidden directory on the drive called .trash. Then when you empty the trash it completely removes whatever is in that directory.

---

### Post by DarkN00b on 2007-03-16
I have never had this issue. Removable drives have always worked for me just like they do in Windows.

---

### Post by Jim March on 2007-03-16
> **FuturePilot said:**
> Are you saying that if you move a file to the trash from a USB drive and then eject it without emptying the trash that everything gets messed up? I've been using Ubuntu for close to a year now and have done exactly that countless times and have never encountered such a thing. What happens when you delete a file from a USB drive is it just moves it to a hidden directory on the drive called .trash. Then when you empty the trash it completely removes whatever is in that directory.

Trust me: in some cases this seriously doesn't work.

Damned if I know just what the contributing factors are, but I have never seen any drive come unglued as fast as it did in that situation.  And it wasn't the drive itself - I've been using this same 60gig laptop drive on a succession of distros since.

I guess worst case I can just warn people not to do that!

Jim

---

### Post by rovernaut on 2007-03-16
> **FuturePilot said:**
> Are you saying that if you move a file to the trash from a USB drive and then eject it without emptying the trash that everything gets messed up? I've been using Ubuntu for close to a year now and have done exactly that countless times and have never encountered such a thing. What happens when you delete a file from a USB drive is it just moves it to a hidden directory on the drive called .trash. Then when you empty the trash it completely removes whatever is in that directory.

Humm, I too am having a problem deleting stuff on my USB removeable drive.
 When I click on files and chose move to trash they go to a hidden folder on the USB called file:///media/usbdisk/.Trash-1000
If I click on the trash folder  it gives me a 'files' folder > 'info'> then lists all the stuff that was deleted.
Would love to know how to get rid of all the 'evidence of those files"
 The only way I have found was to dual boot back to Windows ans do a format of the disk.

---

### Post by DarkN00b on 2007-03-16
If you want to really get rid of these files, try pressing shift+delete. That should bypass the trash folder. Just be warned that you will [COLOR="Red"]*never*[/COLOR] see these files again.

---

### Post by yabbadabbadont on 2007-03-16
In Nautilus, Edit->Preferences->Behavior.  Check "Include a Delete command that bypasses Trash".  Then right-click on the files you want to delete and take the Delete option.  (or just use shift-delete as previously suggested ;))

---

### Post by Jim March on 2007-03-16
Rovernaut: it sounds like what you're describing is that they've changed things by doing multiple trashcans.  Early on they were doing everything with a single trashcan.

Well hell, multiple trashcans would be better than what I saw.

---

### Post by kerry_s on 2007-03-16
I would just use a alternative file manager with out the trash feature. I use emelfm and when you delete it's gone. There are many other file managers with out trash.

But then again you can just make a simple nautilus script for the right click, with something like this.

Name:Skip-trash
script->
#!/bin/sh
exec rm %f

make it executable->
chmod +x Skip-trash

Just my thought, i would never abandon a distro for something thats easily worked around.

---

### Post by yabbadabbadont on 2007-03-16
> **kerry_s said:**
> But then again you can just make a simple nautilus script for the right click, with something like this.

Name:Skip-trash
script->
#!/bin/sh
exec rm %f

make it executable->
chmod +x Skip-trash

Just my thought, i would never abandon a distro for something thats easily worked around.
Why would you do that instead of just enabling that exact same behavior using a built-in option?  (which I already told them how to enable...  :lol:)

---

### Post by kerry_s on 2007-03-16
> **yabbadabbadont said:**
> Why would you do that instead of just enabling that exact same behavior using a built-in option?  (which I already told them how to enable...  :lol:)

Sorry, I didn't know, i haven't used nautilus in years. I was just trying to milk my old memory.

---

### Post by Jim March on 2007-03-16
At the time all this went down I was about 2 months new to Linux period.  I'm starting to realize it was fixable.  I had already had a bad experience with Edgy when I did the initially reported upgrade step from Dapper and it blew up in a lot of people's faces, so when I found this Edgy issue I just gagged.

What Edgy (and Dapper before it) never did was install auto-updates that broke anything, at least not on my rig.  Since then I've seen Fedora Core 6 do exactly that...

---

### Post by rovernaut on 2007-03-19
> **DarkN00b said:**
> If you want to really get rid of these files, try pressing shift+delete. That should bypass the trash folder. Just be warned that you will [COLOR="Red"]*never*[/COLOR] see these files again.

Thanks DarkNOOb, the Shift Delete Nuked them.
All is gone
Thanks.::KS

---

