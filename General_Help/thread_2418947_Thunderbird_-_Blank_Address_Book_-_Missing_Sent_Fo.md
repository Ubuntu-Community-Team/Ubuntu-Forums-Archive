---
title: "Thunderbird - Blank Address Book - Missing Sent Folder"
date: 2019-05-14
forum: General Help
---

### Post by electrosteam on 2019-05-14
Lubuntu 18.04.2 LTS on a 2005 tower.

During the last few days I have implemented the daily offered upgrades and, chasing data on an external hard drive, used the Live CD to interrogate drive parameters with no known deliberate disc activity.

I now discover the Thunderbird Address Book is blank and there is no Sent folder.

Any suggestions on possibly recovering Addresses and/or Sent emails ?

What precautions are recommended for future daily upgrades and/or Live CD usage ?

John

---

### Post by Rex Bouwense on 2019-05-14
The sent information is likely still on the mail server depending upon how you set up Thunderbird.  I too use Thunderbird and during set up I chose POP but also chose to retain copies of messages on the server which is an option

---

### Post by ajgreeny on 2019-05-14
You seem to be suggesting that email addresses that you had in the T'Bird addressbook have been deleted by updates to your system and T'Bird itself, though I am not completely sure what you mean.

Can you give us more detail of what has been upgraded; is this a normal system upgrade, or are you talking, for example, of an upgrade from 16.04 to 18.04.

I can see no way that upgrading either the OS or T'Bird would lose all your email addresses in the addressbook, as they are stored in your home folder, and would all remain even if you uninstalled T'Bird.

---

### Post by electrosteam on 2019-05-14
Rex and Al,

I sent out a group email 3 days ago without problems, the Address Book had about 80 contacts and the Sent Folder about 50 emails.

Over the next few days the only changes were regular daily notifications for upgrades to my Lubuntu 18.04.2 LTS and the installation of GParted.
Gparted was opened, then closed without any activity.

The other activity was the use of the installation CD to enter some commands suggest by Rubi1200 while we tried to mount a laptop hard drive through a USB adapter cable. [https://ubuntuforums.org/showthread.php?t=2418896](https://ubuntuforums.org/showthread.php?t=2418896)

Gparted on the Live CD seemed to have been included in the release as I did not have to install it to perform one action by Rubi1200.
No commands were deliberately entered on the Live CD that were targeted at sda.

My suspicion falls on the Live CD sessions.
Is it normal for GParted to show as available on the Live CD GUI, but not in the actual installation ?

Since first reporting this issue, I have also discovered the Mozilla Bookmark folder is empty.

Busy for a week, but I will test by populating the TB Address Book, sending a few emails and adding a few bookmarks.
Then repeat all the suggestions by Rubi1200 with a Live CD, and see what happens.

Report back in about a week.
John

---

### Post by ajgreeny on 2019-05-15
Some strange things going on here, and I am also wondering what the gparted activity did, though you say it was never pointed at the hard disk.

You say the Mozilla Bookmark folder is empty; what do you mean by that as there is no folder called bookmarks in the hidden .mozilla configuration folder in your home; do you simply mean that you have lost all your bookmarks?
In that hidden .mozilla folder there should be a folder called **~/.mozilla/firefox/qn4bdmr0.default/bookmarkbackups** with a number of **.jsonlz4** backup files so you may be able to restore bookmarks from that.

Are all your data files still available to you, ie, documents, music, videos, pictures, etc etc, or have you lost all your personal files as well?

PS:
Yes it is normal for gparted to be on the live system but not installed on the hard disk, so no problem with that finding of yours.

---

### Post by Rubi1200 on 2019-05-15
To all concerned, this is the thread John is referring to:
[https://ubuntuforums.org/showthread.php?t=2418896](https://ubuntuforums.org/showthread.php?t=2418896)

I do not see how using GParted on the liveCD or fsck could have caused problems with Thunderbird but who knows...?

---

### Post by ajgreeny on 2019-05-15
> **Rubi1200 said:**
> To all concerned, this is the thread John is referring to:
[https://ubuntuforums.org/showthread.php?t=2418896](https://ubuntuforums.org/showthread.php?t=2418896)

I do not see how using GParted on the liveCD or fsck could have caused problems with Thunderbird but who knows...?
Yes, I had already looked at that thread, and like you, I do not see how that action could cause the problems you are seeing.

However, if you mount an external drive using a USB adapter cable it is possible that the folder where you mounted that drive is now unavailable to the OS if you did not unmount the drive properly before removing it.

Tell us in detail what you actually did when trying to mount that drive, and the mountpoint you attempted to use; it may give us some clues.

---

### Post by electrosteam on 2019-05-15
Rex, Al and Rubi1200,

Mea culpa, my sincere apologies.

Please don't hold it against me when assessing possible future problems.

I have two towers operating and I "thought" I had good management of what I was doing - wrong !.

I have now assessed which tower is worth keeping as my work station, the other will be relegated to back-up duties only.

Apologies again,
John.

Note: I will mark the thread as 'Solved', but that seems inadequate. We need an allocation for misleading threads.

---

