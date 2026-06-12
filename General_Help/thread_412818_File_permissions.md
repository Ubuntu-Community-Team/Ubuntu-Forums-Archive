---
title: "File permissions"
date: 2007-04-18
forum: General Help
---

### Post by Cloudy on 2007-04-18
For some reason file permissions confuse me.. I read the man page for chmod but I still don't really "get" it. How do you come up with the numbers? (chmod blah blah blah 754 etc..)? For example, if I have a group - let's say "management" - and I want this group to have full access to a subdirectory called "money" - how would I do that? Or if I had a group like "cashiers" and wanted this group to have read and execute access to "money"? I'm kind of confused.. ahhhh! Someone help me out here.

---

### Post by bashologist on 2007-04-18
> **Cloudy said:**
> chmod blah blah blah 754 etc

I think I see two separate questions. Here's how you use chmod with numbers to change permissions:
```
--- = 0    r-- = 4
--x = 1    r-x = 5
-w- = 2    rw- = 6
-wx = 3    rwx = 7
usage: sudo chmod 644 /example/filename
```
I don't know about groups. I'm kinda curious too.

---

### Post by John.Michael.Kane on 2007-04-18
Have a read.
[ Quick and Dirty Guide to Linux File Permissions]("http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions")
[Understanding Linux file permissions]("http://www.freeos.com/articles/3127/")

---

### Post by Cloudy on 2007-04-18
But could I change the permissions of a group using that, as in the example(s) I gave?

---

### Post by aysiu on 2007-04-18
7 means read/write/execute
6 means read/write
5 means read/execute
4 means read-only
3 means write and execute
2 means write access only
1 means execute only
0 means can't do anything

The first number in any *chmod* command refers to the owner of the file or folder. The second number refers to the group of the file or folder. And the third number is for anyone else who is not the owner or in the group.

So if your permissions were 740, that would mean the owner could read/write/execute the file, the other users in the group could only read the file, and anyone else wouldn't be able to do anything with the file.

Have you considered just doing this through the graphical user interface? Right-click the folder, go to properities and then permissions.

---

### Post by Cloudy on 2007-04-18
> **SD-Plissken said:**
> Have a read.
[ Quick and Dirty Guide to Linux File Permissions]("http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions")
[Understanding Linux file permissions]("http://www.freeos.com/articles/3127/")

Thanks, looking those over now. Cheers.

> 
Have you considered just doing this through the graphical user interface? Right-click the folder, go to properities and then permissions.


Ah yeah I know about that - was just inquiring about this because I have a linux class and we have a skills test tomorrow that entails being able to change permissions etc. and I'm sure the professor would rather us do it through the terminal.

---

### Post by Cloudy on 2007-04-18
OK I think I have it - so, for example, if I change permissions to 600 - chmod 600 myfile - I'm making it read and write, right? :popcorn:

---

### Post by aysiu on 2007-04-18
> **Cloudy said:**
> OK I think I have it - so, for example, if I change permissions to 600 - chmod 600 myfile - I'm making it read and write, right? :popcorn:
You're making it read/write for *you*, but no one else will be able to read it or do anything to it.

---

### Post by Cloudy on 2007-04-18
> **aysiu said:**
> You're making it read/write for *you*, but no one else will be able to read it or do anything to it.

OK, so - another example - if I changed the owner to let'smakeupaname ahhh.. Mrfly then he'd be the only one able to read and write to it?

---

### Post by aysiu on 2007-04-18
> **Cloudy said:**
> OK, so - another example - if I changed the owner to let'smakeupaname ahhh.. Mrfly then he'd be the only one able to read and write to it?
Since this is a homework assignment, I think your best bet is to just play around and experiment. That's the best way to get to know permissions and ownership.

---

### Post by Cloudy on 2007-04-18
> **aysiu said:**
> Since this is a homework assignment, I think your best bet is to just play around and experiment. That's the best way to get to know permissions and ownership.

Yeah, I think I got it now. :D Just tooling about I made a directory called test on my Desktop and a .txt file called "file". I changed the ownership of "file" to travis as well as the group, then changed it back to root and tried to move it to "test" but couldn't because "test" was owned by travis/in the travis group and read-only. :popcorn: Wow, that almost made sense to me. 

:guitar:

---

### Post by koenn on 2007-04-18
600 : read/write for the owner of the file - everyone alse can do nothing (0)

660 :  
read/write for the user that owns the file and read/write for the group that owns the file, all others can do nothing (0)

666 :
read/write for the user and the group that own the file, and for everybody else as well.
Very dangerous number  :)

---

