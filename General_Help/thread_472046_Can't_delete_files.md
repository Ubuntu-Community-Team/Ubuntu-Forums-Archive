---
title: "Can't delete files"
date: 2007-06-12
forum: General Help
---

### Post by stryker719 on 2007-06-12
I'm trying to delete a number of files on my disk.  However, the icons are locked and I am told I don't have permission to delete them.  How do I login as the admin and delete them?

---

### Post by cookies on 2007-06-12
Hit Alt F2 

In the run command box that pops up, type gksudo nautilus

It'll ask for your password. 

Now you can delete all files and folders. Be careful.

---

### Post by stryker719 on 2007-06-12
Thanks for the response.

However, when I do this, I only seem able to manipulate objects in my root.  What I need however is to transfer files from my desktop to my secondary hard drive (which is mounted).  When I try to do that, I am again told that I don't have permission.

---

### Post by Chappy7777 on 2007-06-12
The password you use for Admin is the same as root, so you should be there. But you have to type the password in everytime you open an admin program. IOW, if you have 3 admin programs open, you will have typed the password in 3 times. 
To move files back and forth, you should be able to do from Places, which doesn' require any password. Does Ubuntu see the 2nd HD? When I moved files from my CD to a folder, I didn't need Admin priviledges. Sorry I cannot be of more help, I'm a NooB too. Hopefully someone will see the 2 replies and take a look.

---

### Post by stryker719 on 2007-06-12
I'll take all the help I can get Chappy, thanks.  Anyway, ubuntu is seeing the disk, and it is showing up in Places.

What I do is open 'disk' from the Places menu, and then I try dragging the file from the desktop to 'disk'.  When I try to do that, the 'You don't have permission to do that" prompt pops up.

---

### Post by Chappy7777 on 2007-06-12
Hmmm, more than 2 replies. Anyhow, as I reread your posts I'm a little confused. Nothing new about that. But you said you are deleting files, then you say you are moving them from one HD to another. If Ubuntu sees the 2nd HD, your target HD, I would think you should be able to copy and paste the files from #1 to #2. This is how I moved Mp3s from CD to folder. Mayhaps not the "geekie" method, but it worked. Did you try that? Main thing in my mind is does Ubuntu see the 2nd drive? Likely so. Take a peek in Device Manager if you're not sure.

---

### Post by stryker719 on 2007-06-12
Ubuntu is seeing the second HD, fortunately.  And I apologize about the confusion, I should have clarified that I am trying to both delete and move some files about.

I tried copying and pasting the file, but when I tried to paste the file I was again given the "no permission" prompt.

---

### Post by CautionaryX on 2007-06-12
Is the second HD formatted as NTFS? In this case you'll have to set up the ntfs-3g driver to enable write access from ubuntu to the drive. There's a how-to on how to set it up somewhere around here...

---

### Post by stryker719 on 2007-06-12
It is indeed an NTFS formatted drive.  

Is the ntfs-3g driver safe to use?

EDIT: I installed NTFS Configuration Tool, which uses the ntfs-3g drivers.  Worked flawlessly.  Thanks for all the help everyone.

BTW, [here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") are instructions on how to install the Config tool if anyone needs it.

---

