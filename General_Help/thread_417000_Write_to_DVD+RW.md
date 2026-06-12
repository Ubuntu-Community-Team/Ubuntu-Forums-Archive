---
title: "Write to DVD+RW"
date: 2007-04-21
forum: General Help
---

### Post by AllanP on 2007-04-21
I can't figure this out. I have a DVD=RW rewritable DVD and I am told it is a "read only file system". I have tried in terminal as SU to change it to writable with the same results. I really want to delete a file on the DVD but, still get the message "read only file system"

---

### Post by paulieman on 2007-04-21
I have this on my TODO list of things to check out...  I bookmarked this URL, maybe it will help you?  I can't offer any direct solution, but thought I would share this.

[http://packages.ubuntulinux.org/hoary/utils/dvd+rw-tools]("http://packages.ubuntulinux.org/hoary/utils/dvd+rw-tools")

---

### Post by codingmaster on 2007-04-21
Hello!

You cannot mount a dvd+/-rw as writable, you will need a special filesystem, e.g. UDF.

What you need is a burning tool, you can try:
gnomebaker
or
k3b

dvd+rw-tools will be needed to provide support for your dvd drive to those tools.

Best regards, Georgy Berdyshev

---

### Post by paulieman on 2007-04-21
> **codingmaster said:**
> 

What you need is a burning tool, you can try:
gnomebaker
or
k3b

dvd+rw-tools will be needed to provide support for your dvd drive to those tools.



Installing gnomebaker itself won't allow you to use dvd+rw functionality, we would still need to install the dvd+rw tools?  

Thanks for the help!!

---

### Post by codingmaster on 2007-04-21
Hello!

You need the dvd+rw-tools!

gnomebaker has dependencies set to dvd+rw-tools
<- so those will be intsalled.

Just go for gnomebaker or k3b :)

Best regards, Georgy Berdyshev

---

### Post by AllanP on 2007-04-21
I can't get Gnomebaker to do much of anything. I do as the program says: drag files to Gnomebaker and then burn; no dice; get the failed to burn to disk. One odd thing though is it asks me to insert a disk (DVD already in burner) and the drawer to the CD writer opens. I know the DVD writer is working ok as I've burned many ISO's with no problem.

---

### Post by Toxicity999 on 2007-04-21
you seem to just be mistaken about what a rewritable disc really is, you may have used programs which make it seem as though you're simply deleting something from the disc, or something, but it's really not as simple as just mounting it, and dragging things to and fro with nautilus, you need to use a real burning program which supports dvdrw media, which you can find around with an easy search.

It seems as though you're using gnomebaker, but you're trying to make a new disc on top of the old disc, you have to wipe the old one first, or just add to it with the tools there, play with the menu options.

---

### Post by AllanP on 2007-04-21
Thanks I'll keep trying. It's not a problem as the most I do with DVD's is burn ISO images. I have other means of backup. I just thought it would be as simple as drag and drop.

Thanks again, Allan

---

### Post by AllanP on 2007-04-22
> **Toxicity999 said:**
> you seem to just be mistaken about what a rewritable disc really is, you may have used programs which make it seem as though you're simply deleting something from the disc, or something, but it's really not as simple as just mounting it, and dragging things to and fro with nautilus, you need to use a real burning program which supports dvdrw media, which you can find around with an easy search.

It seems as though you're using gnomebaker, but you're trying to make a new disc on top of the old disc, you have to wipe the old one first, or just add to it with the tools there, play with the menu options.

I forgot I was in Feisty and I can't even burn an ISO. So something is haywire here. This by the way is the first problem encountered with the new OS. I switched to another system (Xandros) and was able to assomplish evertying there. I blanked the DVD and copied files to it; no problem. Not a bad  system actually.

---

### Post by lefty.crupps on 2007-04-25
I am also in Feisty (Kubuntu) and cannot burn any ISOs nor data to disk, not even the data to an ISO file.

---

### Post by AllanP on 2007-04-25
Same here. I actually went back to Edgy for a bit; no problem there. I did however have another problem that for some reason affected many unrelated issues. I had one bank of memory that I discovered to be faulty and was giving me problems. I'll get more serious about this issue after I do my little upgrade; changing MB, processor and memory over the week-end.

Regards, Allan

---

### Post by peterthewolf on 2007-05-21
toxicity999

Instead of a vague comment about searching around for dvdrw why not cite a working example because my searching cannot find such a beast.

---

