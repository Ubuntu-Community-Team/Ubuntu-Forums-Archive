---
title: "Windows XP on C:\ Ubuntu on D:\ and Thunderbird on H:\ for both?"
date: 2006-08-06
forum: General Help
---

### Post by ELMIT on 2006-08-06
Hi,

I have reserved 50G on my hard disk for Ubuntu and on C: is my XP installation. I have installed on H:\ all the data for Thunderbird and Firefox. C:\ and H:\ is ntfs!

I would like to be able to boot from XP and from Ubuntu and still use both times the same data. How can I do that?


bye

Ronald Wiplinger

---

### Post by noof on 2006-08-07
It's easier to use fat32 on the shared partition. fat32 works out of the box with ubuntu, ntfs requires some work. I actually tried to do the exact same thing as you some time ago. The problem was that the FF or TB-settings had to contain some absolute directories (like c:\program files\firefox\...), so I never got it to work.

---

### Post by David Corrales on 2006-08-07
I use a FAT32 partition and both linux/windows thunderbirds can share the same data. What I do is point the file at a directory in the shared partition and that's it.

---

### Post by skirkpatrick on 2006-08-07
I've been doing this for quite some time on my work laptop for Thunderbird and Gaim and it should work for Firefox as well.  Note it's been a very long time since I did this and that this will be a real pain if you already have emails and addresses:).

1 ) Your shared drive/partition (H) should be a FAT32 drive/partition.

2 ) Make sure your Windows TB has all your emails and addresses.

3 ) Create a directory on your shared partition to hold your files and copy your Windows profile to it.  If your name was Scott, your profile would be located at *C:\Documents and Settings\Scott\Application Data\Thunderbird\Profiles\* and have the extension *.Default User*.

4 ) Close TB and go into Profile Manager.  Create a new profile and when you have the option, tell it that the profile will be stored where you saved it on the shared partition.

5 ) Open TB and make sure you still have access to everything.  You will have to go into each account and under Server Settings, change the Local Directory to its new location.

6 ) In Ubuntu, let TB create a profile, if you haven't already.

7 ) Open the commandline window and go to the directory where TB keeps your profile:
**cd ~/.mozilla-thunderbird**

8 ) Find your profile directory and change to it.  Your profile directory probably ends with a *.default* extension:
**ls**
**cd t258zpws.default**

9 ) Delete the following files (note that this will wipe out your Ubuntu address book, history, and stored email):
**rm abook.mab history.mab**
**rm -fR Mail**

10 ) Create symbolic links to the same files on the shared partition (yours will be different than mine):
**ln -s /media/FAT32/SharedAppData/Thunderbird/Profiles/Scott/abook.mab abook.mab**
**ln -s /media/FAT32/SharedAppData/Thunderbird/Profiles/Scott/history.mab history.mab**
**ln -s /media/FAT32/SharedAppData/Thunderbird/Profiles/Scott/Mail Mail**


Once everything is working, you can delete your old profile on the C: drive in Windows.

I don't actually link the Mail directory as I use IMAP so the email and folders stay on the server and I don't have to think about it.  Part of the reason, if I remember correctly, is because it seemed to take more effor to keep the email folders in sync between Windows and Ubuntu.

---

