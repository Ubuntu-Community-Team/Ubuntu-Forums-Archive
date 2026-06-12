---
title: "Multiple /usr directories"
date: 2007-06-28
forum: General Help
---

### Post by NelisWillers on 2007-06-28
Hi All,

Recently installed 7.04 on dual boot with XP. All works well.
The ext3 partition size on my notebook (internal)  is 4GB in size - have another ext3 partition on an USB external hard disk (60 GB).

Space on my internal 4GB partition is running out (only 450MB left) as I am installing packages.

I would like to install less-than-criticial packages on the external drive as well, but would like to keep the critical packages on the internal drive, so that I can boot and do some work without attaching the external drive.  i.e. I would like to keep some of the packages in /usr, but would also like to load some packages in /media/rdisk/usr (where rdisk is my external ext3 drive partition).

Is there a way to iunform the package manager to install some packages in another directory than /usr?
Or any other way yo achieve this objective?

thanks!

nelis

---

### Post by aquavitae on 2007-06-28
Are you sure its the /usr directory thats taking all the room?  I don't think I've ever seen it more than 1G, even with a lot of packages installed.  Before trying what looks like quite a complicated task (i.e. splitting /usr) maybe you should find out exactly where the space has gone.  There's a useful program called filelight which shows disk usage in nice little pie charts that may be handy.

If you do decide to split /usr, the way I would do it is to see if there's a way to just keep certain directories in /usr on the external (e.g. all the documentation) and then mount the external there.  You'd have to be careful what you decide to put on the external though so as not to break the system.  The downside is you would have to have the external plugged in whenever you install something.  Also, have a look at the mount documentation (man mount) - I seem to remember there's a way to mount to an existing directory or something.  Can't remember and I'm not at my linux pc at the moment so I can't check.

---

### Post by NelisWillers on 2007-06-28
Hi aquavitae,

thanks for your time. Sorry my response is so slow, I had to first complete a pretty major update/upgrade cycle, which took quite a while - I want to dabble with ntfs-g3 :-)

 I downloaded filelight and found the following:
/usr/lib = 770 MB
/usr/share = 808 MB
/usr/bin = 114 MB
/usr/src = 62 MB
/usr/include = 24 MB

which all adds up to a healthy 1.7 GB. The stuff I carry along include Boost, g++, Kdevelop, Kile and similar development/authoring tools. 

FileLight is quite useful, thanks for the tip! I see that OpenOffice is quite big at 207 MB. The other stuff is quite necessaery and cannot be removed.

Attaching the external drive when installing or when doing major tasks is not a problem. So I like your idea of moving some of the directories to the external drive.  Maybe I can move openoffice, emacs, since I would not be using it often. Then, moving doc should also work.

BTW I am new to Linux (used it a lot about 12 years ago, but not since).

Again, thanks for your time!

kind regards

nelis

---

### Post by aquavitae on 2007-06-28
Hmmm, seems I was mistaken about the size of /usr!  Unforunately the large ones are /usr/lib and /usr/share, which are the important ones.  The /usr/src is quite surprising though, usually there's nothing there.  The only src package I've ever downloaded is the kernel, and even that was only when I was using gentoo and had to compile the kernel manually.

A suggestion for setting it up:  put what you want onto the external drive is sensibly named folders.  Mount the drive to somewhere like /mnt/external-usr.  Use mount --bind or symlinks to link to the correct places on the /usr tree.  You've probably already thought of all this though!

---

### Post by NelisWillers on 2007-06-28
aquavitae,

>The /usr/src is quite surprising though, usually there's nothing there. 

Boost's source is mostly includes and is quite large, 21MB it seems!

>A suggestion for setting it up:  put what you want onto the external drive is sensibly named folders.  Mount the drive to somewhere like /mnt/external-usr.  Use mount --bind or symlinks to link to the correct places on the /usr tree.  You've probably already thought of all this though!

actually no, I am new to Linux and your advice opens a whole new world for me. 

from what you write, I get the impression the only reasonably safe way out is to use a larger partition.

Thanks so much for your time and trouble!

regards

nelis

---

### Post by aquavitae on 2007-06-29
Ok, I've never used boost - don't actually know what it is.... So what is it?

A large partition would certainly be easier, but I don't know about the safety of it if you're careful.

If you want a quick guide, this is what I would do:

