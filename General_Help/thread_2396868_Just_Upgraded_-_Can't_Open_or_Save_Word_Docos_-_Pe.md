---
title: "Just Upgraded - Can't Open or Save Word Docos - Permissions Error"
date: 2018-07-22
forum: General Help
---

### Post by skyesharica on 2018-07-22
Hi Linux Friends,
Please help me.  I am writing a book.  I have just done a clean install of Ubuntu 18.04 LTS.  I can't get to my book files in Word, LibreOffice.  The PC keeps telling me that the file can't be opened because it is Read Only - and so I open a copy.  And then the computer can't save a copy for my use.  It keeps giving error messages.  No matter how often I try to change the Permissions to Read and Write, it keeps changing back to Read Only.  So I am up the creek.

---

### Post by yancek on 2018-07-22
If this is a new install, where were/are your book files?  On a separate hard drive, pendirve?  What filesystem type on the partition on which you have your book files.

There are a number of reasons why you would get a read-only error so more info is needed.  One possibility is the need for a filesystem check but this all depends upon where the files are.

---

### Post by skyesharica on 2018-07-22
> **yancek said:**
> If this is a new install, where were/are your book files?  On a separate hard drive, pendirve?  What filesystem type on the partition on which you have your book files.

There are a number of reasons why you would get a read-only error so more info is needed.  One possibility is the need for a filesystem check but this all depends upon where the files are.

Thanks yancek.  The book files are on the desktop - transferred from a disk and a flash drive.  I don't know why you mean by "filesystem type on the partition" but I found this under "Permissions":  "Folder (inode/directory)".  I've never heard of a filesystem check.

---

### Post by ajgreeny on 2018-07-22
On your Ubuntu system where the docs are sitting run command ```
ls -l Desktop
``` and show us the output please.
This assumes they are in the Desktop folder of your /home folder.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by skyesharica on 2018-07-23
> **ajgreeny said:**
> On your Ubuntu system where the docs are sitting run command ```
ls -l Desktop
``` and show us the output please.
This assumes they are in the Desktop folder of your /home folder.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

