---
title: "I want to create partitions."
date: 2016-03-19
forum: General Help
---

### Post by huzaifa2 on 2016-03-19
Hello.

Previously I was a windows 10 user and I installed ubuntu ( It was stupid of me to select the '2nd option' that would erase the whole hard disk, I thought it would just erase the 'C' Drive completely so no more windows...)
So now I am  I am with only one partition and it is messy... I am new to ubuntu ofcourse. Never have tried any linux distros before. Before installing ubuntu I tried it first, felt nice. And then I did a install ( in a stupid way )

I don't mind loosing the data, it was mostly movies that I have already seen, and a few other applications that I often used. 
But the problem for me is, I want to have partitions so that I can organize is better. Or is there a better way to organize 'My Computer'
Like I said, I am a windows user making a jump to linux. I tried searching in google, but in vain. 

To give a better understanding of what I mean.
Is this.
[IMG]http://imgur.com/a/2NJEr[/IMG]
[http://imgur.com/a/2NJEr](http://imgur.com/a/2NJEr)

Thanks.

---

### Post by v3.xx on 2016-03-19
It is not your "My Computer" you want to organize, but your "Home Directory".  That is where you keep all files, folders, movies, pictures...

If on the other hand you want smaller partitions for saving the above (a data partition), then you do need to partition.

[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by huzaifa2 on 2016-03-19
> **v3.xx said:**
> It is not your "My Computer" you want to organize, but your "Home Directory".  That is where you keep all files, folders, movies, pictures...

If on the other hand you want smaller partitions for saving the above (a data partition), then you do need to partition.

[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)


Thanks for the reply. 
I have a 500gig HDD.

So what I want to do is create 3 partitions.
Like A, B, C
A for system files (100 gigs)
B for movies and pictures(200 gigs)
C for misc files(200 gigs)

Is this possible? I am confused with the 2nd link you have given me.
I opened the first link 
and it said that you have to do it while doing a fresh install of ubuntu?
Can it not be done after already installing it?

Thanks.

---

### Post by v3.xx on 2016-03-19
It is possible to move the "home directory" to its own partition.  I think this was what you were reading about.  Being new to linux, I would not suggest trying to partition your home.

A for your current install (you call it system files) 100G will give you a lot of space.

B&C could be combined for everything else and you can automount this partition at boot.

---

### Post by yancek on 2016-03-19
If you want to create a separate partition for data you can do that.  If you want to create several separate partition for different type os data as you indicate in your post above, you  can also do that.  Do it with the GParted Partition Manager which is on the medium you used to install Ubuntu.  Boot it and open a terminal and type the following to open it:

```
sudo gpartede
```

A link to the GParted Manual giving all the information you want to do this is below.  Check the Index for the appropriate section.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

Moving your /home directory and sub-directories is possible but it is going to very problematic for a new user.  Given what you indicate you want, you already have a partition for your system files so create two partitions,  one for your movies and pictures and another for miscellaneous files.  The Manual above explains the whole process in detail but if you have questions, post them here.

---

