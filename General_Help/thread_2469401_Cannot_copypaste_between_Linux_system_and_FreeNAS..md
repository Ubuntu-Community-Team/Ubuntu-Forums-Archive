---
title: "Cannot copy/paste between Linux system and FreeNAS. What is the problem?"
date: 2021-11-27
forum: General Help
---

### Post by geekgeek4 on 2021-11-27
Hello, 

I have Ubuntu 20.04.3 LTS installed and have been using it for some time. I have a NAS through FreeNAS. I have been using the NAS with all of my devices including Ubuntu without any problems. However, recently, something changed on the Linux system only. I cannot use copy and paste between the Linux system and the FreeNAS. 

I have verified the permissions on the FreeNAS. When I click on "Copy" on a NAS file in Ubuntu "Files" and then right click on Desktop, the "Paste" option is greyed out, indicating that the copy did not work or register. Same thing happens if I "Copy" file from say Ubuntu Desktop, and go to the NAS folder, the "Paste" option is greyed out. 

One important note is that when I use "Copy To", a window opens that prompts me to select where I want to copy the file. **This works** **for both of the above situations **and using "Copy To" or "Move To", I can transfer data between Ubuntu and the NAS without a problem. 

Please let me know what additional information I can provide to assist with finding the problem.

Why is this issue occurring and how can I solve it?

---

### Post by yancek on 2021-11-28
The functions you describe worked before, correct?  The Copy/Paste options.   Have you made any type of hardware changes or changes to configuration files for NAS?

> I   have verified the permissions on the FreeNAS. When I click on "Copy" on  a NAS file in Ubuntu "Files" and then right click on Desktop, the  "Paste" option is greyed out,

What are the permissions and owner:group?  When you say "Desktop", are you trying to paste to the Desktop directory?   Or are you trying to copy to a particular user Desktop.  If you click on a file not part of FreeNAS and try to Paste it on your user Desktop, what happens?

---

### Post by Topsiho on 2021-11-28
I since recently have noticed the same problem, which did not exist before.
an example of the permissions of the files are:

drwxr-xr-x 2 jaap jaap   4096 okt 30  2009 .
drwxr-xr-x 3 jaap jaap   4096 apr  3  2021 ..
-rw-r--r-- 1 jaap jaap  68235 okt 30  2009 Beach...surf_crashes_down.jpg

I am trying to copy to my desktop, which is refused.

The desktop (Bureaublad) permissins are
drwxr-xr-x 13 jaap jaap  4096 nov 26 16:40  Bureaublad

Once again: this problem did not exist before, and I found no settings of the permissions that changed this behaviour.

Topsiho

---

### Post by yancek on 2021-11-29
I'm really not sure your problems is the same as that of the original poster.  Are you using FreeNAS also?  What do you mean by copying to your desktop?  There is a directory named Desktop in each user /home directory, is that where you are trying to copy to?  You need to be logged in as that user.  Also, are you running the standard Ubuntu as the Gnome/Nautilus developers do not want files/folders on the Desktop.    

What exactly is "Bureaublad" and how does it fit in here?  The output you posted for it shows it to be a directory with the owner being 'jaap with read, write and execute permissions.

---

### Post by yancek on 2021-11-29
I'm really not sure your problems is the same as that of the original poster.  Are you using FreeNAS also?  What do you mean by copying to your desktop?  There is a directory named Desktop in each user /home directory, is that where you are trying to copy to?  You need to be logged in as that user.  Also, are you running the standard Ubuntu as the Gnome/Nautilus developers do not want files/folders on the Desktop.    

What exactly is "Bureaublad" and how does it fit in here?  The output you posted for it shows it to be a directory with the owner being 'jaap with read, write and execute permissions but you do not show in what directory it exists, is this in your FreeNAS. .

---

### Post by Topsiho on 2021-11-29
Hello yancek,

Thanks for replying. Actually, I only wanted to support the original poster in that he is not the only one who has this problem.
I think a recent update of Ubuntu (20.04.3, Gnome) caused this, a future update will correct this, i'm sure.
If it really becomes a nuisance I'll investigate this further, or do the copying and moving in the terminal.

In my previous post I wrote that the Bureaublad is the Desktop. Bureaublad is the Dutch translation of Desktop.

And: I think the problem is very much the same as that of the original poster, I think. Even without a NAS.

Topsiho

 
Edit: I have plenty of files and folders on my desktop. I cannot do without them, making my desktop a mess. So be it.

---

### Post by Topsiho on 2021-11-29
Hello yancek, and geekgeek4,
I tried  this on another computer, problem is the same.
Using the terminal everything is as it should be, no problem.
Your remark that Gnome/Nautilus developers are against files and folders on the desktop set me thinking. And so the (my) problem is solved. Until recently however, I did not notice anything in that direction. So something learned today. Thank you.

Topsiho

---

