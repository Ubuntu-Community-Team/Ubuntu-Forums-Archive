---
title: "resize partition 14.04"
date: 2015-11-24
forum: General Help
---

### Post by tmy on 2015-11-24
Hello 
I had a 1 TB drive with 1 GB space left. I did a sector by sector to a new 2 TB hard drive.

Now I find I'm no better off as I need to resize to make use of the extra 1TB 

I need help to resize and take advantage of the 2 TB drive 

I have Gpart live on a disk but just don't know how to resize things, can anyone help please ?

regards 

tmy

---

### Post by yancek on 2015-11-24
The GParted Manual is at the link below.  Scroll down to the section entitled 'Advanced Partition Actions'.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by tmy on 2015-11-25
Hi yancek,
the manual is no help as I just don't get it  :-( while in ubuntu I can't look at the layout as it says "Unable to access location" "can't mount file" try to mount it says "Unable to access"

So to recap I had a 1 TB drive which warned it was almost full

I bought a new 2 TB drive 

did a sector by sector transfer to the 2 TB drive 

Everything works ...but I can't access the extra 1 TB 
Please see my drive layouts 
thank you everyone 

regards 

tmy

---

### Post by yancek on 2015-11-25
Your last post shows that you are using LVM (Logical Volume Management) so the standard method of resizing won't work.  I understand that it is possible to do so with GParted but I have never used LVM so have no suggestions.   I'm surprised to see an Extended partition on the drive as my understanding was that LVM would use the entire dirve other than a boot partition but I'm not sure about that.  You could take a look at the link below or do an online search for 'resize LVM partition'.

[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

---

### Post by tmy on 2015-11-25
Thank you yancek.
I'm doomed then to have a wasted 1 TB drive that I can't access  :-(

as I have explained before this whole thing has me baffled

I was hoping someone could help me 

because of my ignorance reading manuals etc won't help as it doesn't mean anything to me

I just hope someone can save me 

help everyone please help 

regards 

tmy

Hi everyone,
what started off as a simple operation has turned in to a complete joke

I can't believe it is so complicated to run out of room on a drive transfer the whole lot to a bigger container and still end up with a load of messing to access the whole of the disk ?

It is no wonder the take up is so poor this spoils a great OS 

getting an answer is even harder, no one knows, so the whole ubuntu community is unable to advise on a way to sort this issue out ? 

amazed and frankly bemused.
if it was a Windows machine I would have taken it to one of millions of shops to have it done

but with ubuntu I have to post and hope someone has an answer to this incredibly difficult issue

oh well too hard basket, road block, in pass, go back to start  :-(

---

### Post by tmy on 2015-11-28
Thanks everyone,
I'm shocked this has baffled the whole ubuntu community, but not surprised by the response.

Thank you to those that took time out to reply and assist, I'm frankly perplexed that there seems to be no way to fix my issue

back to the drawing board thanks 

tmy

---

### Post by QIII on 2015-11-28
Hello!

It hasn't baffled the whole community.  If you look at the first answer [here]("questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume"), you'll find a very detailed process for doing it.  You'll need to know some information about your groups and volumes.

LVM adds some level of complexity to resizing.

---

### Post by tmy on 2015-11-29
Hi Q111,
the problem is I set the pc up using default settings I have zero clue about LVM etc ( the link 'Here' did not work ) 

I just asked what I considered a simple question 

I had a 1 TB drive that ran out of space

I did a sector by sector to a bigger drive ( 2 TB )

now I find I can't use the other 1 TB 

I asked how can I make ubuntu use the whole drive ?

It is absolutely pointless directing me to a how to as it means nothing to me 

I hoped someone could take time to help 

that is all I wanted 

I love ubuntu but when this type of thing crops up I'm lost

anyone able to help would be greatly appreciated

I thank everyone who has responded

regards

tmy

---

### Post by yancek on 2015-11-29
The LVM option is not the default setting.  If you have an operating system currently on a computer, you should have 5 different options.  The first and default is "Install Alongside" and one of the 4 other options would be LVM so it would have been necessary to select that.  With a machine with no OS, the simplest option is Erase Disk, if you wanted more control over the install the best option would be Something Else which is the manual install.  LVM has its uses but is not often used on a standard Desktop install and many of the members here are just regular users so most of us won't know any more about LVM than you do.

If you go to the "howtogeek" link I posted earlier and scroll about half way down the page, it explains how to resize and LVM partition.  If that doesn't make sense to you, you might try posting a new thread specifically asking how to resize an LVM partition because the process and commands are very different than what most users know about resizing partitions.

---

