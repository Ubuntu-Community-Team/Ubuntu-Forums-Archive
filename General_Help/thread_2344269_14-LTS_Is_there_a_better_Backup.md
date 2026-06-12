---
title: "14-LTS: Is there a better Backup?"
date: 2016-11-23
forum: General Help
---

### Post by FerryGnu on 2016-11-23
Just had to use Restore for the built-in Backup, Deja I think it is, and then sit through 123-GB of home videos and music being restored.

That is crazy. Is there a better backup that actually checks to see if a file has been changed before needing to restore it?

Thanks

---

### Post by untrustytahr on 2016-11-23
Better?... maybe, depends on your requirements I suppose.

As far as your problem description goes though, deja-dup doesn't require a full restore (unless thats what you want).

You could just navigate to your file browser menu.  Open the folder in question and select: File-> Restore Missing files
Deja dup will then ask from where and walk you through.

You can also do it from the command line if you know the file name

```
[COLOR=#6C6C6C][FONT=sans-serif]**Restoring a Lost File**

[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]
[LIST]
[*]Browse to the folder containing the file you lost. 
[*]Click [COLOR=#6C6C6C][COLOR=#6C6C6C]File[/COLOR] &#9656; [COLOR=#6C6C6C]Restore Missing Files…[/COLOR][/COLOR]. 
[*]When the [COLOR=#6C6C6C]Restore[/COLOR] dialog appears, it will scan for files that are in the backup but no longer in the folder. 
[*]When you see the file you want to restore appear, select it and click [COLOR=#6C6C6C]Forward[/COLOR]. 
[*]Review your selections and click [COLOR=#6C6C6C]Restore[/COLOR]. 
[/LIST]
[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]


You can restore lost files from the command line as well, if you remember what their filenames were:
deja-dup --restore FILE1 FILE2
[/FONT][/COLOR]
```[COLOR=#3C3C3C][FONT=sans-serif][COLOR=#3C3C3C][FONT=sans-serif]
[/FONT][/COLOR] 

[/FONT][/COLOR]


If that fails for some reason, you could also use duplicity directly from the command line with the --file-to-restore option if you know the name as well.

---

### Post by FerryGnu on 2016-11-23
Thanks for the quick reply, but that is pretty cumbersome. I have just changed over the family PCs to Ubuntu and very happy, well, was until this morning. I hate to compare, but in windows a restore will only restore those files that have changed, unless you specifically tell it to over-write regardless. Your descriptions suggests the exact opposite of that and I need to tell it what to do. 

Other than the video and music folders I have no idea what had changed so I would have had to select dozens of folders. Makes no sense. I'd dearly love to see Ubuntu eventually blow windows out of the water but this is not even close.

I have read where good backup software copies all of the file meta-data too so the information is already available, just not used. It's like Ubuntu wants us to use the most difficult way first. :)

---

### Post by FerryGnu on 2016-11-23
OK, looks like Back In Time does it the smart way. A little clunky to use, but way better than that Deja thing.

---

