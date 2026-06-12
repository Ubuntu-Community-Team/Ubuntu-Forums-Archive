---
title: "making an iso image from scratch?"
date: 2008-03-31
forum: General Help
---

### Post by ElTimo on 2008-03-31
ok here's my problem:

my school offers free copies of Windows XP. "Great!" you say, "And?"

they only offer it as a self-extracting exe. 
as such, I have all the files that belong in an iso, but i have no idea how to get them there and make it bootable so i can use it with kvm.

any help at all would be wonderful.

---

### Post by Slushdoot on 2008-03-31
To simply make an .iso image from files in a directory use ```
mkisofs -o ~/Desktop/cd.iso ~/Desktop/extracted/directory/
```Where the first bit is where you want to save the .iso image, and the second is the location of the extracted files.

I assume that it would then be bootable,  but you might want to check it in a VM like VirtualBox first.

---

### Post by ElTimo on 2008-04-01
That's actually what i want the iso for :-P I'm trying to make an XP virtual machine so i can run Dreamweaver, and I found a tutorial on how to do seamless windowing with kvm. The only thing is that every iso i've tried (be they legal or not) has frozen at some point during the second stage of installation. I did find a working ISO though, although it wouldnt work with KVM.....but i'll save that for another post ;) Thanks for your help though I was trying to figure out how to use mkisofs on my own and nearly exploded into a thousand kittens.

---

