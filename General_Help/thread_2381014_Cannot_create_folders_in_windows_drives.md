---
title: "Cannot create folders in windows drives"
date: 2017-12-25
forum: General Help
---

### Post by carusoswi on 2017-12-25
In previous versions of Ubuntu, I could access, read from/write to, and create folders on Windows drives (I refer to the system drive upon which Windows resides, other internal drives/volumes, and external USB drives.  Since upgrading to 17.10, I can only create drives on the Ubuntu volume. I can read to/write to, add/delete files to or from any location, but if I need to create a folder, that option is not presented.  Checking properties on these "Windows" drives, I confirm that I have permissions set for full "read/write".

What am I missing.  As it is now, I have to either choose some other location, or exit Ubuntu, boot into Windows, then boot back into Ubuntu to use the newly created folder.  Inconvenient to put it mildly.

Suggestions would be appreciated.

Caruso

---

### Post by The Cog on 2017-12-25
17.10 certainly is capable of writing to NTFS partitions. I seem to remember that it is possible for NTFS to be marked as needing a check with chkdisk and that the Linux drivers will treat it as read-only until chkdsk as done its work. If this is what has happened then I think you need to use windows to run chkdsk over the partition.

---

### Post by coffeecat on 2017-12-25
Make sure you have fast startup disabled in Windows, otherwise you won't be able to write to NTFS partitions. If you previously disabled fast startup, a subsequent Windows update may have re-enabled it. Irritating, but true. In case you need it, here's how to disable fast startup:

[https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html](https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html)

Also. Don't do a restart from Windows. Even if you have fast startup disabled, I believe Windows will do a hybrid shutdown when you select restart/reboot or whatever it is called in Windows. You need to shutdown from Windows and then do a cold boot into Ubuntu.

By the way, by fast startup, I'm referring to the Windows "feature", not fast boot in BIOS.

---

### Post by carusoswi on 2017-12-26
> **The Cog said:**
> 17.10 certainly is capable of writing to NTFS partitions. I seem to remember that it is possible for NTFS to be marked as needing a check with chkdisk and that the Linux drivers will treat it as read-only until chkdsk as done its work. If this is what has happened then I think you need to use windows to run chkdsk over the partition.

Thanks for the reply.  I will run chdsk on Windows to see if that helps.  However, and perhaps I did not make it clear enough, my problem is not reading from/writing to NTFS partitions.  I can do that.  What I cannot do is create new folders on those partitions.  I can only create folders on ext* partitions.  I like to work with Blender and Gimp in Ubuntu.  I have a large external USB drive that I use for storage.  I wanted to put my work from yesterday into a new folder on that drive that I called "Christmas 2017".  Could not create the folder from Ubuntu.  Had to boot into Windows, create the folder, boot back into Ubuntu, and, then, I could create files with Blender and Gimp and save my work to the "Christmas 2017" folder on the external drive.

I will try your suggestion and run the chkdsk to see if that illuminates the problem.

Thanks.

Caruso

---

### Post by carusoswi on 2017-12-26
I discovered the problem.  I am not certain it is supposed to work this way (and, if it is, am puzzled as to why it would be designed to work this way), but in order to bring up the menu that allows you to create a new folder you have to right click somewhere in the white space of the "box" that contains the drive contents.  This is easy to do if your list of items (folders/files) do not fill the screen.  If your list of items is long and runs off the screen, there may not be any white (empty) space.  In that case, when you right click, another menu pops up that does not include the "new folder" entry.

I overcame this problem by switching away from list view to icon view so that white space was available.

Problem solved, simple (but in my view,, unnecessary step).

Now, if I knew how, I would mark this thread SOLVED.

Caruso

---

### Post by uRock on 2017-12-26
> **carusoswi said:**
> ...

Now, if I knew how, I would mark this thread SOLVED.

Caruso

In the upper right hand corner, click Thread Tools and select [Solved]

---

### Post by Cavsfan on 2017-12-26
Personally, I would not write anything from a Linux system to a Windows partition. It *can* cause problems.

It resulted in me re-installing windows, which I have never had to do before that.

But, it is up to you what you do with your system.

PS: uRock left out that you must edit the 1st post and do that there.

---

### Post by uRock on 2017-12-26
> **Cavsfan said:**
> PS: uRock left out that you must edit the 1st post and do that there.

Nope. Editing not required.

---

### Post by Impavidus on 2017-12-27
> **Cavsfan said:**
> Personally, I would not write anything from a Linux system to a Windows partition. It *can* cause problems.

Don't use Linux to write anything to your Windows C partition. That can cause problems. Writing to data partitions, like those D and E partitions you may have in Windows, is safe.

---

### Post by carusoswi on 2018-03-04
I, basically, do not write anything from either Windows or Linux to my C drive other than writing that takes please when I install new applications.  On the other hand, I would assume that, as long as one does not write to system folders, writing to C from either OS should not pose a problem.  I have two internal drives and a number of external storage devices, so, I generally avoid storing data on C in case I need, for some reason, to wipe the drive and start over from scratch.

In my experience, I have found both OSs to be fairly robust in so far as their ability to preserve data.  I've been locked out of both on numerous occasions.  The only time I recall not being able to recover was on one of my office machines where an employee left our employee and we did not know her computer password.  I called in a 'specialist' who said he could get around it (and he's a good man, I don't doubt his abilities), but something went wrong and he broke the system.  He didn't charge me, so I took it to a PC shop who claimed to be able to overcome the problem, but, in the end, we wiped it and its data.

Of course, my experience is just that.  Others will report different experiences for various reasons.

Thanks for the replies.

Caruso

---

