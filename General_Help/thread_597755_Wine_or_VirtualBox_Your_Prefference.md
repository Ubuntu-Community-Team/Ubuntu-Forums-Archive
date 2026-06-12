---
title: "Wine or VirtualBox Your Prefference?"
date: 2007-10-30
forum: General Help
---

### Post by Fidgel on 2007-10-30
I need to run Adobe CS2, Photoshop, Dreamweaver, and the rest of the package as well as a few other graphic programs and :-P Front Page.

Which will perform the best?
Which will require less RAM?
Easiest to manage?

THANKS for your opinions!
Fidgel ><>

---

### Post by MarinaraOfDeath on 2007-10-30
Depends on what works. I'd love to virtualize my current installation, but I nearly permanently borked my XP install trying yesterday. If I didn't have a busy semester I'd break out the external harddrive and take the time to make an image. Instead I just relearned how to launch IDL via wine, much faster to get back to work.

---

### Post by michaelzap on 2007-10-30
I don't believe there's any reliable way to make CS2 programs run in Wine (if I'm wrong, I will be very happy to be corrected). You can run these in VirtualBox or VM Ware, but you should be aware that you won't get nearly as good performance running a virtual XP machine as you would if you dual booted to use these apps. I dual boot (Ubuntu/XP) so that I can use Photoshop, Flash, and other Windows-only software when necessary, and fortunately I find I only have to boot into XP once every couple of weeks or so.

---

### Post by kjbuente on 2007-10-30
Personally, I'm an wine user. More configurable if you ask me. It does use a bit of the swap partition, but that is only because it loads the necessary M$ binaries there instead of RAM to give that space to your apps. I use CS2 in wine and I can't tell that is was not made for linux, though I'm making to move to GIMP.

---

### Post by L815 on 2007-10-30
I think Wine would be a simple solution in terms of work of installing. 
Although virtual box allows you to run anything you want on a complete windows core without worrying about running into problems in the future etc..

But that's just me. I don't have enough experience with Wine yet.

---

### Post by michaelzap on 2007-10-30
> **kjbuente said:**
> Personally, I'm an wine user. More configurable if you ask me. It does use a bit of the swap partition, but that is only because it loads the necessary M$ binaries there instead of RAM to give that space to your apps. I use CS2 in wine and I can't tell that is was not made for linux, though I'm making to move to GIMP.

How do you make this work? I didn't think that anything later than Photoshop 7 worked reliably in Wine. If there's a way to do it, I definitely want to try.

---

### Post by daengbo on 2007-10-30
In standard Ubuntu, my choice for running applications always follows this pattern
1. Gnome apps
2. GTK apps
3. Native Linux apps
4. Windows apps in Wine
5. Windows apps in an virtual machine.

This keeps my machine running as well as it can.

---

### Post by Fidgel on 2007-10-30
Pardon my ignorance, what does the acronym GTK stand for?

---

### Post by skywisenight on 2007-10-30
I would say from my experience having to use Photoshop every day:

- Install Photoshop 7.0 via Wine
- Install Windows XP or 2000 via VirtualBox (use  the lowest version of windows your software supports... lower always means less resouces for the most part) and install everything you will need into VirtualBox, CS2, Dreamweaver and what not.

I also have a dual-boot for really-really intensive work (like 150dpi poster work or complex Photoshop work) but I only have to go this route once a week or so.

The beauty of installing PS 7 under wine is that it loads faster and is quick and dirty for quick and dirty jobs (and will be far less intensive on your machine CPU and RAM wise), and then for the larger stuff or need feature from the newer versions fire up the virtual machine. (slower but certainly more reliable).

CS1+ just aren't very reliable under wine yet and the performance is pretty bad (coming from someone who has used Photoshop professionally (as in food on the table) for 8 years.)

Do a search on these forums for Winefix script to run your wine apps with, it seems to help out a bit for wine apps too.

---

### Post by skywisenight on 2007-10-30
> **Fidgel said:**
> Pardon my ignorance, what does the acronym GTK stand for?

The Gimp Toolkit - [http://www.gtk.org/](http://www.gtk.org/)

---

### Post by fjgaude on 2007-10-30
> **Fidgel said:**
> I need to run Adobe CS2, Photoshop, Dreamweaver, and the rest of the package as well as a few other graphic programs and :-P Front Page.

Which will perform the best?
Which will require less RAM?
Easiest to manage?

THANKS for your opinions!
Fidgel ><>

I'm a graphic designer and I'm sold on VMware Server. It's free and easy to install. See my signature.

---

### Post by Fidgel on 2007-10-30
>  				frank at [http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)
[SIZE=1][FONT=Arial]Homebuilt AMD 64 2X 4400+, 1.7 TB RAID5; Dell laptop E1505n; Shuttle AMD 64 3200+; 
VMware Server w/ WinXP Guest running  Xara Xtreme, Paint Shop Pro, and InDesign CS.[/FONT][/SIZE]

What version of Paint Shop Pro are you running in Wine?  I use 7 did you have to do anything special to make it work?

Fidgel ><>
[SIZE=1][/SIZE]

---

### Post by nowshining on 2007-10-31
I use VB for my windows fun, VB runs pretty fast even with 512mb ram and all I gave it is 60mb RAM, u can chose the amount of ram, but 60megs seems like that's the lowest XP will use.. :) also VB is again FAST and is even faster using XP in it than when XP was native.

---

### Post by fjgaude on 2007-11-01
> **Fidgel said:**
> What version of Paint Shop Pro are you running in Wine?  I use 7 did you have to do anything special to make it work?

Fidgel ><>


Version 9 and 11, just load it like you would in Windows from CD or file. Nothing special. All Windows programs are the same in VMware... it's just like you were in Windows because you are. <smile>

---