```
mofa511@mofa511-All-Series:~$ ls -l Desktop
total 49208
-rw-rw-rw- 1 mofa511 mofa511    32938 Nov 23  2017 '$5 off from a Hair Moisturizer - Amcal Chemist.eml'
-rw-rw-rw- 1 mofa511 mofa511    22200 Jul 21 15:31 '7.  July.ods'
-rw-rw-rw- 1 mofa511 mofa511    42204 Jul 20 18:07 'Amaysim Expires 16 August - Pre Pay $10 For Longer Than 28 Days.png'
drwxr-xr-x 2 mofa511 mofa511     4096 Jul 17 22:27  Baptism
drwxr-xr-x 2 mofa511 mofa511     4096 Dec 28  2017 'Bible and Homosexuality etc'
-rw-rw-rw- 1 mofa511 mofa511  1290552 Dec  1  2017 'Birth Certificate - I.D..pdf'
-rw-rw-rw- 1 mofa511 mofa511    13824 Jul 18 11:47 'BODY MEASUREMENTS.xls'
-rw-rw-rw- 1 mofa511 mofa511    30359 Dec 27  2014 'COMMONWEALTH BANK.odt'
-rw-rw-rw- 1 mofa511 mofa511     8993 Jul 20 16:16 'Defaming Details.docx'
-rw------- 1 mofa511 mofa511    31441 Jul 23 15:30 'Defence Jobs.eml'
-rw-rw-rw- 1 mofa511 mofa511    19215 Jul 20 16:20 'Diet Calculations.odt'
drwxr-xr-x 2 mofa511 mofa511     4096 Jul 30  2015 'Driving Instructions'
-rw-rw-rw- 1 mofa511 mofa511     3765 Jul 18 15:09 'Fiona - Chronic UTI.eml'
-rw-rw-rw- 1 mofa511 mofa511    26457 Jul 23 00:53 'Fortnightly Budget.odt'
-rw-rw-rw- 1 mofa511 mofa511    20432 Jun 13 19:30 'GO MASTERCARD.odt'
drwxr-xr-x 2 mofa511 mofa511     4096 Jun 10 21:56 'Goodlife Pass'
-rw-rw-rw- 1 mofa511 mofa511    31419 Mar 24  2017 'I Have Costly Delivery Saver.png'
-rw-rw-rw- 1 mofa511 mofa511   322427 Apr  6 15:51  Jesus.png
-rw-rw-rw- 1 mofa511 mofa511   287900 Jul  1 23:39 'Kung Fu Map - From Nerang Railway Station.jpeg.odt'
-rw-rw-rw- 1 mofa511 mofa511   256065 Jul  1 23:21 'Kung Fu.odt'
-rw-rw-rw- 1 mofa511 mofa511   913704 Jun 20 18:12 'Letter re NBN 18-06-18.pdf'
drwxr-xr-x 2 mofa511 mofa511     4096 May 16 16:34 'Library Notices'
-rw-rw-rw- 1 mofa511 mofa511     8660 Nov  9  2015 'Logan City Council Libraries Item Now Available.eml'
-rw-rw-rw- 1 mofa511 mofa511    13359 Jan 13  2015 'Macquarie Cash XL Log On Details.odt'
-rw-rw-rw- 1 mofa511 mofa511 42242928 Sep 20  2017 "Mother Teresa's Quotes.pdf"
drwxr-xr-x 6 mofa511 mofa511     4096 Jul 18 13:25 'New Body Corporate'
drwxr-xr-x 2 mofa511 mofa511     4096 Jul 16 13:03 'New Electricity Provider'
drwxr-xr-x 3 mofa511 mofa511     4096 Jul 22 13:50 'NEW STOVE & RANGEHOOD'
drwxr-xr-x 2 mofa511 mofa511     4096 Jul 10 16:35 'PCYC Gym + Fitness Classes'
-rw-rw-rw- 1 mofa511 mofa511    24210 Jul 19 11:52 'Phone Donna Sinclair of Gold Key B.C..eml'
drwxr-xr-x 5 mofa511 mofa511     4096 Jul 22 14:31 'Photos To Put In Book - Most Images Are Lop-Sided or Crooked'
drwxr-xr-x 2 mofa511 mofa511     4096 Jul 20 17:01 'Plus Size Bras Convertible Bra'
-rw------- 1 mofa511 mofa511     2571 Jul 23 15:32 'Re: Caring For Fitz.eml'
-rw-rw-rw- 1 mofa511 mofa511    38115 Jun 13 14:42 'Re: Water bill.eml'
-rw-rw-rw- 1 mofa511 mofa511    74268 Jul 20 12:25 'SpinTel Monthly Bill.eml'
-rw-rw-rw- 1 mofa511 mofa511    47150 Jul 21 17:47 'The Middle East.odt'
-rw-rw-rw- 1 mofa511 mofa511   550419 Oct  2  2013 'The Secrets of Fighting Female Flab Over 40.pdf'
-rw-rw-r-- 1 mofa511 mofa511    30341 Jul 23 01:51 'Three Dead.odt'
-rw-rw-rw- 1 mofa511 mofa511  1490432 Mar  9 18:54 'Weekly Nutrition Diary Charts.xls'
-rw-rw-rw- 1 mofa511 mofa511  1498112 Mar 29 13:46 'Weekly Nutrition Diary.xls'
-rw-rw-rw- 1 mofa511 mofa511   456283 Jul 23 02:04 'Winning The Dark Magic World War.docx'
-rw-rw-rw- 1 mofa511 mofa511   445837 Jul 23 02:04 'Winning The Dark Magic World War.odt'
```

---

### Post by ajgreeny on 2018-07-23
Is **mofa511** your Ubuntu username as that is the owner of all those files and folders on your Desktop?

---

### Post by skyesharica on 2018-07-23
> **ajgreeny said:**
> Is **mofa511** your Ubuntu username as that is the owner of all those files and folders on your Desktop?

Yes, mofa511 is my Ubuntu username.

---

### Post by yancek on 2018-07-24
If you are logged in as user 'mofa511', you should be able to access and modify the files based on the owner:group and permissions you posted.  If you are getting a read-only error, you might have a corrupted filesystem and you need to check that.  You can run the 'fsck' command to do that from the Ubuntu installation media.  You can't do a filesystem check from a system in use, the Ubuntu you are booted to from the installation.  You will need to know which partition your /home/user folders/files are on also and this is explained at the link below.  It also tells how to run fsck with various options.

