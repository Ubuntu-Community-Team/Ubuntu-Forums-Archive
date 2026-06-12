---
title: "[SOLVED] rsync problem when excluding files"
date: 2008-02-17
forum: General Help
---

### Post by geo909 on 2008-02-17
Hello everybody.

I have been using rsync for a while to back up some folders on an external usb disk and I am pretty happy with it.

Then I decided to take the next step and manage the way the backups are being done, starting with excluding folders from a list.

I searched a lot and read the rsync man pages but couldn't manage to get "--exclude-from=" to work.
This is my case:
For testing purposes, I have created on my Desktop a "source" and a "destination" folder.
I left "destination" empty:

[CENTER][[IMG]http://www.imageshack.gr/files/zgtwrl49wgy2ydc3t105.png[/IMG]](http://www.imageshack.gr/view.php?file=zgtwrl49wgy2ydc3t105.png)[/CENTER]

and I created three folders inside "source" like this:

[CENTER][[IMG]http://www.imageshack.gr/files/av8hlyw602lm9ir8bvxm.png[/IMG]](http://www.imageshack.gr/view.php?file=av8hlyw602lm9ir8bvxm.png)[/CENTER]

Now, on my desktop I create an empty file. I rename it to "exclude", I open it with an editor and write a line like this
```
C_folder
```
having in mind to exclude the "...../source/C_folder"

Then I do:

```
rsync -a --exclude-from= '/home/jorge/Desktop/exclude' /home/jorge/Desktop/source/ /home/jorge/Desktop/destination 

```

So, here's what I get inside the "destination" folder:

[CENTER][[IMG]http://www.imageshack.gr/files/e7yslm5f9h3b325dtq6g.png[/IMG]](http://www.imageshack.gr/view.php?file=e7yslm5f9h3b325dtq6g.png)[/CENTER]

Why the "C_folder" is not being excluded?
What am I doing wrong?

Thanks in advance!

---

### Post by Sokertes on 2008-02-17
you are using it wrong

--exclude-from=FILE     read exclude patterns from FILE

it reads the patterns you set in a file. If you want to use the --exclude-from= then you will have to write a file with the dirs that you want to exclude.

Or you can use

--exclud

--exclude=PATTERN       exclude files matching PATTERN

which is what it looks like you are doing.


run:

rsync -a --exclude= '/home/jorge/Desktop/exclude' /home/jorge/Desktop/source/ /home/jorge/Desktop/destination

and it should work for what you want.

---

### Post by spupy on 2008-02-17
Try:
```
- C_folder/
```

@Sokertes:
He got his syntax right. He want to read exclude patterns from that file, so he uses exclude-from.

---

### Post by Sokertes on 2008-02-17
spupy < your right. I missed that part of the thread somehow. Call it dazed and confused or just blind.

---

### Post by geo909 on 2008-02-17
Thank you both for taking the time to answer this.

> **spupy said:**
> Try:
```
- C_folder/
```
.

You mean to write this line inside "exclude" file, right?
I did, and it was the same, C_folder (and the 'exclude') file was inside the destination folder after the synchronization...

@Sokertes: Yes, the --exclude=PATTERN had already worked for me but I want to make a list of multiple files and folders I would like to be excluded..

But I can't get it! As spupy said, the syntax seems to be right! Whatever sources I found from the internet was like that..
](*,)



Any further ideas?!

---

### Post by spupy on 2008-02-17
Hm, i made the same test and it is working for me! 
```
rsync -a --exclude-from /home/uibxn/test/source/excl /home/uibxn/test/source/ /home/uibxn/test/dest/
```

First make sure you have emptied the destination folder. ;)
Try to enter the exclude file just as i did - no quotes and a **space** instead of **=**. That seems to be the only difference!
EDIT: Nah, it's not that. I see no difference between my and your command. Make sure you copied the line i gave you correctly into the exclude file.

---

### Post by geo909 on 2008-02-17
YES, IT WORKED!
FINALLY!!

Thank you so much, you don't know how much time I spent on this!

The mistake was not the '=', but the '=' plus the space..
My God, I lost one hour of my life for a space, a damn extra space ](*,)
It also works like:
```
rsync -a --exclude-from=/home/uibxn/test/source/excl /home/uibxn/test/source/ /home/uibxn/test/dest/
```
Even with the quotes.

Thanks again!

                Cheers,
                      George

---

