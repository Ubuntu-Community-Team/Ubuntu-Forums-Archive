---
title: "Deja-Dup fails restore to new 14.04 on new HDD"
date: 2016-06-13
forum: General Help
---

### Post by Shobuz99 on 2016-06-13
I have an issue with Deja-Dup that I cannot find anywhere on the Ubuntu Forums.

***** Background: I backed up my 14.04 160GB drive using Deja-Dup (aka Backup) on a Dell Inspiron 1525.

***** Clean installed Ubuntu 14.04 from live CD to my NEW 250GB drive, and the install went as expected.

**Note:** I had originally encrypted the 160GB drive with a password; but also created a logon password using the keyring.
The passwords are not similar in any way.

**Note2:** When I clean installed the new 250GB with 14.04, I selected the same HDD encrypt process using the same exact password
that I used on the 160GB. I also created the same keyring password for the 250GB that I used on the 160GB.
And they are dissimilar in the same way they are dissimilar on the 160GB.

******I then ran the Backup Deja-Dup application and intended to restore the previous drive's contents to my new drive.
The process began, properly restoring a list of files as it is supposed to; but within a minute, it abruptly stopped,
the screen went black, and the logon screen appeared asking me for my keyring password to the desktop.
I obliged and it brought me to the desktop. Nothing appeared to have been restored from the Deja-Dup action.
Moreover, the 4 icons I chose to put on the desktop instead of the launcher: Nettools, Terminal, Disks, and Backup,
were now scattered instead of aligned with each other at the top of the desktop.

******* Meanwhile, the external backup drive that I stored the backup of the 160GB appears to be trying to access and complete the restore.
 (*External HDD light turns red then back to green, slowly; but no information seems to be transferred, and the Deja-Dup program is not loaded and running.*)
But it's not doing anything that I can see. 

*********I'm at a loss as to why the Restore will not complete. I'm just trying to restore a 14.04 from one drive (160GB), to a 14.04 of another drive (250GB)
that has a clean install of 14.04 already on it.
Does anyone have any ideas where I can troubleshoot this failure? What errors could I have made during the backup process of the 160GB drive?
Please let me know if there is more information you require.