Copy the relevant parts of the /usr tree to the external, keeping the full path (e.g. copy /usr/share/doc to the eternal as /usr/share/doc.

Rename the originals to backup names (e.g. move /usr/share/doc to /usr/share/doc~)

Edit /etc/fstab (as root) to set up mount points.  Set the external to mount to /mnt/external, and the subdirectories (i.e. /mnt/external/usr/share/doc) to mount to the right locations in /usr using the bind option.

Make sure that the mount point /mnt/external exists.

Use mount -av to mount the external and subdirectories.

Hope this helps!  I assume a bit of knowledge in editting /etc/fstab, but if you need it I'll be glad to help.  I think there's a way to do that step using a gui, but I've always found manually editing it to be faster and more reliable.

---

### Post by NelisWillers on 2007-07-03
Hi aquavitae

I was away over the weekend, only back in office today.

>Ok, I've never used boost - don't actually know what it is.... So what is it?

[http://www.boost.org/](http://www.boost.org/)
A peer-reviewed set of C++ libraries.  Some/most/all of the libraries that did not make it into the first C++ standard library, but that was considered worthy, was collected under the Boost banner. The idea is that in the upcoming C++ specification, some of these libraries will be included.  In fact, some of them are in the TR1 shortlist for the new standard.  

What is nice about Boost is that these are all peer-reviewed by some of the biggest guns in the C++ world today - many of which are serving on the C++ standardisation committee.  The other nice thing is that it is free.  One of the down sides is that it is quite big.  The compressed download is over 30MB, and as we saw last week, the include files for the library is 20MB once decompressed.  It is a large and comprehensive library with lots of goodies.  Some of which are highly specialised, but quite good.

I have been using some of the Boost libraries very successful for about five years now and is quite committed to it.

>A large partition would certainly be easier, but I don't know about the safety of it if you're careful.

maybe I need a larger disk and a larger partition.

>If you want a quick guide, this is what I would do: Hope this helps! 

thanks for your clear instructions. I will try it today.

> I assume a bit of knowledge in editting /etc/fstab, but if you need it I'll be glad to help.  I think there's a way to do that step using a gui, but I've always found manually editing it to be faster and more reliable.

Most of the times the GUIs are just in the way - they also make you lazy!
My memory from working in Linux for a year or two in the early 1990s is poor (but still there), but your description is quite clear and I have no problems with any of the details.

thanks for your care and support in this!

regards

nelis

---

### Post by aquavitae on 2007-07-03
I've never heard of boost, but I'll have a look at it!  I mostly use Qt for extra libraries.  Or write my own, but thats a pain.  Unfortunately I find Qt can be quite cumbersome though, so boost may be the answer.  Still have to use Qt for the widgets though I suppose...

A larger disk would be useful, bit not easy with a ntoebook, is it?

> Most of the time GUIs are just in the way - they also make you lazy!

Agreed.  Crazy thing is, the 'lazy' people who insist on GUIs usually take much longer to do something than the CLI addicts!

Thanks for telling me about Boost!

---

### Post by NelisWillers on 2007-07-03
Hi aquavitae

> I mostly use Qt for extra libraries.  Or write my own, but thats a pain.  Unfortunately I find Qt can be quite cumbersome though, so boost may be the answer. 

Boost is also cumbersome, but it is free and contains pretty much everything I need.

I don't use Qt simply since the commercial licence is so expensive (at least in my part of the world it is very expensive).

> Still have to use Qt for the widgets though I suppose...

Consider  [http://www.wxwidgets.org/](http://www.wxwidgets.org/).
It is free, mulitplatform, multi-language and has reached critical size.  I have not yet used it, but it appears very similar to MFC. Some of my colleagues have used it with great success.  What is very nice is that you can use the same interface from Python and C++ (learn once only).  On the down side, they are using built-in classes for things such as strings, since wxWidgets took shape before the ISO-C++ std::string was mainstream.

I bought the book and my next project will surely be wxWidgets!

>A larger disk would be useful, bit not easy with a ntoebook, is it?

my current disk is only 40GB - new machines come out with at least 80GB.

>Thanks for telling me about Boost![/QUOTE]

It is I that must say thanks for your valuable time....

regards

nelis

---

### Post by aquavitae on 2007-07-03
Yes, Qt's commercial license is expensive, but the programming I'm using at the moment is open source, so it doesn't matter too much.  If fact I'd rather that because I'm developing an inhouse program for my company, which I'd rather not be forced to leave behind if I move jobs.  If my work knows they'll have to pay a huge amount to keep it, they might be happier to leave it open source.  But I'm thinking of doing something commercial in my spare time, and perhaps wxWidgets would be better.

If you've got a 40G hd, can't you increase the space available for linux?  Its not great, but its not bad either.

---

### Post by NelisWillers on 2007-07-03
Hi aquavitae

>If you've got a 40G hd, can't you increase the space available for linux?  Its not great, but its not bad either.

there is no space left in the Windows partition!  All filled up with apps and data.  Windows remains my main OS, since I have built up a plethora of tools and utilities.  Linux comes second here, unfortunately. :-((

regards

nelis

---

### Post by aquavitae on 2007-07-03
Up to you.  I'd probably put some of the windows stuff on the external and get the complete ubuntu on the internal, but I suppose it depends on your situation.

---

