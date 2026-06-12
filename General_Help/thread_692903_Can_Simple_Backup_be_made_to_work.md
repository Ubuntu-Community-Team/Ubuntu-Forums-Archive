---
title: "Can Simple Backup be made to work?"
date: 2008-02-10
forum: General Help
---

### Post by Roger D on 2008-02-10
Hi 

Hi

I'm trying to implement a very simple backup strategy. The idea is that I will store my home directory (/home/roger) in a folder on my external hard disk (/media/"My Book"/backups/roger_backup). Then, should my regular PC fail for any reason, I will restore the folder on my external hard disk into /home/roger on my spare PC. In this way I hope I will be able to carry on working while my regular PC is fixed. Sounds simple.

There are, I know, no end of ways of doing backups in Ubuntu - I've been reading various postings for months now, many of which depend on terminal-based tools like tar, dar and rsysnc. For anyone who enjoys getting under the hood of your OS, I can see that these are absolutely brilliant; however, I'm running Ubuntu as a working desktop OS, i.e. as an alternative to Vista or Leopard, and I'm adamant that something as basic as backup has to be addressable via a fairly easy to use GUI-based tool. I have tried using rsysnc, but while the dry run seemed OK, everything fell over when I tried it for real.

I seem to have a choice of two tools: 'Home User Backup', which is restricted to backing up home directories (so fine in principle) and the more sophisticated 'Simple Backup'.

'Home User Backup' fails at the first post I'm afraid - it doesn't detect my mounted external hard disk.

Here's how I get on with 'Simple Backup':

1 I opt for 'Use custom backup settings', and click on the 'include' tab.

2 Click on '/home'. Not quite sure what to do next, but since 'roger' is a directory within 'home', I click on the 'Add Directory' button. Now I can see all the folder within 'roger', but I just want 'roger'. Click on 'home', and now I can see the folders of all the users on my system, including 'roger' - looks like progress. I'd like to see a 'select' button at this point, but click on 'open' as the next best thing.

3 Progress - I'm back in the 'include' tab, and I can see '/home/roger/ added to the list of directories. I move the cursor down to highlight '/home/roger'. 

4 Have I selected this directory for backup? I'm not sure. I assume I have, and click on the 'Destination' tab. Without too much difficulty, I manage to select '/media/"My Book"/backups/roger_backup' as the destination. Should be home and dry

5 Click on the 'Backup Now' button. I'm told a backup run is initiated in  the background, and the power light on my hard disk blinks a few times - looking good, as they say.

6 Not sure how long this should take, as others have said, a progress bar would be a great idea, so I leave my PC for 10 minutes.

7 There's a new folder in 'roger-backup' with today's date and the current time and the extension ful - looking really good.

8 I eject, and then remount, my external hard disk - just to make sure that the file is actually written to the disk - the file is 2.9MB, something wrong here, my home directory is actually 11.2 GB. Inside the folder there are five files: excludes, flist, fprops, packages and ver, none of which makes much sense.

Can only assume that I haven't actually selected my home folder, or I didn't leave my PC for long enough.

Any ideas anybody, and please, no offers of scripts. I just want to know whether or not Simple Backup can be made to work, and I want to keep this  thread focused on this simple question.

Roger D

---

### Post by Keith Hedger on 2008-02-10
If all you want is a simple backup of your home folder and really don't want to use the command line why not just right click on it and select "Create Archive" u can then select what to call it and where to save it

---

### Post by Roger D on 2008-02-10
Yes, but how do I restore it? I'm pretty sure I can't just copy the archive to /home on my spare PC, right click and slect 'extract here'. I seem to remember trying this, and I get told I'm not allowed to do it. The reason I'm asking about Simple Backup is that it's suppose to work, and the restore procedure looks straightforword.

Roger D

---

