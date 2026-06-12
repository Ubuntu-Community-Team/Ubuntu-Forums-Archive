---
title: "Cinnamon, Nautilus, Nemo crashed at the same time.."
date: 2022-03-11
forum: General Help
---

### Post by Shobuz99 on 2022-03-11
Hi all,

I wasn't sure where to post this. I hope here is okay.

Yesterday I was trying to create a boot-able 20.04.4 CD from the iso in my Downloads folder.

I didn't even get to select the .iso file to Brasero and burn the image.

My system crashed. Cinnamon, Nautilus and Nemo ALL crashed at the same time.

However, I had just backed up my HDD the day before.

I ran the Backup (Deja-Dup) and selected 'Restore'. 
It seemed to be going okay until it came up with an error that said the **Restore Failed**.
There was a mismatch that I *think* had to do with the Downloads folder...maybe not..
I'm sorry that I didn't capture an image of the error message for the Restore failure.

My next option was to try to run the recovery version of the 5.4.0-104-generic that I had ALSO updated the day before.

The recovery ran fine, but didn't give back my Downloads folder.
I don't think Nautilus or Nemo were running; but the Cinnamon environment was working fine.

Today I tried going back to the previous 5.4.0-100-generic.
Although it booted properly with no errors, my Downloads folder is still missing.
I have no idea how many files I lost that were in the Downloads folder.

error message from /vars/crash:

[rick@rick-HP-EliteBook-8460p:~$ ls -l /var/crash
total 8672
-rw-r----- 1 rick     whoopsie  204052 Mar 10 19:28 _usr_bin_cinnamon-launcher.1000.crash
-rw-r--r-- 1 rick     whoopsie       0 Mar 10 19:28 _usr_bin_cinnamon-launcher.1000.upload
-rw------- 1 whoopsie whoopsie       0 Mar 10 19:30 _usr_bin_cinnamon-launcher.1000.uploaded
-rw-r----- 1 rick     whoopsie 4432973 Mar 10 19:09 _usr_bin_nautilus.1000.crash
-rw-rw-r-- 1 rick     whoopsie       0 Mar 10 19:09 _usr_bin_nautilus.1000.upload
-rw------- 1 whoopsie whoopsie       0 Mar 10 19:09 _usr_bin_nautilus.1000.uploaded
-rw-r----- 1 rick     whoopsie 4237546 Mar  9 11:21 _usr_bin_nemo.1000.crash
-rw-r--r-- 1 rick     whoopsie       0 Mar 10 19:16 _usr_bin_nemo.1000.upload
-rw------- 1 whoopsie whoopsie       0 Mar 10 19:17 _usr_bin_nemo.1000.uploaded ]


I am running Ubuntu [U]18.04 bionic (x86-64) on an HP Elitebook 8460p Intel Core i5-2520M CPU @ 2.50 GHz x 2
with 7.7GiB memory and 250GB storage HDD.[/U]


My question is, knowing all this, should I still try to upgrade to 20.04 LTS?
If it is successful, will a *new* Downloads folder be created?

I'm resigned to the fact that the Downloads folder is gone and not retrievable...unless there IS a way to retrieve it?

I hope someone here has some advice that I can go forward with.

Thank you for your help.

Rick (shobuz99)

---

### Post by TheFu on 2022-03-11
Do your backups include ~/Downloads?  If not, then it is probably gone. Have you looked for some of the files across the entire file system?
I consider ~/Downloads as a temporary location, not for permanent storage. Other programs do stuff in that directory. 

If ~/Downloads/ is part of your workflow, that's fine. Use what works for you.

There's nothing special about the Downloads directory.  **mkdir ~/Downloads** will make it if it is gone.  Any program, like a file manager, can trivially delete it too. It is just a directory like any other. It isn't actually required. It can be named something else or download files somewhere else.  There are settings that can be changed to the new name - logout and login for the new setting to take effect. Or not. They are XDG variables.

