---
title: "recover data on hdd"
date: 2007-02-01
forum: General Help
---

### Post by arya6000 on 2007-02-01
Hello

My friend has a external HDD with 2 partitions, he uses windows, on one of the partitions all of his work files disappeared, he gave his HDD to me so I can try to see if the files are recoverable. I think the file system is NTFS but when I plug it in using USB, Ubuntu detects and I can read and write to it. Is there any programs on Linux that can recover the files?

Thank You

---

### Post by bodhi.zazen on 2007-02-01
I do not understand.

If you can read and write to the HD why can you not just copy the files, either to an alternate drive or burn to CD/DVD ?

---

### Post by arya6000 on 2007-02-01
I can read and write new files to it, but his old important files have been deleted, but the HDD has not been formated yet, so I was wondering if there are any programs that would bring back the deleted files

---

### Post by aysiu on 2007-02-01
And if you wrote something else (and bodhi.zazen and I just misunderstood the part about being able to read from and write to it), you can use *dd_rescue* to save it, too.

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by bodhi.zazen on 2007-02-01
> **arya6000 said:**
> I can read and write new files to it, but his old important files have been deleted, but the HDD has not been formated yet, so I was wondering if there are any programs that would bring back the deleted files

How were the files deleted ? Deleted from windows or re-partitioned ?

First thing you should do is **mount the HD READ ONLY. If you continue to write to the disk you may well overwrite the files you are trying to recover** ...

---

### Post by arya6000 on 2007-02-12
> **bodhi.zazen said:**
> How were the files deleted ? Deleted from windows or re-partitioned ?

First thing you should do is **mount the HD READ ONLY. If you continue to write to the disk you may well overwrite the files you are trying to recover** ...

It hasn't been repartitioned, I tries rsync and didn't recover the files :(

---

### Post by bodhi.zazen on 2007-02-12
I'm sorry, can you provide any further information ?

How is it that the data was "deleted" ? It is very difficult to assist you without more specific information.

And what made you think rsync can be used for data recovery ?

I guess at this point my best advice is for you to seek some professional assistance as I am not confident you are up to the task.

I would warn you that continued "blind guessing" at data recovery is likely to increase the problem and I would advise against such attempts.

---

### Post by arya6000 on 2007-02-12
> **bodhi.zazen said:**
> I'm sorry, can you provide any further information ?

How is it that the data was "deleted" ? It is very difficult to assist you without more specific information.

And what made you think rsync can be used for data recovery ?

I guess at this point my best advice is for you to seek some professional assistance as I am not confident you are up to the task.

I would warn you that continued "blind guessing" at data recovery is likely to increase the problem and I would advise against such attempts.

The HDD belongs to my friend and he said the files vanished one day, he is a teacher so he had or has some important files in there, I searched Google and found a software on this site: [http://www.recovermyfiles.com/](http://www.recovermyfiles.com/) , but I was wondering if there is  anything like that for Linux, so that I can try, maybe I would get a chance to recover them.


Thank You

---

### Post by bodhi.zazen on 2007-02-12
This may help :


[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

