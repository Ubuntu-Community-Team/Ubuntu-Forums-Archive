---
title: "No boot after motherboard replacement"
date: 2021-06-25
forum: General Help
---

### Post by martins54 on 2021-06-25
Hi,
My motherboard failed on a Packard Bell Acer computer, and I have had it replaced with an exact replacement.
I was running Ubuntu 16.04 desktop.
On powering up, all I get is a black screen, however, if I insert a 16.04 DVD boot disk, the computer can boot up in the "try installation" mode.  I can then see my hard drive, and it appears that all (most?) of my files are intact.
The BIOS appears to be right, first trying the hard drive to boot, then the optical drive.
Changing the SATA ports around makes no difference.
How can I make the computer boot from the hard drive, and restore my desktop and installed programs properly?
Many thanks
MartinS

---

### Post by tea for one on 2021-06-25
Just a few comments:-

16.04 has reached end-of-life and is unsupported (unless you have [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm))
Your old Ubuntu 16.04 may be installed as BIOS/MBR and your new motherboard may be [COLOR="#0000FF"]pre-set[/COLOR] for UEFI?
Double-check the BIOS/UEFI settings.

Use the live session to back-up your data.
Download the 20.04 version of your preferred Ubuntu flavour.
Make a USB boot disk
Install in UEFI mode with GPT
Restore your data

Here's some info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by martins54 on 2021-06-25
Hi,
Yes, the BIOS is showing UEFI as the only option in "Launch PXE OPROM", "Launch Storage OPROM", "Launch Video OPROM" and "Boot Filter", so I guess this is the root of the problem.
I am not an expert user, I went to Linux for Internet and Email - to get away from all the annoyances of Windows.
So - how do I do a "live session" backup?  Will this also backup all the emails and settings, which are stored locally using Thunderbird?
I have a few other installed programs such as dia for drawing - will I need to re-install these programs from scratch?
Many thanks
MartinS

---

### Post by dragonfly41 on 2021-06-25
Do you only have a single HDD containing Ubuntu 16.04?
How much unallocated space is there?
I am thinking that you might have to create a second partition into which you would install (say) Ubuntu 20.04.
Then you can transfer into 20.04 your old 16.04 data using UEFI.

---

### Post by tea for one on 2021-06-25
> **martins54 said:**
> So - how do I do a "live session" backup?  Will this also backup all the emails and settings, which are stored locally using Thunderbird?
I have a few other installed programs such as dia for drawing - will I need to re-install these programs from scratch?

Have you ever backed up at all?
If you have a recent daily back-up, then you do not have to worry.

I'm assuming that Windows is not installed as a dual boot.

As you previously mentioned that you can see your hard drive in a live session.
Repeat the boot procedure into a live session.
Insert another disk larger than your Ubuntu home/user directory.
Navigate to your home/user directory.
Copy home/user directory to second disk.

Thunderbird setting/emails will be preserved.

When you install a new version, you will have to re-install other software which is not contained on the installation disk.
The other software will probably be newer versions to be compatible with 20.04.

Please do not install 20.04 until you are happy that your back-up is OK.

---

### Post by martins54 on 2021-06-25
Hi,
As my disk was rather full, I decided to put a new larger disk in the computer.
Installation went OK, and 20.04 is running properly.
I have the previous disk on a SATA to USB converter, and have managed to transfer a lot of files across - though it seems some files are in slightly different places - for instance, desktop appears to be in home, rather than home/user - but that is not an issue.
However, Thunderbird is an issue, as when I open Thunderbird in 20.04, it is not finding my previous setups and emails.  The original drive is untouched - so where on the original drive are the Thunderbird files, and where do they need to go to on the new drive.
Many thanks for all your help.
MartinS

---

### Post by tea for one on 2021-06-25
Thunderbird profile  - good question.

Thunderbird development changed hands between 16.04 and 20.04 but I can't remember where the files were in 16.04.
[COLOR="#0000FF"].mozilla/Thunderbird possibly?[/COLOR]

In 20.04 it is the hidden file found in user directory [COLOR="#0000FF"].thunderbird.[/COLOR]

---

### Post by dragonfly41 on 2021-06-25
Forgot to mention .. you need to understand what hidden files to copy .. not only for Thunderbird but all apps (although in moving from 16.04 to 20.04 it is far preferable to reinstall apps).

