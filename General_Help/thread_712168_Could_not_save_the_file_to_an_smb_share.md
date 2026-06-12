---
title: "Could not save the file to an smb share"
date: 2008-03-01
forum: General Help
---

### Post by MountainX on 2008-03-01
I may have encountered a bug or a situation that requires extra steps that I'm not aware of yet. After reading some of the cifs permissions documentation and following the suggestions in [another thread]("http://ubuntuforums.org/showthread.php?t=710607"), I am fairly comfortable that I'm mounting the share correctly, yet I am still getting an error -- see step 3 below.

The common factor in my testing has been that I use Nautilus to create an empty file in the smb share, then I use gedit to attempt to write text into that empty file and save it. This has been failing. At first I thought it was related to write permissions. Now I don't know what the problem is.

Below are the latest details of my testing:

Step 1: test read only

sudo mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myu ser,dir_mode=0400,file_mode=0400,ro //192.168.99.5/Shared /media/test

echo "The command is: mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myu ser,dir_mode=0400,file_mode=0400,ro //192.168.99.5/Shared /media/test" > /media/test/deleteme1.out

#bash: /media/test/deleteme1.out: Permission denied
#this is as expected

sudo umount /media/test

Step 2: test with write permissions

sudo mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myu ser,dir_mode=0770,file_mode=0770,rw //192.168.99.5/Shared /media/test

echo "The command is: mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myu ser,dir_mode=0770,file_mode=0770,rw //192.168.99.5/Shared /media/test" > /media/test/deleteme2.out

#ls /media/test
#deleteme2.out (it is listed and it has the correct content)

**Step 3: test as I have been doing previously:**

Open Nautilus
open test folder (share)
File > Create Document > Empty File "deleteme3.txt"
double click "deleteme3.txt" to open in gedit
enter some text and click save:
**[SIZE="4"]Error: Could not save the file /media/test/deleteme3.txt.[/SIZE]**
:confused:

ls -l shows:
-rw-r--r-- 1 myuser myuser 171 2008-03-01 12:42 deleteme2.out
-rw-r--r-- 1 myuser myuser   0 2008-03-01 12:43 deleteme3.txt

I have tested this various ways, but I always get an error with the above steps.

Questions:
1. Why do I get an error when I try to write text and save the file deleteme3.txt?
2. Why don't I have the expected permissions which would be **-rwxrwx---** ?

I added another test scenario:
Open gedit
put some text in a new file
save to /media/test as deleteme4.txt (the share 'test' is still exactly as specified above)
There is no error writing the file.
WIth the file still open, add another line of text (doesn't matter what or how much).
Save the file again by clicking the 'save' button in gedit
**ERROR:**
The file /media/test/deleteme4.txt
has been modified since reading it.
If you save it, all the external changes could be lost. Save it anyway?
Click "save anyway" button
**ERROR: **
Could not save the file /media/test/deleteme4.txt.

---

### Post by MountainX on 2008-03-01
FYI, I noticed that my mount command had a typo - credentials has an "s" on the end. However, in my testing yesterday I spelled it correctly, and I fixed the typo today and retested and I get the same errors.

---

### Post by MountainX on 2008-03-01
In further testing, I find that these smbfs commands works as expected. cifs continues to give problems.

```
sudo mount -t smbfs -o credentials=/root/.MyCredentials,dmask=777,fmask=777 //192.168.99.5/Shared /media/test

sudo mount -t smbfs -o credentials=/root/.MyCredentials,uid=me,gid=me,dmask=770,fmask=770 //192.168.99.5/Shared /media/test
```

I understand that cifs is preferred, so I find it baffling that smbfs works well but cifs is seemingly very quirky. Can anyone shed some light on this for me? Thanks.

---

### Post by MountainX on 2008-03-01
I filed this as a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/197490](https://bugs.launchpad.net/ubuntu/+bug/197490)

---

### Post by rapiscan on 2008-03-01
That's a duplicate bug, I would recommend killing it. 

Here's my response in the other thread on this topic:

This is a known bug, which was originally reported for samba cifs. See this bug report:

[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

The developers seem to blame cifs, while some of the users try to blame gedit itself. I would trust that the developers know what they're talking about, and it's a bug with cifs. This is even more likely since it works fine when it's mounted as smbfs.

I would recomend just using smbfs for now. Don't forget to mark the thread SOLVED.

---

### Post by marcuskoze on 2008-03-19
I'm on a Ubuntu Gutsy Gibbon (all updates installed at the moment of writing this), mounting through smbfs ... I keep on getting the message "The file ** has been modified since reading it. If you save it, all the external changes could be lost. Save it anyway?" ; if i click on the "Save anyway" button it saves the change, but if do that again i get the message (again ... and again ...)

What on earth is happening ?  I've seen [here]("https://bugs.launchpad.net/gedit/+bug/34813") people saying that the issue is either with gEdit or Cifs or Smb ... don't understand a thing of it ... just keep on hoping that this problem is going to go away from my favourite source code editor ...

---

### Post by MountainX on 2008-03-19
> **marcuskoze said:**
> 
What on earth is happening ?  I've seen [here]("https://bugs.launchpad.net/gedit/+bug/34813") people saying that the issue is either with gEdit or Cifs or Smb ... don't understand a thing of it ... just keep on hoping that this problem is going to go away from my favourite source code editor ...

I solved the problem by mounting my network shares with smbfs rather than cifs. That was the issue for me. You may need to look at your fstab file to make sure you aren't using cifs. People more knowledgeable than me might have other tips.

---

### Post by MountainX on 2008-03-26
Hmmm now I'm using Hardy beta and a very similar problem is back! I can't solve it yet.

---

### Post by MountainX on 2008-03-27
I have verified this. The problem is back in Hardy -- and the fix described here doesn't work.

---

### Post by MountainX on 2008-03-27
[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

The diagnosis is described in these two comments here:
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40)

solution: don't use gedit to edit files on network shares

---