[https://www.thegeekstuff.com/2012/08/fsck-command-examples](https://www.thegeekstuff.com/2012/08/fsck-command-examples)

Were the various folders/files you copied to Ubuntu created on another Linux/Ubuntu installation or some other operating system?

---

### Post by skyesharica on 2018-07-25
> **yancek said:**
> If you are logged in as user 'mofa511', you should be able to access and modify the files based on the owner:group and permissions you posted.  If you are getting a read-only error, you might have a corrupted filesystem and you need to check that.  You can run the 'fsck' command to do that from the Ubuntu installation media.  You can't do a filesystem check from a system in use, the Ubuntu you are booted to from the installation.  You will need to know which partition your /home/user folders/files are on also and this is explained at the link below.  It also tells how to run fsck with various options.

[https://www.thegeekstuff.com/2012/08/fsck-command-examples](https://www.thegeekstuff.com/2012/08/fsck-command-examples)

Were the various folders/files you copied to Ubuntu created on another Linux/Ubuntu installation or some other operating system?

I've tried changing the permissions for all of the Desktop, and Documents.  But whenever I use the same title for the file, and book, and try to save it, I get this message:  "Error saving the document To Win Against The International Dark Magic War:  Object not accessible.  The object cannot be accessed due to insufficient user rights."

If I have a corrupted file system I think I am at a loss.  Because I don't understand all the technical details and language in that article.  I can't do that.

---

### Post by deadflowr on 2018-07-25
Seems fairly easy to find out if it's a libreoffice problem or a file system problem.
Create a basic text file in gedit and try and save it.
If it saves then the issues would seem to be libreoffice related.

In which case perhaps try nuking or moving the libreoffice configuration folder at ~/.config/libreoffice/4/user.
(or rename that folder something like user-old; libreoffice will regenerate a new folder if one does not excist the next time you start it up.)

If trying to save the gedit file fails, then it's logically the file system at fault.

---

### Post by skyesharica on 2018-07-25
> **deadflowr said:**
> Seems fairly easy to find out if it's a libreoffice problem or a file system problem.
Create a basic text file in gedit and try and save it.
If it saves then the issues would seem to be libreoffice related.

In which case perhaps try nuking or moving the libreoffice configuration folder at ~/.config/libreoffice/4/user.
(or rename that folder something like user-old; libreoffice will regenerate a new folder if one does not excist the next time you start it up.)

If trying to save the gedit file fails, then it's logically the file system at fault.

The gedit file saves fine.  So it's not the file system.  I don't understand what you mean by nuking or moving the libreoffice configuration folder.  I wouldn't want to do advanced things like that because I'm not a programmer etc.

---

### Post by deadflowr on 2018-07-25
> **skyesharica said:**
> The gedit file saves fine.  So it's not the file system.  I don't understand what you mean by nuking or moving the libreoffice configuration folder.  I wouldn't want to do advanced things like that because I'm not a programmer etc.

Not really that advanced.
Simply open the Files program.
enable show hidden folder and files (ctrl + h is the keyboard shortcut for showing hidden folders)

Go to the .config directory.
Scroll down to the libreoffice directory and open.
Then open the 4 directory and highlight the user directory and right click and choose rename and change the name to something else, anything would work, really.
But probably easiest to rename it something like user-old.

The next time you open libreoffice, it'll regenerate a new and clean configuration folder.
And if the new one is still as bad as the old renamed one, then you can always move the new one to trash and rename the old one back to it's original name.

Now, I can't say that this is the solution, but only that it is something I would try.
And if it does not work to restore read/write document functions either, then at least it's known that that was not the problem.

---

### Post by skyesharica on 2018-07-25
> **deadflowr said:**
> Not really that advanced.
Simply open the Files program.
enable show hidden folder and files (ctrl + h is the keyboard shortcut for showing hidden folders)

Go to the .config directory.
Scroll down to the libreoffice directory and open.
Then open the 4 directory and highlight the user directory and right click and choose rename and change the name to something else, anything would work, really.
But probably easiest to rename it something like user-old.

The next time you open libreoffice, it'll regenerate a new and clean configuration folder.
And if the new one is still as bad as the old renamed one, then you can always move the new one to trash and rename the old one back to it's original name.

Now, I can't say that this is the solution, but only that it is something I would try.
And if it does not work to restore read/write document functions either, then at least it's known that that was not the problem.

Thankyou very much but I'm sorry, that's all impossible for me - far too advanced - I wouldn't know what to do if I made a small mistake half way through it.  I don't understand most of the words you are using like:  the Files program, .config directory, 4 directory, user directory, configuration folder, etc.

---

