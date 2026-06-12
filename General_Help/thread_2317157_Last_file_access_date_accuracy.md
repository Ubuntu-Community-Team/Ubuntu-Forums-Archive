---
title: "Last file access date accuracy"
date: 2016-03-14
forum: General Help
---

### Post by MibunoOokami on 2016-03-14
Hi all,

I'd like to know if there's a more accurate way of viewing when a file was last accessed? When I use ```
stat filename
``` almost all of the files are being labelled as having been viewed on the 9th of March 2016 and those that aren't have today's date of 13 March 2016. I know for a fact the files I was trying to see the access date of weren't accessed in the past 12 months.

The reason I want to have an accurate date line is so I can delete files that haven't been used over a certain period of time in order to reduce the amount of stuff on my machine.


As usual you have my thanks in advance for any advice.

---

### Post by ajgreeny on 2016-03-14
Last accessed by whom?

If you look at a file in your home that you know you have not accessed for a long time you should see a date from that time, not the current date.
If, however, you are looking at files in the root filesystem many of those will have been accessed by the system without your knowledge, eg look at **stat /etc/fstab** and you will get output which will show the last time you booted the system as that is when the file was accessed.

Here is output in my system for one of my files showing an old date and for fstab showing todays date and time of booting the computer.

My file```
Access: (0664/-rw-rw-r--)  Uid: ( 1000/  ajgreeny)   Gid: ( 1000/  ajgreeny)
Access: 2015-06-11 16:47:38.414354724 +0100
```
fstab```
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2016-03-14 11:43:12.541625795 +0000
```

---

### Post by MibunoOokami on 2016-03-15
Nope, still getting 06 March 2016 as the last access date (09th march was a mistake) below is the output of a file that hasn't been touched since late 2014.
```
  Size: 435569        Blocks: 856        IO Block: 4096   regular file
Device: 806h/2054d    Inode: 1971514     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     mno)   Gid: ( 1000/     mno)
Access: 2016-03-06 07:40:46.478018870 +1300
Modify: 2015-02-19 17:19:28.464593337 +1300
Change: 2015-02-19 17:19:28.544593336 +1300
 Birth: -
```

Edit: One possibility I just thought of is when I back up, I run Rsync using sudo... I'll back my machine up and double check the dates tomorrow.

---

### Post by mcgess on 2016-03-15
Hi

Just a couple of thoughts, do you ever run any recursive searches, grep modifies access dates. Or how about clamscan?

Martin

---

### Post by MibunoOokami on 2016-03-16
> **mcgess said:**
> Hi

Just a couple of thoughts, do you ever run any recursive searches, grep modifies access dates. Or how about clamscan?

Martin

I don't normally use terminal for doing any searches and I've never heard of clamscan. The only thing I can think of again is Rsync, that uses the recursive feature for backing up. I haven't been able to test my theory yet because my storage device is showing up as full again.

That is unless running fslint had something to do with showing the odd access dates on untouched files. That might fit the time frame too.

---

### Post by mcgess on 2016-03-16
I haven't used fslint, but from the description of using it to find and remove duplicate files on howtogeek, it looks like it would entail reading every file you have which would mean all your access times would be updated.

---

### Post by MibunoOokami on 2016-03-18
> **mcgess said:**
> I haven't used fslint, but from the description of using it to find and remove duplicate files on howtogeek, it looks like it would entail reading every file you have which would mean all your access times would be updated.

OK that'll explain why nearly all my files had the same access date and time. Thanks for your help.

---

