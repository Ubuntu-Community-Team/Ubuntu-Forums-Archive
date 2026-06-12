---
title: "Selective Folder Restore w/ Deja Dup?"
date: 2012-11-26
forum: General Help
---

### Post by Rocket J Squirrel on 2012-11-26
I'm presently running 10.10 and am going to overwrite it with a clean install of Lubuntu 12.04.

I have the entire Home folder and subdirectories backed up on an external HD using Deja Dup. 

After installing 12.04 I then want to restore my /home folders, like Downloads, Pictures, etc.

Also, some selected hidden folders used by apps like Thunderbird, the Liferea rss reader, etc, so I don't need to start all those from scratch. 

If I am not mistaken, once 12.04 overwrites 10.10 I won't have access to Nautilus's "Revert To Previous Version," options. 

So my question is: can Deja Dup be used for selective folder and file restoration, and if so, how? 

And if not, is there a better tool for this, one that works with Ubuntu 10.10 and Lubuntu?

---

### Post by CaptainMark on 2012-11-26
The closest option you have is after clicking "Restore" and after selecting where and when to back-up from you get the option to 
i) Restore files to original locations
or
ii) Restore to a specific folder

If you create a temporary folder in your home directory and restore all your files into it then you can copy the ones you require to their correct location and delete the temporary folder when your done, if space is an issue then this wont work for you as you'll effectively double everything. I am not a fan of Deja Dup for this very reason and for future reference would recommend using Rsync in an anacron run script

---

### Post by Shuudoushi on 2012-11-26
You can just use google back up to save just the files you want as .zip files and re-download them as needed.

---

### Post by Rocket J Squirrel on 2012-11-26
Hey there CaptainMark,

Restoring to a spare folder then copying as needed sounds like the simple workaround. Many thanks for that idea.

After that, I'll look into rsync and anacron and see if I can sort those out.

---

