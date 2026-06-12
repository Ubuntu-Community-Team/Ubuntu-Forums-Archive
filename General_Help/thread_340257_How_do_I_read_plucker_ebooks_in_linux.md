---
title: "How do I read plucker ebooks in linux?"
date: 2007-01-16
forum: General Help
---

### Post by Shay Stephens on 2007-01-16
I have been downloading and reading ebooks in the plucker format on my handspring visor, but today I got the itch to read one on the computer instead of the handheld.  Oddly (it seems to me) the plucker format is not readable by anything I have in Ubuntu.  I did some searching around and found a program called FBReader that does a fair-ish job of reading them, but nothing to write home about.

So my question is to those who may have figured this out already, how do I read a plucker ebook in Ubuntu?  Is there a better program than FBReader?  Plucker is a free and open format, I would have thought this would have been better supported.

---

### Post by element on 2007-01-22
Plucker is in the repos.

Do this in a terminal...

**sudo apt-get install plucker**

Then from the terminal run this...

**plucker your_file.pdb**

---

### Post by Shay Stephens on 2007-02-02
Sorry for the long delay, I went on vacation and just got back...

Ok, now I feel reallllyyyy stupid hehehe.  That was so obvious I can't believe I didn't think to do that myself.  A million thank you's for the tip, it works perfect.  In fact, I can right click on the file and choose "open with plucker" which I *also* can't believe I never tried.

---

### Post by Shay Stephens on 2007-02-02
An update.  Now I remember that I have tried that, but plucker is only showing part of the book.  Now I will freely admit I am probably doing something wrong here hehehe, but I can't get a whole book to be readable in pluck.

What does work however is a program called FBReader.

---

