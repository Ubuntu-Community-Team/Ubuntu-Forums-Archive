---
title: "Burn XBOX 360 backup images on Ubuntu?"
date: 2007-10-09
forum: General Help
---

### Post by RAFAMP on 2007-10-09
Hello

 I have a backup image on my computer that i have done with CloneCD, i wonder how to burn it? i have a .dvd image, with layer breaks sections...

 I have seen [this]("http://www.bross.eu/2007/08/29/how-to-burn-xbox-360-backups-in-linux/") article but it seems kinda complicated...

 Does K3b works fine with xbox 360 images?

---

### Post by Phearicle on 2007-10-10
i have the same problem

---

### Post by RAFAMP on 2007-10-10
so anyone knows how to solve this?

---

### Post by fearevilleet on 2007-10-10
I wonder if nero linux would be able to handle it. I bought nero because I had an issue similar to your with burning games.  i

---

### Post by Mantorp on 2007-10-13
> **RAFAMP said:**
> Hello

 I have a backup image on my computer that i have done with CloneCD, i wonder how to burn it? i have a .dvd image, with layer breaks sections...

 I have seen [this]("http://www.bross.eu/2007/08/29/how-to-burn-xbox-360-backups-in-linux/") article but it seems kinda complicated...

 Does K3b works fine with xbox 360 images?



K3b can't burn xbox images sorry! I use the growisofs method from the article and works fine for me. Never had a problem. BTW It's not so complicated!

---

### Post by McScruff on 2007-10-14
lo all,

its really easy to do. 

My Guide

open terminal

change directory to the same location the ISO file is located

type:
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=IMAGE.000

change /dev/dvd to your dvd burner, change IMAGE.000 to your iso name

Press enter!!! and OMG IT BURNS!!!!

Edit:
forgot to add, the .dvd file only contains the layer break and iso name,  the layer break = -use-the-force-luke=break:1913760  (always the same in all .dvd files) and the iso name at the end

---

### Post by ohzopants on 2008-01-29
Sorry for reviving an old dead thread.

I tried to burn one of my backups last night using this technique and it burned the disc at 4x instead of 2x.  Did I misunderstand the "-speed=2" parameter?  The resulting disc was read ok by my xbox, but it was very, very slow and I suspect that it has something to do with the burn speed (particularly since my media is only good up to 2.4x).

Also, does this change the book-type correctly form dvd+r to dvd-rom?  If not, how do I do this?

Thanks all.

---

### Post by ryrules1 on 2008-01-30
wait so do i need to drag and drop my image (iso file) into the dvd drives nautilus or do i have to type in exactly where the image is located on my computer. if so could you give me an example of this.? also do you know of any programs for backing up games onto your harddrive. I have an  drive that reads xbox 360 games.

---

### Post by oddword on 2008-03-01
Yo McScruff you are the best. I've been on Ubuntu for like 2 weeks and it is Heaven! i can't believe how easy it is to burn a 360 disc. Thanks again man, You rule!

 I don't miss my Mac Pro whatsoever. I sold it and bought a 
p4 2.4ghz quad 
Asus p5k Black Pearl
4 gb of ram
xfx geforce 8800gts 512mb
500gb seagate with 32mb cache
and Ubuntu!

---

### Post by rahduke on 2008-03-04
A quick follow up to what ohzopants said.

Do you need to set a booktype to burn w. linux? If so is there a terminal command?

---

### Post by rahduke on 2008-03-06
If anyone else comes across this thread that is as dumb as me:

 If you cant figure our what the terminal path to your DVD is:

Goto Places----> Computer

Browse the filesystem and go into the Dev folder

You will see a link to your dvd drive right click the file and goto properties.


The Link Target will be the path to your drive

I.E. 
/dev/scd0


I'm sure there is an easier way to find this out, but i'm half retarted so.

---

### Post by Moezzie on 2008-03-10
This all seems really great.
So what would i need to actually create the image? Seems like there would be some kind of copy-protection in the disks. Would i need any special software for that?

*edit*
What kind of dvd should the game be bruned on. I heard that normal DVD-R didnt do it. It has to be DVD+R, is that right?

---

### Post by stumpalump on 2008-03-14
> **rahduke said:**
> A quick follow up to what ohzopants said.

Do you need to set a booktype to burn w. linux? If so is there a terminal command?

Works perfectly. No need to set book type for me. This should be changed to a HOWTO

---

### Post by ohzopants on 2008-03-14
Moezzie:
You need to use dual layer DVD+Rs.

---