**UPDATE:** I have wiped my 250GB drive and started over again. I clean installed Ubuntu 14.04 LTS on the drive, downloaded the updates
so that I had the latest linux-generic kernel and files installed too.
Then I went to the Deja-Dup and started to Restore the data & files that I backed up from the 160GB drive (that's about to die).
It began as expected, asked me for the password to restore and then began. The lights were flashing, the list of restored files were growing...
and then it HUNG... no activity other than an occasional flash from the external drive where the backup is stored and the 250GB drive with Ubuntu.
I waited 10 minutes. No change. I hit "resume later". No change. I hit cancel. No change. I exited "Backup" and examined the files list for updates.
There were NONE. Nothing changed and I can't get this to complete! I don't even know yet if there is a log file I can look at for error messages or failures,
not that I got any, anyway..but I have no other ideas.. Can someone please advise here???
 
Thank you for your help,
Shobuz99

---

### Post by Shobuz99 on 2016-06-24
Bump

---

### Post by Shobuz99 on 2016-06-26
Bump

---

### Post by Shobuz99 on 2016-07-06
It's been three weeks since I first posted this. No one has offered any help. 
I BUMPed it only twice, so I wasn't annoying. It didn't matter. No one has offered any help at all.
I'd like A Moderator to expunge and delete this thread, because it doesn't help ANYONE.

Thank you Ubuntu Community.

Rick Shobuz99

CC: [http://ubuntuforums.org/member.php?u=27747](http://ubuntuforums.org/member.php?u=27747) 

       [http://ubuntuforums.org/member.php?u=171805](http://ubuntuforums.org/member.php?u=171805)  

      [http://ubuntuforums.org/member.php?u=1256508](http://ubuntuforums.org/member.php?u=1256508)

---

### Post by QIII on 2016-07-06
Just a moment.  Wait.  I think I see the problem here.

Yes.  Yes.

Instead of bumping at twelve hour intervals, you allowed this to sink to the bottom of the pile for a week or so at a time and expected others to find it there.

Alas.  That is hardly the fault of the community.

---

### Post by pauljw on 2016-07-06
I know you're frustrated, Rick.  This is the first I noticed your post, probably true for many others as well.  I'm no expert, but I'm not sure a backup program is best for the job at hand.  I would go for Clonezilla.  It will restore to bare metal, even to a larger partition than the original drive.  Some or most backup programs balk at that.  Download Clonezilla iso, make a bootable dvd or usb, install your old drive, boot your system with Clonezilla and clone the drive to your backup drive.  Install your new drive and use Clonezilla to recreate your system on the new drive.

Hope this helps, good luck.
Paul

---

### Post by Shobuz99 on 2016-07-06
Why would I have had to continue bumping it more than in 12 hour intervals? 
Is that an Ubuntu Forum POLICY??? I never read any such thing anywhere...unless you updated Ubuntu Policies recently?
That makes no sense. 
If you don't want to help, just say so. No reason to be sarcastic about it.
I've been an Ubuntu user since 2006. I know the drill. Your comment is uncalled for.
I was asking for help, not begging.

Rick Shobuz99

> **pauljw said:**
> I know you're frustrated, Rick.  This is the first I noticed your post, probably true for many others as well.  I'm no expert, but I'm not sure a backup program is best for the job at hand.  I would go for Clonezilla.  It will restore to bare metal, even to a larger partition than the original drive.  Some or most backup programs balk at that.  Download Clonezilla iso, make a bootable dvd or usb, install your old drive, boot your system with Clonezilla and clone the drive to your backup drive.  Install your new drive and use Clonezilla to recreate your system on the new drive.

Hope this helps, good luck.
Paul

Thanks Paul. I already have Clonezilla. I had made the backup with Deja-Dup a while before I burned the Clonezilla iso file.

I appreciate your friendly response, anyway. unlike QIII's ineloquent sarcasm..

> **QIII said:**
> Just a moment.  Wait.  I think I see the problem here.

Yes.  Yes.

Instead of bumping at twelve hour intervals, you allowed this to sink to the bottom of the pile for a week or so at a time and expected others to find it there.

Alas.  That is hardly the fault of the community.

Forum rules Purpose..First paragraph:

The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. 
**Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.**

---

### Post by pauljw on 2016-07-06
Well, if that old 160G drive is still functioning, I would do as I said above, put it back in and use Clonezilla to image the drive.  I think it's your best bet.

Paul

---

### Post by lisati on 2016-07-06
> **Shobuz99 said:**
> Thanks Paul. I already have Clonezilla. I had made the backup with Deja-Dup a while before I burned the Clonezilla iso file.

I appreciate your friendly response, anyway. unlike QIII's ineloquent sarcasm..

From the forum [code of conduct]("http://ubuntuforums.org/misc.php?do=showrules"): 
> Respect the Forum Staff: We provide a service in our free time to keep the forums running efficiently. We are all volunteers. Feedback is welcome in Forum Feedback & Help , this is also the place to request assistance with forum software issues. If you believe an error has been made in moderation or other staff actions, please post politely in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") and help us understand your perspective.

---

### Post by wildmanne39 on 2016-07-06
In truth people probably do not know the answer, there is a lot of trouble with restoring especially when restoring to another drive and it has encrypted files. 

I recently restored to a new drive but it took a few days to figure out how to do it and it was still just a work around it did not ork like it was supposed too. 

I had to use google a lot and then ended up coping all my files from the back up drive to my home folder on my new drive by opening my file browser with privileges, mine is caja both the destination drive and the old drive had to have privileges then I could restore. Google the exact error you get then if you need help post back. I really do not know anything about encrypted files though.
Thanks and I hope this gets sorted soon.

---

### Post by Shobuz99 on 2016-07-06
> **pauljw said:**
> Well, if that old 160G drive is still functioning, I would do as I said above, put it back in and use Clonezilla to image the drive.  I think it's your best bet.

Paul

I'm doing just that as we speak... Thank you. I appreciate it.

I've got the How-to-Geek Clonezilla instructions as a guide.
I plan on cloning the entire 160GB disk to 250GB disk that's connected via USB.
I want to be sure to get all of it, including the 'swap' drive, etc.

Thanks again. :-)

Rick shobuz99

---

### Post by pauljw on 2016-07-06
You're welcome.
Paul

---

### Post by Shobuz99 on 2016-07-07
Well....Clonezilla will not finish. The 160GB drive has some bad sectors. It will not fix the problems and fails to complete the disk to disk cloning.
I'm not sure what to do now. I'm in trouble.....

---

### Post by Shobuz99 on 2016-07-08
** UPDATE!!! **
Alright, after this, no more Bumping or Thrashing from me. I've solved my problem. I didn't use Clonezilla to do it.
I decided that the 160GB drive is beyond salvation, unless I use gParted to move around partitions and isolate "bad sectors".
i don't have that kind of time nor do I want to take a risk that I destroy the drive before I fix it.
So, I went back to some other posts, and saw a recommendation from a Moderator in a different thread to do the following:

[LIST]
Do a fresh back-up of the bad drive.[/LIST]
[LIST]
Install a clean Ubuntu distro to the new drive. Get all updates and bring it up to as recent as possible.[/LIST]
[LIST]
Create a folder on the new drive and leave it empty, naming it as 'restore" or whatever.[/LIST]
[LIST]
Restore the fresh backup of the bad drive to the folder just created.[/LIST]
[LIST]
Gradually copy folders and use Synaptic Pkgs to bring the restored files in to use.[/LIST]

This is what I did. i am typing this from the laptop I did this to, and it is working fine.
I should've done this originally, like it was recommended to me by a previous Moderator in a different thread

Thank you ALL for your help. I Do appreciate it.
This thread is already marked <Solved>. And it will stay that way.

Rick Shobuz99

---

