---
title: "Mounting an UDF DVD-ROM"
date: 2007-03-24
forum: General Help
---

### Post by pieroxy on 2007-03-24
Hi,

I have been burning big files onto DVD-ROM lately (filers that are > 2GB). k3b gives me the warning that the DVD will be burned as UDF and I need to make sure I mount it as UDF in order to be able to  read the file completely. And it works. What bugs me is that I have to type

sudo mount /dev/hdc -t udf /media/cdrom0

by hand every time.

If I put "UDF" as the fs type in my fstab then I cannot mount pure iso9660 cds anymore. if I put "udf,iso9660" everything is mounted as iso9660, and files over 2GB are only readable up to 2GB of data.

Is there a way of telling fstab that I want it to try and mount the CD/DVD as udf, and if that fails, mount it as iso9660? Or can it detect it automagically?

Thanks

---

### Post by goghgoner on 2007-03-29
I am no help at all but thank you. I had burned some UDF DVDs and had yet to figure out how to access them. Did you look at UDFTOOLS at all? I installed the package and was looking for instructions but haven't got back to it.

---

### Post by ling4a6 on 2007-04-19
I had the same problem as you. The DVD's were burned correctly in the UDF format but refused to auto mount and I had to do it via the terminal every time.

You can solve the problem by changing your fstab from:

/dev/cdrom        /media/cdrom0   **udf,iso9660** user,noauto     0       0

to 

/dev/cdrom        /media/cdrom0   **iso9660,udf** user,noauto     0       0

---

### Post by jacksonz123z on 2007-04-20
Yes, brilliant, that fixed the problem.  Many thanks.  How did you work that out?

---

### Post by jacksonz123z on 2007-04-28
Well, actually changing to iso9660,udf stops iso's from working.  Best to change udf,iso9660 to auto.

---

### Post by Laryllan on 2007-05-04
Had the same problem here.

Setting "udf,iso9660" in /etc/fstab to "auto" did the trick for me.
My drives can read both now, UDF and ISO.

Bug or feature?

---

