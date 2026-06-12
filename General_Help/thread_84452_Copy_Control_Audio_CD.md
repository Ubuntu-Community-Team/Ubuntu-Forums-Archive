---
title: "Copy Control Audio CD"
date: 2005-10-31
forum: General Help
---

### Post by Txukie on 2005-10-31
Hello all,

I've purachased an original Coldplay Album X&Y, this album is excellent but it has an unwanted feature called Copy Control which basically doesn't allow me to play this CD on my computer as i can't even mount it, not even make a backup as i'm entitled to do by spanish law. Is there anything  can do about this?

---

### Post by slux on 2005-10-31
Maybe try it around in different CD drives and one might read it. I've heard some CD drives are able to do that effortlessly. I don't know if there are actual tools for ripping these but probably not for Linux at least.

I've been avoiding copy protected CDs but I had a similar experience with one that my sister had bought. You can of course illegally download it off the internet which seems a little backwards to me since the stupid thing was supposed to prevent it getting there on the first place.

---

### Post by crankcaller on 2005-10-31
Try the following.  Someone gave it as a reply to a post i had on /.
it's worked for me with copy protected cd's:

"I have never had difficulty with cdparanoia. Just change to a directory, place the CD in the drive and # cdparanoia -B. You get a set of .wav files which are easily dealt with {for i in *wav; do lame -h $i && rm $i; done}. Note that you will have to download and compile lame yourself {from a server in a country where maths patents are unenforcible}.

Back in the days of 2.4 kernels, you had to muck about with SCSI emulation, /etc/modules and append statements in lilo.conf; but all that finally changed with the advent of 2.6.

For some discs, you might need a drive of 12X or slower speed. This is because older, slower drives seem not to read all TOCs as soon as the disc is inserted; so are immune to "protection" methods involving bogus TOC entries."

---

### Post by Txukie on 2005-10-31
> Maybe try it around in different CD drives and one might read it. I've heard some CD drives are able to do that effortlessly. I don't know if there are actual tools for ripping these but probably not for Linux at least.

Im on a laptop, just one drive [-X 

> You can of course illegally download it off the internet which seems a little backwards to me since the stupid thing was supposed to prevent it getting there on the first place.

As i'm on Spain it's legal for me to do that, but still don't know why i should use my bandwidth (which costs money at the end of the day) to make full use of my rights.

---

### Post by 23meg on 2005-10-31
The latest generation of copy protection used by EMI won't even let you play the CD in Windows if it doesn't have the latest version of Windows Media Player installed and isn't connected to the internet.

[QUOTE=Txukie]  Is there anything  can do about this?[/QUOTE]

You can start by boycotting the RIAA member companies, which deprive you of those rights by using such incompatible and possibly privacy breaching copy protection.

---

### Post by Txukie on 2005-10-31
cdparanoia won't work for me either, it asks me if i have a cd in the dc drive......

---

