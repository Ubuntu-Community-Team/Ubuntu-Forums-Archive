---
title: "Ubuntu mess up my file system? Can't copy large folders in Windows + Deletion trouble"
date: 2014-06-17
forum: General Help
---

### Post by 777funk on 2014-06-17
I've had an issue that I've noticed after letting Ubuntu modify "My Documents" for a couple years. I went to copy a large folder (maybe my pictures) from one hard drive to another and it wouldn't do anything in Windows (new install of Win7 Pro). I'm not sure if this is a permissions thing.

Also sometimes I get an error saying can't read from directory. 

Never seen this before and wondering if Ubuntu use or perhaps improper use is to blame.

---

### Post by rahul4557 on 2014-06-17
May be because of user rights to the folder
you can change rights to any folder in ubuntu using terminal 
goto the directory where the folder is located and type
> sudo chmod -R 777 <foldername>

---

### Post by ajgreeny on 2014-06-17
Be _**very careful**_ how you use that command within your ubuntu filesystem; incorrect permissions to folders and files can potentially cause you BIG problems, so I would investigate a bit more and look for the reasons why you can't copy those folders and try to find alternative ways.

Give us an exact example of what you are having problems with; tell us the details of what and where the folders are (which partition/disk) to start with and to which filesystem/partition you are trying to move them.

---

### Post by Mark Phelps on 2014-06-17
> perhaps improper use is to blame. 

Well, I've been telling folks for years NOT to use Linux to make changes to files in Windows OS partitions -- but nobody listens.

---

