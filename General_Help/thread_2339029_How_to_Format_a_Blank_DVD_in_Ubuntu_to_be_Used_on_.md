---
title: "How to Format a Blank DVD in Ubuntu to be Used on a Win 7 Computer as UBS Flash Drive"
date: 2016-10-04
forum: General Help
---

### Post by John_Patrick_Mason on 2016-10-04
Hey guys,

Today, I decided to do clean install of Windows 7 on my  laptop. I managed to install all critical drivers, but unfortunately  I'm still missing some drivers, so I have to go back on the  manufacturer's websites and download the missing drivers there.  Unfortunately, for now at least, the USB ports  on my laptop are  inoperable, as well as the internet, because of the missing drivers, so I  have to rely instead on the DVD drive to install the remaining drivers.  The problem is that every time I add the missing drivers to a blank dvd  on my other computer (Ubuntu) and pop in the dvd into my laptop,  Windows 7 tries to reformat the dvd thereby erasing the drivers that  were added. When I pop in a dvd that has already been formatted by  Windows into the dvd drive of my Ubuntu machine I get an error message  that says "the destination is read only" so I can't add the missing  drivers to a dvd that has been formatted by Windows under my Ubuntu  machine. Is there anyway to add files to a blank dvd in Ubuntu that has  already been formatted by a Windows machine?

---

### Post by T2uiYKb7 on 2016-10-04
Brasero is extremely buggy (Google it, endless cases of failed burns.)

I don't understand why it's still the default burner app in Ubuntu, it's failed burns can mean people losing irreplaceable photos and documents.

Try installing K3B or Xfburn and see if they work.

---

### Post by John_Patrick_Mason on 2016-10-04
I'll try K3B and Xfburn and see if I have any better luck with those, but just so you know, I'm not trying to burn anything on the dvd, I'm only trying to transfer .exe files on it. In other words, I'm using it purely as a storage medium, much as someone would use a USB flash drive to transfer files from a work PC to a home PC.

---

### Post by T2uiYKb7 on 2016-10-04
True but it's still changing the DVD the same way "burning" to a DVD would.

This will probably sound very patronizing and that's not my intention but are you sure DVD hasn't been closed?

Is it possible to check on a Mac/Windows or a live version of another Linux distro?

If it's been closed it will consider it's self read only and you'll need to get another DVD. 

Is it re-writable?

---

### Post by QLee on 2016-10-04
> **John_Patrick_Mason said:**
>  When I pop in a dvd that has already been formatted by  Windows ... Is there anyway to add files to a blank dvd in Ubuntu that has  already been formatted by a Windows machine?

If Windows tries to "format" a blank DVD, I'd guess it's using UDF.

See if this helps:
[http://askubuntu.com/questions/359264/how-to-open-udf-volume](http://askubuntu.com/questions/359264/how-to-open-udf-volume)

Like the others, I would expect the Ubuntu burning applications to be able to create a Windows readable DVD but I don't use Windows and haven't since Windows98 so I can't help with that.

---

### Post by John_Patrick_Mason on 2016-10-05
I tried K3B and it solved the problem. All what I had to was "burn" the files to a blank DVD. Whatever. I guess I'm more used to using USB flash drives which automatically work without having to reformat anything. Thanks for all the help.

---

