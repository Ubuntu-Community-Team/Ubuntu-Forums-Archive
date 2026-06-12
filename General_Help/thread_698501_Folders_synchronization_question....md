---
title: "Folders synchronization question..."
date: 2008-02-16
forum: General Help
---

### Post by geo909 on 2008-02-16
Hello everybody.
I have purchased an external USB hard drive in order to make regular folder backups.
I have used rsync a bit, it seems fast and easy. I do:
```
rsync -a /myinternaldisk/sourcefolder/ /externaldisk/destinationfolder 
```
and I'm ok.

But there's also a thing I want to accomplish and will save me lots of time:

Is there a way I could manage to make rsync not to duplicate files in the destination folder,when they are moved from a folder inside /sourcefolder into another one?

OK, confusing. Let me say it as an example. Let's say I have folder /A and want to back it up in /B.
I do ```
rsync -a /A/ /B
```
But /A has tho folders inside, let's call them /A/A1 and /A/A2. Inside /A/A1 there is a file. let's call it "myfile". If I move "myfile" from A1 to A2 after the rysnc and synchronize again later, I will have "myfile" in both /B/A1 and /B/A2, that is, it will be duplicated in my destination folder..

Does anyone knows how could I prevent that? How could I make "rsync" see such movements of files in destination folder?

If that is not possible, is there any tool other than rsync that will be able to accomplish that?

---

### Post by chrisccoulson on 2008-02-16
If you run rsync with the --delete option, it will remove files from the destination that no longer exist on the source. So, in your above example, the file wouldn't exist twice on the destination.

---

### Post by geo909 on 2008-02-16
> **chrisccoulson said:**
> If you run rsync with the --delete option, it will remove files from the destination that no longer exist on the source. So, in your above example, the file wouldn't exist twice on the destination.

Hmm..

Yes, indeed that will do the job...
But it will also erase any file I have erased permanently in my source folder and I don't really want that.

 Sorry I didn't mention it earlier I'm not so familiar with rsync and I didn't know this possibility

---

### Post by chrisccoulson on 2008-02-16
I'm not sure what else to suggest then. As far as rsync is concerned, a file moved is a file deleted from one folder and added to another folder. This is how rsync will treat it, and I don't think it can distinguish between a file that has been deleted and a file that has been moved (correct me if I'm wrong).

What you need is an option like - don't delete the file from the destination, unless the file exists somewhere on the source. That would mean that files moved on the source are deleted from the destination (and re-sync'd elsewhere), but files deleted completely from the source stay on the destination. Is that what you're asking?

---

### Post by geo909 on 2008-02-16
> **chrisccoulson said:**
> 
What you need is an option like - don't delete the file from the destination, unless the file exists somewhere on the source. That would mean that files moved on the source are deleted from the destination (and re-sync'd elsewhere), but files deleted completely from the source stay on the destination. Is that what you're asking?

Yes, that is *exactly* what I would like to do!!!
Thanks for making it clear.. 
Do you think there is a way to accomplish that?

---

