---
title: "Mass rip data cds"
date: 2016-12-25
forum: General Help
---

### Post by timandjulz on 2016-12-25
After failure of my google-fu I must now appeal to the community. 

I am trying to mass rip hundreds of data CDs and DVDs to isos for archival.  There are plenty of programs to rip music cds or movie dvds.  But I can't find any to do the same for data.

The situation:
0) Using Ubuntu Desktop with xfce4 (can switch to Gnome or other if it helps)
1) 5 CD/DVD rom drives
2) Mix of several hundred data CD/DVDs in a stack
3) Expect to drop a disc in, have the system copy /dev/sr[0-5] to /backups/sr[0-5]_{label}_{unique_datetimestamp}.iso
4) Optionally verify the md5 for cd/dvd and iso.
5) When done it should eject the disc

I have Bash knowledge and am willing to script it.  Except I am not sure how to trigger the script whenever a disc is inserted.

Any help is appreciated.

Thanks,
Tim

---

### Post by Keith_Helms on 2016-12-25
You could probably put together a script that sits on top of the dd command.
```
dd if=/dev/sr0 of=image_name.iso
```

Instead of having it try to detect an inserted disc, I think I'd just have it put up a prompt saying "insert a disc into sr[0-5]", do the copy, then redisplay the prompt when finished.

It's possible to have one script handle 5 drives at once, but it would have to fancy.  You'd have to spawn the dd commands off in asynchronous threads and then poll for task completion.  If would be easier to just open 5 terminal windows and run a copy of the script in each.  You could pass the drive device in as a parameter to the script - i.e. **copydisc.sh /dev/sr0**.

---

### Post by timandjulz on 2016-12-26
Hi Keith,

I should have been more specific.  I want to remove all manual steps except swapping discs.  So manually launching scripts each time is not what I am looking for.

On the plus side, I have started a script that is launched by udev rules and rips using ddrescue instead of dd.  (ddrescue handles bad blocks on discs)  Unfortunately it fails for some of my test discs.

So I am still looking for a solution.

**Does anyone else have a suggestion for a script that automatically rips data to .iso files every time you put a disc in?**

Thanks,
Tim

---

