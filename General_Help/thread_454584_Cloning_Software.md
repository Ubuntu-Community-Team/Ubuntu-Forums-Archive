---
title: "Cloning Software"
date: 2007-05-25
forum: General Help
---

### Post by Graham1 on 2007-05-25
Hi

I'm currently looking at cloning software. My choices so far are Partimage and Clonezilla. Just wondering what everyone else is using and which you prefer. Ideally, looking for a live cd version.

:)

---

### Post by psusi on 2007-05-25
I just use tar.  Tar up the whole system and put it somewhere safe.  If need be, you boot from the livecd, reformat the disk, untar, and reinstall grub.

---

### Post by Graham1 on 2007-05-25
> **psusi said:**
> I just use tar.  Tar up the whole system and put it somewhere safe.  If need be, you boot from the livecd, reformat the disk, untar, and reinstall grub.

That sounds complicated :(. What is tar? Not sure about the grub part. I should note that I have multiple partitions (other distro's). Would that make a difference?

:)

---

### Post by the lemming on 2007-05-25
> **Graham1 said:**
> Hi

I'm currently looking at cloning software. My choices so far are Partimage and Clonezilla. Just wondering what everyone else is using and which you prefer. Ideally, looking for a live cd version.

:)


I too would be interested in a cloning application for linux.

As for a Windows product I have been happily using Norton Ghost 2003 which has got me out of a shed load of problems.  The 2003 version can work in a windows environment or from a floppy disc if you can't boot into windows.

---

### Post by Graham1 on 2007-05-25
We use Norton Ghost at work (well, the dos version). Does Ghost not work with Linux?

:)

---

### Post by the lemming on 2007-05-25
> **Graham1 said:**
> We use Norton Ghost at work (well, the dos version). Does Ghost not work with Linux?

:)


No idea, but I'm willing to give it a go.

---

### Post by Graham1 on 2007-05-29
> **the lemming said:**
> No idea, but I'm willing to give it a go.

Please do, let us know how you get on. I haven't restored an image yet but at the moment, I'm preferring Partimage.

:)

---

### Post by ramjet_1953 on 2007-05-29
Ghost for Linux is the go!

You can download the iso image for Ghost for Linux (G4L) from here:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Make sure that you burn the iso as an iso, no just a data disk, on high quality media at a speed no greater than 4 X.

It can produce an exact 1:1 copy of a HDD, which means that you don't need to re-install GRUB.

It can even copy to a USB HDD plugged into a laptop.

Enjoy!

Roger :cool:

---

### Post by mcduck on 2007-05-29
I just use dd, as it's already installed and does everything I could ever want cloning app to do ;)

---

### Post by AnRa on 2007-05-29
You can use Partimage from the [SystemRescueCd](http://sysresccd.org/) live cd. :)

---

### Post by liberalist on 2007-05-29
Maybe GParted might help, although I am unsure (I am new to Ubuntu).

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

There is a Live CD version of GParted. My apologies if this is the wrong program.

---

### Post by Graham1 on 2007-05-31
> **ramjet_1953 said:**
> Ghost for Linux is the go!

You can download the iso image for Ghost for Linux (G4L) from here:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Thanks Roger :). Downloading at the moment and I'll give it a go ;).

:)

---

### Post by Graham1 on 2007-05-31
> **mcduck said:**
> I just use dd, as it's already installed and does everything I could ever want cloning app to do ;)

Is dd command line only?

:)

---

### Post by Graham1 on 2007-05-31
> **AnRa said:**
> You can use Partimage from the [SystemRescueCd](http://sysresccd.org/) live cd. :)

Using Partimage at the moment ;). I'm preferring Partimage as it only creates one file (image) where as Clonezilla creates many files. Actually, I'm using Partimage from Parted Magic LiveCD which also includes GParted. I'm also using SystemRescueCd too which includes other great tools.

:)

---

### Post by Graham1 on 2007-05-31
> **liberalist said:**
> Maybe GParted might help, although I am unsure (I am new to Ubuntu).

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

There is a Live CD version of GParted. My apologies if this is the wrong program.

Thanks for the suggestion :). GParted is used to manage partitions (i.e create, delete, move, etc) but unfortunately, doesn't allow you to clone them. It would be great to see one program that does both though.

:)

---

### Post by Graham1 on 2007-06-01
> **Graham1 said:**
> Thanks Roger :). Downloading at the moment and I'll give it a go ;).

:)

Hi Roger

Not sure if I did something wrong but the partition that I was backing up said that it was 118% through (still incrementing before I cancelled) and the partition size shown as backed up was actually bigger than the partition itself :confused:. The interface looked nice, easy to use but I was a little worried about what was actually being backed up.

:)

---

### Post by mcduck on 2007-06-01
> **Graham1 said:**
> Is dd command line only?

:)

Yes, it's CLI tool. I don't know if anybody has made a graphical interface for it.

---

### Post by Graham1 on 2007-06-05
> **mcduck said:**
> Yes, it's CLI tool. I don't know if anybody has made a graphical interface for it.

CLI scares me (a little). I think I'll stick with GUI type apps for the time being.

:)

---