### Post by Alcopops on 2008-04-18
> **rahduke said:**
> A quick follow up to what ohzopants said.

Do you need to set a booktype to burn w. linux? If so is there a terminal command?

I think that the "-dvd-compat" flag in  the command sets the booktype to dvd-rom. 

Cheers,

Jaime

---

### Post by kennox on 2008-05-13
Thanks heaps. worked like a charm.

---

### Post by Yamthief on 2008-05-23
McScruff's response seems to work like a charm, another alternative to fixing the problem is to burn using ImgBurn [ [http://www.imgburn.com](http://www.imgburn.com) ] under Wine (which i'm sure everyone knows how to use already?)

@ohzopants - the speed you burn a disk at won't effect the speed it reads at :???:
If the game takes ages to load, it's either to do with the speed of the DVD drive in your xbox or the quality of your disks?

---

### Post by Ev1L on 2008-05-29
> **Yamthief said:**
> McScruff's response seems to work like a charm, another alternative to fixing the problem is to burn using ImgBurn [ [http://www.imgburn.com](http://www.imgburn.com) ] under Wine (which i'm sure everyone knows how to use already?)

@ohzopants - the speed you burn a disk at won't effect the speed it reads at :???:
If the game takes ages to load, it's either to do with the speed of the DVD drive in your xbox or the quality of your disks?
damn, i ruined the second DVD with McScruff's method, here's the error :(

 1601732608/7835492352 (20.4%) @2.4x, remaining 32:22 RBU  99.9% UBU  75.0%
 1612677120/7835492352 (20.6%) @2.4x, remaining 32:17 RBU 100.0% UBU  89.6%
 1613922304/7835492352 (20.6%) @0.3x, remaining 32:26 RBU 100.0% UBU  75.0%
 1613922304/7835492352 (20.6%) @0.0x, remaining 32:42 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=c0650h failed with SK=4h/ASC=03h/ACQ=00h]: Input/output error
:-( write failed: Input/output error

Any idea?

I tried ImgBurn with Wine but it can't see the DVD writer, then I tried with Win XP in virtual image, but ImgBurn can't take the ISO either in a shared folder from Ubuntu or from USB HD :(

Everything worked flawlessly in Vista before, so it's not a writer or DVD problem...

Please help

---

### Post by Ev1L on 2008-06-21
****!

 6884687872/7835492352 (87.9%) @2.4x, remaining 4:55 RBU 100.0% UBU  91.7%
 6895796224/7835492352 (88.0%) @2.4x, remaining 4:52 RBU 100.0% UBU  91.7%
 6897664000/7835492352 (88.0%) @0.4x, remaining 4:51 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=336440h failed with SK=4h/ASC=03h/ACQ=02h]: Input/output error
:-( write failed: Input/output error

---

### Post by CanBert on 2008-06-24
Yes K3B can be used to burn 360 games:



Goto settings -- configure k3b

Click programs on the left side.

Click user parameters tab

Click growisofs (beside the word under parameters)

In the box put:  -use-the-force-luke=break:1913760

Click apply or ok

And burn the iso file, ignore the dvd file.

---

### Post by Ev1L on 2008-06-24
> **CanBert said:**
> Yes K3B can be used to burn 360 games:



Goto settings -- configure k3b

Click programs on the left side.

Click user parameters tab

Click growisofs (beside the word under parameters)

In the box put:  -use-the-force-luke=break:1913760

Click apply or ok

And burn the iso file, ignore the dvd file.
does it automatically choose growisofs to burn DVD+R?

and what do you think about the error i get (see previous posts)?
it happened using plain growisofs, thus i expect i'll screw another DVD...

---

### Post by arcinthesky on 2008-06-27
I have a question. If I want to read a dvd that has layer break (ex. 360 backup-ed game to iso) to an iso, how can I do that with growisofs?

---

### Post by fmonjaraz on 2008-07-01
So the thing is that you can burn the game as long as its a dual layer dvd-r? Will the game be playable in the 360?

---

### Post by fmonjaraz on 2008-07-01
and with any dvd burner??

---

### Post by nanospire on 2008-07-04
To ensure greater success use better media.  Verbatim works great for me.  I am told that Maxell is also very good.

---

### Post by fearevilleet on 2008-07-05
Has anyone experienced issues closing dvd images after upgrading to hardy using the cli method?

---

### Post by Ev1L on 2008-07-06
> **fearevilleet said:**
> Has anyone experienced issues closing dvd images after upgrading to hardy using the cli method?
i passed from vista (working), to hardy cli (wasted 3 DVD) to hardy k3b (successfully burned one)

---

