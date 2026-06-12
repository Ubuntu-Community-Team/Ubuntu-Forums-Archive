---
title: "how to move a file mounting location"
date: 2023-09-20
forum: General Help
---

### Post by jgw on 2023-09-20
I am trying to figure out how to move a file.  The file is in a hard drive which has been named 3tb  and 3tb holds 2 large files.  3tb is 'media' (a root folder)  The first file I will call 'one' and the second 'two'.  What I want to do is to change the location for the two large files from /media/3tb to /media.  Another way to say that is that I want to access the two files from /media and not /media/3tb.  I also think that I may be confused.  

What I need to do is to change the location of the two large files to /media without actually changing the location.  I suspect there is an easy solution to this but I can't figure it out.  

Thank you............

---

### Post by Holger_Gehrke on 2023-09-20
Would a symbolic link be what you want ? Read the man page for 'ln' for the details.

Holger

---

### Post by jgw on 2023-09-20
Thank you for the reply.  I have read the man page and I remain confused. 

I think my best shot is to mess with this with dummy files as I really don't want to lose a 1.5tb file that I really need.  So, I will play with Ln for a bit and see what happens.  Can't hurt anything with dummy files.  But, just in case I am currently backing up to another drive.

Thanks again!

---

### Post by jgw on 2023-09-21
I have a file named 'testing' and testing holds 3 other files called test1, test2, and test3.  Each of these holds stuff.

I set this which creates a symbolic link to the real 'testing' at /media/3tb/testing.
 ln -s /media/3tb/testing /media/testing
Then I changed stuff using /media/testing and, as far as I can tell it worked.

I am posting this so that somebody can tell me if this is the right way to change the access point of a file from a different location.  It seems to work for me but I have never done this before and want to make sure I'm right.

Thoughts?

.

---

### Post by ajgreeny on 2023-09-21
I am baffled as to why you want to change away from the default mount-point of partitions not listed in /etc/fstab, ie, /media/username/diskident to  the one step up, ie, /media/diskident; why is it important to you?
It is easiest to leave it at the default mount-point and simply add that as a bookmark in your file-manager if it's not there already.

If I'm missing something important here tell me more.
By using /etc/fstab it is possible to make a partition mount anywhere in the filesystem but there are few advantages to the sort of change you seem to want hence my questions.

---

### Post by jgw on 2023-09-21
I am not sure about partitions which I suspect has to do with parts of memory but I can be wrong.  I want to access a file which is at /media/TV  I need to do this for a program I have that wants it there.  Ubuntu does not like my moving a 1.5tb file onto a root folder.  using ln -s /media/3tb/testing /media/folder_name performs that function.  In theory, I can now access a file which is directly mated to /media (a root folder).

I have never done this before.  I think I have it right.  Somebody will take a look and tell me if I am screwing up or not before I go with the real folder.

---

### Post by jgw on 2023-09-24
ln -s /media/3tb/testing /media/testing worked.  I did the same with real files and that worked too. 
Then I tried access the link and, for no reason I can think of, didn't work so, for now, I am going to give up.

I will mark this one as solved.

---

