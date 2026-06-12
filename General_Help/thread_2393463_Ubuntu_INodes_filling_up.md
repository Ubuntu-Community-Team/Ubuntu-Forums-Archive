---
title: "Ubuntu INodes filling up"
date: 2018-06-04
forum: General Help
---

### Post by MarcusL on 2018-06-04
I have an Ubuntu 16.04 server that I recovered this morning from an INodes at 100% issue. The server is in AWS and it contains a Laravel app.

After deleting a bunch of files / packages, I now have 63K INodes free. 

I am now monitoring the number of free INodes over time and I can see it declining (very slowly) over time as the app is used. 

I am looking to find out which files are being created and by which process as they do not seem to be deleted after use.

Is there a way to list all files in a drive / dev by order of creation date? Or any other suggestion to find which / were files are being created?

Thanks!

---

### Post by TheFu on 2018-06-04
find with a sort?  
To get started, 
**find / -type f -ctime -1**
Be certain to understand how find rounds up/down time specifications. It isn't intuitively obvious, at least not to me.

There are 500 other methods too, but really the best answer is to build a new file system with 100x more inodes. The mkfs (or is it newfs) command lets you specify the inodes manually.  The defaults work for larger file systems, but when they are less than 8G in size, the algorithm doesn't work so well if there are lots of tiny files like most web-app scripting languages have.

---

### Post by MarcusL on 2018-06-04
Thanks! Figured out the issue with your help and sorted the problem out. I was holding session lifetime too long and causing the creation of many files.

---

