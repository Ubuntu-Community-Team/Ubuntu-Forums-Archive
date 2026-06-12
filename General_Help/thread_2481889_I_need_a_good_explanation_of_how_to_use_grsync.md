---
title: "I need a good explanation of how to use grsync"
date: 2022-12-12
forum: General Help
---

### Post by lou6 on 2022-12-12
Can someone point me to a detailed explanation?  I've been using grsync for 8 years but a system crash has left me without access to my files and I can't remember how to set grsync up.  Please help if you know or can recommend a good explanation.  

Thank you, in advance.

---

### Post by Frogs Hair on 2022-12-12
I think you would have to explain how you want use grsyc. I used it to clone my pictures and documents to a removable drive occasionally. I now sync those folders with a different application after adding or removing content.

---

### Post by lou6 on 2022-12-12
I have been using grsync for daily backups for about 8 years.  I learned about grsync from a site on the 'net (was called how-to-geek back then but no longer exists).  My system crashed so I have no files to look at to see how I had grsync set up.  Right now I'm trying to define sessions but I keep getting a screen with a heading "Include these sessions" and can't get past it.

---

### Post by lou6 on 2022-12-13
I've managed to get grsync working but now I need to know how to exclude a folder from backup.  I used to know this but no longer remember - something about a list of files to include in the backup.  I still have the list but don't know where to include it in grsync.  
Help, please?

---

### Post by SHENGTON on 2022-12-14
To exclude a folder from a GRSync synchronization job, you will need to use the "Exclude" option in the "Options" section of the job configuration. This option allows you to specify a list of files or directories that you want to exclude from the sync.


Here is a step-by-step guide to excluding a folder from a GRSync synchronization job:



[LIST=1]
[*]Open GRSync and select the synchronization job that you want to modify.
[*]In the "Options" section, click on the "Exclude" button to open the "Exclude files" dialog.
[*]In the "Exclude files" dialog, click on the "Add" button to add a new exclude rule.
[*]In the "Rule" field, specify the name of the folder that you want to exclude from the sync. You can use wildcards (such as "*" or "?") to match multiple files or directories.
[*]In the "Type" field, select whether the exclude rule applies to files, directories, or both.
[*]Repeat steps 3-5 for each folder that you want to exclude from the sync.
[*]Once you have added all of the exclude rules that you want, click on the "OK" button to save the changes and close the "Exclude files" dialog.
[*]Click on the "Save" button to save the updated synchronization job.
[*]To run the synchronization job with the new exclude rules, select it from the list of saved jobs and click on the "Run" button. GRSync will sync the files and directories according to the rules that you have specified.
[/LIST]


I hope this helps!

---

### Post by lou6 on 2022-12-14
Thanks for replying - I don't see the exclude option in any of the options tabs.  Could it be that I have a different version of GRsync?

---

### Post by TheFu on 2022-12-14
a) how-to Geek is still posting and active.
b) grsync is just a GUI over rsync. If you use rsync, you would create a 2-3 line script that does what you want and you can 100% automate what it does.  

IMHO, rsync isn't really sufficient for backups, at least not alone for a number of reasons.  rsync + hardlinking can get to 80% of what a good backup tool does, but it doesn't provide versioning as owner, group, permissions, xattrs and ACLs change over time, which a better backup too handles.  Many excellent backup tools exist, some have GUIs.  Some don't because automation with a GUI is next to impossible for the middle of the night.  For about a decade, I've been using rdiff-backup, which handles the short-comings that rsync+hardlinks has.  Also, rdiff-backup's command looks much like an rsync command and the most recent backup set is just like an rsync mirror, so to get the most recent files back is just a copy or a recursive copy or ... we can use rsync. ;)  Older backups can manually be created too, but it is easier to ask rdiff-backup to restore a file or directory or entire set from 23 days ago.

If you really, really, want a GUI, and want to use rsync with hardlinking of different versions, use 'Back-in-Time'. It has the normal rsync flaws, but at least it does versioning in a way that my 80+ yr old mother could understand (RIP).  There are better solutions, but life is about compromise.  
Here's a how-to-Geek article on using Back-In-Time [https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/](https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/)  Short, to the point.

---

### Post by lou6 on 2022-12-14
Thanks TheFu - a quick looksee at Back In Time will definitely get me to try it.  Speaking as a retired computer programmer, Grsync is one of the least intuitive and poorly documented chunks of code I've ever seen.  I will continue to search for how-geek's original Grsync post...when I was able to get it working it really did the job very well.

---

### Post by lou6 on 2022-12-14
After careful assessment I've decided to stick with Grsync - it has it's faults (mainly virtually no documentation) but my familiarity is coming back as I work at it.  The backup runs have a few errors but the actual output looks good to me.

Thank you to the responders - your help is appreciated.

---

### Post by timgood on 2022-12-16
Here is a brief overview of how to use GRsync:

Install GRsync on your computer.

Launch the GRsync application.

In the "Source" field, specify the location of the source directory or file that you want to synchronize.

In the "Destination" field, specify the location of the destination directory or file that you want to synchronize with the source.

Choose the options that you want to use for the synchronization. Some common options include:

"Recursive": This option tells rsync to copy the contents of directories recursively.
"Preserve permissions": This option tells rsync to preserve the file permissions of the files being synchronized.
"Delete": This option tells rsync to delete files in the destination that are not present in the source.
Click the "Sync" button to start the synchronization process.

The synchronization process will begin, and a progress bar will be displayed showing the status of the process. When the synchronization is complete, a summary of the results will be displayed.

Note: It is important to carefully choose your options when using GRsync, as it can potentially overwrite or delete important files if used improperly. It is always a good idea to make a backup of your important files before using any file synchronization tool.

---

### Post by dragonfly41 on 2022-12-16
[COLOR=#000000]> Note: It is important to carefully choose your options when using GRsync, as it can potentially overwrite or delete important files if used improperly. It is always a good idea to make a backup of your important files before using any file synchronization tool.

Remember that there is a "dry run" feature which simulates a session run without actually syncing. This is a good precaution against "cockups".[/COLOR]

---

