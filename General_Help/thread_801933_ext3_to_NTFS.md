---
title: "ext3 to NTFS"
date: 2008-05-21
forum: General Help
---

### Post by Garrulousbrevity on 2008-05-21
Hey, this is sort of silly.

So, I just purchased a 1TB external hard drive for myself, and it should be arriving in the mail tomorrow.  I'm using this to replace a 500GB hard drive that I have that's nearly full.  Currently, the 500GB hard drive is formatted to ext3, but I would like to give it to my girlfriend though, but she uses Vista.  I would like to format the drive to NTFS, but when I was poking around with Gparted to make sure I could do it, NTFS is grayed out and not an option.  

I tried to Google around to see if I could find an answer on my own, but I can't wade through all the requests of people trying to format from NTFS to ext3 and find an answer for my question.  

Thanks.

---

### Post by Living2007 on 2008-05-21
> **Garrulousbrevity said:**
> Hey, this is sort of silly.

So, I just purchased a 1TB external hard drive for myself, and it should be arriving in the mail tomorrow.  I'm using this to replace a 500GB hard drive that I have that's nearly full.  Currently, the 500GB hard drive is formatted to ext3, but I would like to give it to my girlfriend though, but she uses Vista.  I would like to format the drive to NTFS, but when I was poking around with Gparted to make sure I could do it, NTFS is grayed out and not an option.  

I tried to Google around to see if I could find an answer on my own, but I can't wade through all the requests of people trying to format from NTFS to ext3 and find an answer for my question.  

Thanks.

Have you tried using the LiveCD?

---

### Post by PmDematagoda on 2008-05-21
Install ntfsprogs and see if that helps you format the drive to NTFS using Gparted:-
```
sudo apt-get install ntfsprogs
```

---

### Post by Garrulousbrevity on 2008-05-21
> **PmDematagoda said:**
> Install ntfsprogs and see if that helps you format the drive to NTFS using Gparted:-
```
sudo apt-get install ntfsprogs
```

That did it, thank you much.

---

