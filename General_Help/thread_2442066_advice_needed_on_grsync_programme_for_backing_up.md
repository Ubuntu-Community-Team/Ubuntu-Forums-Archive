---
title: "advice needed on grsync programme for backing up"
date: 2020-04-29
forum: General Help
---

### Post by smokeyone2 on 2020-04-29
Hello

I am hoping for some guidance please on using GRSYNC to back up my photo collection. I have around 500gb of images
and was thinking of using GRSYNC to do an incremental back up on to an external SSD. Then use the external SSD to restore
the back up to an older little used computer. Is this a good idea and would the restore to an older computer be okay in so far
as would that also be an incremental restoration. I would then have two back ups - just in case...

At the moment I just do a copy & paste but unless I remember which folders have been altered since my last back up I have
to just copy all 500gb each time...

Many thanks for any advice.

---

### Post by cmcanulty on 2020-04-29
I've used grsync for years and love it. It is fast reliable and easy. The main thing is to set up the options for a particular backup the way you want and then save that backup by clicking the + in the toolbar and name it. You can have lots of setups for various backups. One thing I really want to stress is you make sure the source and destination are correct and realize that you should always click through to the destination source and make sure it's correct in case that drive is mounted with a different name. If you screw that up the backup could go to another folder and fill up another partition by mistake. I am attaching 3 screenshots showing the options I use. Of course your options may be different than mine. All of the options have a tooltip if you hover over them. Also I suggest 2 east test tips 1) you can click on the light bulb in the toolbar it runs a simulated backup so you can see if it works by *arrow by Rsync outputs you can see if there are any errors, often caused by a permission issue in some file 2) try a real test backup by say taking a flash drive with a few files and backk it up to someplace and see if that works as desired.I hope this helps.

[ATTACH=CONFIG]285674[/ATTACH]

[ATTACH=CONFIG]285675[/ATTACH]

[ATTACH=CONFIG]285676[/ATTACH]

---

### Post by sgage on 2020-04-29
I agree with cmcanulty. I've used and loved grsync for years. I like to experiment with different distros and such, and I use grsync to keep data synced among them. A separate job keeps config info quickly up-to-date. Learn how exclusion lists work, and check out all the options, and you can really fine-tune things.

---

### Post by smokeyone2 on 2020-04-29
Thank you very much for the advice and the screenshots. I will test it out to see if it behaves as I would like it to.
One thing though that I cannot double check at the moment is that if I restore to another third hard drive will grsync
overwrite an existing restore file or even incrementally overwrite it or do I need to delete an existing restore file.
Just thinking that at 500gb a throw if it just added another restoration the hard drive will soon be full.
Thanks again

---

### Post by dragonfly41 on 2020-04-29
Don't forget the "dry run" feature to test your runs before the "real run".

---

### Post by smokeyone2 on 2020-04-29
The dry run feature and the exclusions list make it sound even better - thank you to all for the advice -

---

### Post by kevdog on 2020-04-29
grsync uses rsync in the background.   You may also be interested in checking out a product known as vorta that uses borg in the background.  This makes versioned delta backups as opposed to rsync.  Just another program you may be interested in.

---

### Post by smokeyone2 on 2020-04-30
Is there an advantage to versioned delta backups....

---

