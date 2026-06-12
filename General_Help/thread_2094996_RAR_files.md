---
title: "RAR files"
date: 2012-12-15
forum: General Help
---

### Post by typos1 on 2012-12-15
I m trying to extract some .rar files. I simply right click and left click on "extract here". It works fine, I enter a password (these .rar files are password protected) and it extracts them. Its a DVD iso, broken up into 14 200mb packages, but when extracted they are all 4.4Gb (all have the same file name as well, not part 1, 2 etc) and clearly wont fit onto one disc. Because of this problem, "I googled how to extract .rar files on ubuntu" and most results say to install unrar. 

Now, I m pretty sure I ve been able to extract .rar files before, although I may be wrong, but unrar is not installed, surely I would not be able to extract them at all without unrar or similar and I d get an error message, rather than "extract here" appear to work but extract the files in the wrong size ?

---

### Post by Ms. Daisy on 2012-12-15
Everything I've seen indicates that Ubuntu can't uncompress a .rar file without unrar.  

I think if you tried to uncompress the .rar files in terminal without having unrar installed, you would see the errors you're expecting.

---

### Post by typos1 on 2012-12-15
Thanks, based on your reply, I used software centre to try and install it, but it IS installed. I dont remember installing it (and I ve got a new pc and done a completely new install within the last 5 months), I could be wrong, or maybe it comes with ubuntu out of the box now, but have you any suggestions as to what might be causing this ? Thanks

---

### Post by Ms. Daisy on 2012-12-15
Well I would start by checking the md5 sum of the .rar file (assuming you downloaded it from somewhere).  It's possible that it got corrupted during download.

---

### Post by Rexilion on 2012-12-15
Most GUI use 'unrar' as a backend. That is also the reason why it's already installed. Might I suggest you use a terminal, navigate to the directory containing the rarfiles and do:

```
unrar x 'file'
```

On the rarfile not ending with a digit?

Post the output of the above command please. Maybe it will tell us what is going on in detail.

---

### Post by SeijiSensei on 2012-12-15
Now that you have the opportunity to check the box to allow restricted-extras during installation, perhaps unrar is installed automatically if you check that box?

---

### Post by typos1 on 2012-12-15
Rexilion, they all end with a digit, eg DVD1part01 etc

---

### Post by Rexilion on 2012-12-15
Okay, pick a random one (maybe one starts with 00?) or any other one for that matter. And show us the output.

---

### Post by typos1 on 2012-12-15
They are numbered DVD1part01.rar through to part 14.

If I type what you say it says no such file or directory.

Should I give it a path ?

---

### Post by Mark Phelps on 2012-12-15
Been a while since I did this, so the apps might work better now, but when I had this problem (with numbered archive pieces) in the past, I discovered that unlike with WinRAR, I could not just select the first and ALL would then expand; instead, I had to do it one at a time.

I was using unzip at the time, so unrar might not work the same way, but the solution was to open a terminal and type the following:

```
for FILE in `/bin/ls _*.zip`; do unzip -o $FILE; done
```

Notice the use of "graves" (the ` mark), not apostrophes.

---

### Post by steeldriver on 2012-12-15
iirc unrar / archive manager is smart enough to recognize if it's given one part of a multi-part archive and looks for the rest of the parts implicitly - if you try to unrar each part explicitly you are probably just getting multiple copies of the same complete original file

---

### Post by typos1 on 2012-12-15
It says "cannot access /bin/ls, no such file or directory".

All  I am doing is right clicking on the file and extracting it, I m not trying to do all at once.

Steeldriver, I think youve cracked it - I m trying them all separately. This has always worked before, but it sounds like it could be the problem . . .

---

### Post by typos1 on 2012-12-15
. . . well, it extracted them all, in one go - I could see it extracting each part, it put them all in a folder entitled disc1, so I thought that was the problem. The only thing is, once it had done part 14, it started again. When it finished it created another folder - disc1 (2). Then it started again ! Did a third, etc, stopped it after 4, as it seems its just doing the same thing as if I do them separately :(

---