To upgrade or not?  If a system is having issues, doing an upgrade won't fix them. Often, the upgrade will fail or make them worse, but not always.  Backup any files you can't lose (be 100% certain each can be restored), then do a full, fresh, new 20.04 install. Format each file system in the new install. This will remove all the old cruft left in settings and configs which can cause problems, especially if you've changed DEs over the years. If you do an overlay install, the cruft will remain, likely to cause problems.

---

### Post by Shobuz99 on 2022-03-11
Thank you TheFu, for your reply.

As I said, I ran Backup (Deja-Dup) and selected 'Restore'.
It seemed to be going okay until it came up with an error that said the *Restore Failed*.

So I didn't get to *see* the back-up fully restored...ergo, to answer your question, Yes my backup included ~/Downloads *originally*.

As far as I can recall, every Ubuntu distro that I've used since Ubuntu 6.10 (Edgy Eft, the fifth release of Ubuntu) had a ~/Downloads folder included
with the install...as a temporary folder or not. I may be wrong. 2006 was 16 years ago, and Ubuntu 6.10 Edgy Eft was the first version I started using.

I planned on upgrading from 18.04 to 20.04 three days ago.
I purposely created a full fresh backup before I opened *Brasero* and attempted to burn a CD.
I know the risks.
What I didn't know was what I should do if I had a crash, ran a Restore and it failed!
I wanted to know if the "cruft" would also be backed up, if I ran another full fresh backup and then tried creating a 20.04 image to upgrade from 18.04?

I did not / do not plan on doing an overlay install.

Again, I backed up the whole drive the day before.
I planned on doing a *restore* AFTER I did a fresh install of 20.04.

So let me rephrase my question: 
Will running a new full backup on the 18.04, carry any "cruft" with it when I run a restore to the fresh 20.04??
If not, then I assume I shouldn't have any problems related to the the initial Crashes...Correct?


Thanks again for your help...TheFu.

---

### Post by TheFu on 2022-03-11
There's no magic. The settings in the backup tool control what it tries to backup as spelled out in the different directories included. But if it cannot restore using said backup(s), it is useless and a different tool should be used.  
If the backup directory settings include where cruft is stored, then the cruft will be saved and when restored, it will be brought forward.

DejaDup used to support selected directory and file restores. Has that changed?

If the backups can be validated by checksum validation, see if that works.  If not, I'd look at the backup storage for failures.

---

### Post by Shobuz99 on 2022-03-13
I discovered why the Restore failed. It was a powered USB hardware issue on my laptop.
I found that out when I tried running a fresh backup with a different external drive.
Once I switched to another USB port that isn't "powered", the backup ran flawlessly and finished.
Now my plan is to change the BIOS in the laptop, so that it defaults to the CD/DVD drive on boot.
Then I can wipe out the HDD, install a fresh 20.04.4 LTS and then restore from the backup.
I know that ALL upgrades can have issues and nothing is guaranteed to go 100% smooth;
however, I've had many good upgrades go without issues or "cruft" (That's an interesting word, btw)
interfering with success.

BTW...You mentioned running a checksum. I thought Deja Dup aka "Backup" ran its own Checksum?
If you mean running a checksum from an external app, would that be a software pkg on the 18.04.3 version?
If that is available, then I'll do that, if I can. 

Otherwise, if there is anything you think I missed here, please tell me.
Once I complete the upgrade and restore the data to Ubuntu 20.04.4 without any major setbacks,
| will close this thread.
Thanks again for your help TheFu.
It is appreciated.

Rick (shobuz99)

---

### Post by TheFu on 2022-03-13
Please use the "thread tools" button near the top of the page to mark this thread SOLVED. That helps everyone in the community. You've already posted what the root issue was, which is extremely helpful too.

---

### Post by Shobuz99 on 2022-03-27
I got my Downloads folder back with ALL files included. I found it in my /home/rick/.cache folder.
Thanks again for all your help.
I'll be upgrading to 20.04 LTS soon!

Shobuz99

---

