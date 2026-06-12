---
title: "Issues with wastebasket in 13.04"
date: 2013-04-30
forum: General Help
---

### Post by northwestern on 2013-04-30
Hi
I have two files in my rubbish bin called L & k, no matter what I do my system will not let me delete them.
Any suggestions what they are and how to delete them?.

Regards
Northwestern

---

### Post by dino99 on 2013-04-30
sudo rm /path/to/file

---

### Post by northwestern on 2013-05-01
Thanks for your reply, could you explain what to do more simply, I don't quite understand your reply.

Regards
Northwestern

---

### Post by alhefner on 2013-05-01
> **northwestern said:**
> Thanks for your reply, could you explain what to do more simply, I don't quite understand your reply.

Regards
Northwestern

In a terminal, you'll be using the "sudo" level to run the "rm" command to remove the file. the "path/to/file" is just an example so, if your file is in "home/documents/filename.txt" that would replace "path/to/file".

This will immediately and permanently delete that file so be sure of the path and file name!

Hope it helps!

---

### Post by northwestern on 2013-05-01
Thanks for reply.
Sorry I am none the wiser, the two files are just calles "L" & "k", no matter what I do it says I have not got permissions to read or delete them. I have tried "sudo nautilus" but even using that I am denied permiision to read, delete or move.
Regards
Northwestern

---

### Post by alhefner on 2013-05-01
> **northwestern said:**
> Thanks for reply.
Sorry I am none the wiser, the two files are just calles "L" & "k", no matter what I do it says I have not got permissions to read or delete them. I have tried "sudo nautilus" but even using that I am denied permiision to read, delete or move.
Regards
Northwestern
 OK, use your file system to find where these files are located. That would be the "folder" icon on the launcher. When it opens, you'll be looking at your home folder. press ctrl+h to show the "hidden" files and folders.

Once you can see the hidden stuff, use the search function to look for those two files and remember the "path" to them... "home/documents/someotherfolder/L".

When you have the paths to those files written down so you can remember them, use "crtl+alt+t" to open a terminal.

In the terminal, type "cd .." and then press "enter". You'll notice that you are now in a lower level directory.

Then, type "sudo rm the/path/you/wrote/down/L" then press "enter". You may get a prompt telling you to enter your password. Type it in even though you will NOT see anything happening on the display as you do it! Once you have typed your password, press "enter". You should see either a new blank command prompt or an error message.

If you get an error message, it should be something like "no such file" and THAT means you didn't find the path to the files and need to look some more.

If you just get a blank command prompt, that means the file was erased and you can then repeat the steps to get rid of the second file.

When both files have been erased, or you have given up, you can close the terminal window.

---

