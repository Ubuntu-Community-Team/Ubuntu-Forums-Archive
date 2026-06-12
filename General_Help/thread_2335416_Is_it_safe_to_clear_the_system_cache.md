---
title: "Is it safe to clear the system cache?"
date: 2016-08-28
forum: General Help
---

### Post by danjswade on 2016-08-28
I've installed bleachbit as read it was a good package to do some housekeeping. I've run the preview and see I've over 100gb in the system cache. Am very new to Ubuntu and linux in general, so I was wondering if it's safe to delete these files and speed up my old laptop somewhat??

Thanks

---

### Post by Bashing-om on 2016-08-28
danjswade; Well ...

"beleachbit" is a touchy situation. While it is an excellent tool used "properly", it often will do much more than you may realize. A high degree of discretion is to be observed. In my opinion there is little to be gained from bleachbit that is not better done in terminal for housecleaning .
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove #removes old obsolete/orphaned files
sudo apt-get clean #clears out the local repository of retrieved package files
sudo apt update
sudo apt upgrade
sudo apt -f install #to check/fix any broken packages

```
is all that is required for the normal housecleaning. These commands clear the cache and also removes orphaned files and checks that the package manager is in a happy state.
Ya want to see what is in the cache ? Then:
```

ls -al /var/cache/apt/archives

```
then drill around for closer inspection

[INDENT][INDENT]driving a nail with a sledge hammer - bleachbit-
[INDENT][INDENT][INDENT]maybe undesired side effects
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2016-08-28
Bleachbit is a great tool I use it daily some of the features may take more time then others so make sure you view the dialog box when it appears letting you know how to proceed

I've been using it for sometime with out a hitch

I think it's safe for me to say deleting unwanted files Bleachbit detects should not effect your system as long as they are things like, cache, history, temporary, and so on

---

### Post by &amp;KyT$0P# on 2016-08-28
Well what exactly is a "system cache"?  I'm no expert but the only things I can think are the disk cache in RAM and the apt package cache (as already mentioned by Bashing-om).  Neither of those (not even both combined) would get that big would it?

Does Bleachbit give more details of what it thinks needs cleaned and if so can you please post that info here?

---

### Post by danjswade on 2016-08-29
Hi all

Thanks for the replies.

No, it doesn't give me any further info on what is in the cache.

With regards to bleachbit, I'm assuming if you don't know exactly what it's doing, it's best to stick with the terminal commands??

---

### Post by speartip on 2016-08-29
100 Gig in the system cache. That's insane. I have about 100mb. Think you need to look into that further.

---

### Post by howefield on 2016-08-29
Looking at the description for System Cache..

```
System
The system in general

Cache: Delete the cache
Clipboard: The desktop environment's clipboard used for copy and paste operations
Custom: Delete user-specified files and folders
Broken desktop files: Delete broken application menu entries and file associations
Free disk space: Overwrite free disk space to hide deleted files
Localisations: Delete files for unwanted languages
Memory: Wipe the swap and free memory
Recent documents list: Delete the list of recently used documents
Rotated logs: Delete old system logs
Temporary files: Delete the temporary files
Rubbish Bin: Empty the Rubbish Bin
```

I'd check the size of the logs in /var/log/*

Could be an underlying system issue that is filling up the log files and needs fixing/investigating..

```
sudo du -hs /var.log/
```

---

### Post by RobGoss on 2016-08-29
> **halogen2 said:**
> Well what exactly is a "system cache"?  I'm no expert but the only things I can think are the disk cache in RAM and the apt package cache (as already mentioned by Bashing-om).  Neither of those (not even both combined) would get that big would it?

Does Bleachbit give more details of what it thinks needs cleaned and if so can you please post that info here?

Bleachbit has this page that might provide more information on how Bleachbit cleans your system
[https://www.bleachbit.org/features]("https://www.bleachbit.org/features")

---

### Post by pfeiffep on 2016-08-29
> **danjswade said:**
> I've installed bleachbit as read it was a good package to do some housekeeping. I've run the preview and see I've over 100gb in the system cache. Am very new to Ubuntu and linux in general, so I was wondering if it's safe to delete these files and speed up my old laptop somewhat??

ThanksI've been using Bleachbit for 4+ years and use it regularly just prior to shutdown. 

Clear System Cache is enabled only when running as root on my config and hasn't caused me difficulties.

I didn't want to take the time to write scripts to keep my machine clean.

**Your mileage may vary!**

---