[https://support.mozilla.org/en-US/questions/1065144#:~:text=Make%20hidden%20files%20and%20folders%20visible%20*%20http%3A%2F%2Fkb.mozillazine,Show%20hidden%20files%20and%20folders%22](https://support.mozilla.org/en-US/questions/1065144#:~:text=Make%20hidden%20files%20and%20folders%20visible%20*%20http%3A%2F%2Fkb.mozillazine,Show%20hidden%20files%20and%20folders%22).

[P.S.] If you have IMAP server you can import messages from your IMAP server.

---

### Post by martins54 on 2021-06-25
Hi,
I initially copied the files with drag and drop - not realising that there may be hidden files.  I am now trying copying the whole of the user directory in one hit - which presumably will copy hidden files as well.
I'm really only interested in Thunderbird files, I only had a few other apps on 16.04, and can easily re-install those.
How can one see the hidden files?
Thanks
MartinS

---

### Post by SuperFreak on 2021-06-25
press CTL H keys

---

### Post by dragonfly41 on 2021-06-25
grsync or FileZilla for file transfer allows you to select hidden files.
Important: Try a dry run first since you get varied results if you append/leave out the  / to filepaths.

For example you might get /home/home/username which is not what you want. Study the syntax.

---

### Post by martins54 on 2021-06-25
Hi SuperFreak,
How simple - thanks!
I am still copying, but can now see .mozilla and .thunderbird directories.
MartinS

---

### Post by martins54 on 2021-06-25
Hi,
I have now finished copying, and can see the following:
in home/user/.thunderbird/wi3pbdhl.default/Mail I can see my two email accounts (mail.xxx.com and mail.yyy.com) and in these directories I can see Inbox, Sent, Drafts etc. so I obviously have the data off the old drive - the files are large, a Gig of more, but there are several thousand emails stored.
However, when I open Thunderbird from the toolbar, it still asks me to specify email addresses, the contacts page is not populated, so it's presumably not found the data that is now in .thunderbird.
What to do next?
Thanks
MartinS

---

### Post by tea for one on 2021-06-25
Does .thunderbird/profile.ini point correctly to the default user?

Possibly, you may try logging out and in again?

---

### Post by oldfred on 2021-06-25
It used to be that I just had to start Firefox & Thunderbird & edit the profile.ini with my  profile.
But now there also is a installs.ini that seems to need editing also. 
 I typically delete the new default profile it creates once I know mine is working.

For first time in over 10 years I did have an issue.
I typically use most current LTS vesion of Ubuntu, now Kubuntu 20.04 and my profiles are from years ago. 
I did run a profile update that houscleaned a lot of old folders.
But when I used the profile in a newer test install of Ubuntu, it did some update in background. And then profile did not work in my main working install. I did have backup and had not really made any changes in test install, so showed backups important.

---

### Post by martins54 on 2021-06-25
Hi,
I seem to have two .thunderbird directories, one in home, and one in home/user.
The one in home was created this afternoon, whilst the one in home/user was last modified in April 2020.
The .default files have different names - in home n2b4y8eu, and in home/user wi3pbdhl - they are presumably randomly generated files names.
The one created this afternoon only has a file times.json in it - should I try copying all the files from wi3pbdhl to n2b4y8eu and see what happens, or is that too simplistic?
As mentioned before, in 20.04 the top level directories such as downloads, documents, videos etc seem to be in home, whilst previously they were in home/user.
Thanks
MartinS

---

### Post by dragonfly41 on 2021-06-25
The /home/ (without username) is incorrect.

Personally I only have four user folders in /home/

I would selectively move all into /home/username/.  But be very, very careful. Perhaps in small transfers not in one huge transfer which might corrupt your /home/username/ structure. A move might overwrite content.

You can also open Thunderbird with different profiles (as you can do with Firefox).
[COLOR=#000000]n2b4y8eu, and wi3pbdhl [/COLOR]

[https://support.mozilla.org/en-US/kb/using-multiple-profiles](https://support.mozilla.org/en-US/kb/using-multiple-profiles)

Much safer if you have backups.

---

### Post by martins54 on 2021-06-25
Hi,
Well, I have the backups, as the old disk is off the system at present.
When I installed 20.04, the Desktop, Documents, Downloads, Music, Pictures and Videos folders appeared in home, along with user.  In 16.04, the only folder in home was user.  Maybe I did something wrong in the install?  I can reinstall 20.04 easily enough.
Thanks
MartinS

---

### Post by martins54 on 2021-06-25
Hi,
SUCCESS!!
The problem seemed to be that I had inadvertently created a file of home/user/user, and was putting things into that.
I transferred .thunderbird from the old disk to the new disk in home/user, and also transferred .mozilla from the old disk into home/user.
I now have Thunderbird showing all my old emails, and able to pick up new ones, and also Firefox is now showing all my bookmarks etc.
Many, many thanks for all you help.
Best Wishes
MartinS

---

### Post by dragonfly41 on 2021-06-25
Please mark thread as solved. Top of this page > thread tools.

---

### Post by tea for one on 2021-06-25
> **martins54 said:**
> Hi,
SUCCESS!!
The problem seemed to be that I had inadvertently created a file of home/user/user, and was putting things into that.
I transferred .thunderbird from the old disk to the new disk in home/user, and also transferred .mozilla from the old disk into home/user.
I now have Thunderbird showing all my old emails, and able to pick up new ones, and also Firefox is now showing all my bookmarks etc.
Many, many thanks for all you help.
Best Wishes
MartinS

Splendid - Well done
Onwards and upwards

As requested by [COLOR="#0000FF"]dragonfly41[/COLOR] [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Paulgirardin on 2021-06-28
For future reference: /home/$user/.thunderbird/xxxxxx.default-release (the xxxxx will be a string of characters)  is where all the settings and mail reside.
save this directory from your old installation.
After a new install, open Thunderbird and then close it.
In your file manager go to /home/$user/.thunderbird/  and rename "xxxxxx.default-release" to "oldxxxxxx.default-release" and copy your saved xxxxxx.default-release into /home/$user/.thunderbird/    and rename it to the same name as the new "xxxxxx.default-release" was before you appended the "old" to it.
To clarify:
ogysrck4.default-release is the one in the new Thunderbird
pscketx3.default-release is the one you saved with all your mail and settings in it.
ogysrck4.default-release is renamed: oldogysrck4.default-release
pscketx3.default-release is copied into /home/$user/.thunderbird/
pscketx3.default-release is renamed ogysrck4.default-release.
Now you can start Thunderbird and it will be exactly as you had it on you old system.

It used to be that all you needed to do was copy the "default" folder but some changes were made in how it all works that require the renaming of the "xxxxxx.default-release" folders or Thunderbird spits the dummy

This is what I do after each fresh install of Ubuntu

---

