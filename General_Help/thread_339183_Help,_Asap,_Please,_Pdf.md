---
title: "Help, Asap, Please, Pdf"
date: 2007-01-15
forum: General Help
---

### Post by Elena678 on 2007-01-15
i have a odt file, with imigas, i would like to convert it to PDF, becouse you need to have the possibility to see it in windows, but it's 11mb big, and i only can send 10mb with hotmail, i trued to put it in a zip, but it still 11 mb, how can i compress it???

thanks

---

### Post by mvaniersel on 2007-01-15
Do you want to convert the file to pdf first, and then send it? Or do you want to send it, and then convert it?

Usually a pdf can get a lot smaller when you compress it, are you sure that you didn't make a mistake there?

If you're reasonably proficient with the command line there is a command called "split" with which you can split a file in several pieces, and "cat" with which to put it together again. See "man split" and "man cat" for more info.

---

### Post by Elena678 on 2007-01-15
it is allready an pdf, but can't i use gzip or somthing like that, if yes, how do i need to do, i don't understand the program

thank

---

### Post by peabody on 2007-01-15
> **Elena678 said:**
> i trued to put it in a zip, but it still 11 mb, how can i compress it???

thanks

hmm, odd, while certain file types don't compress well (mp3, jpeg, etc. since they're already compressed) a document should certainly shrink.  I always gzip from the command line, "gzip filename" is all you need.

---

### Post by Elena678 on 2007-01-16
> **peabody said:**
> hmm, odd, while certain file types don't compress well (mp3, jpeg, etc. since they're already compressed) a document should certainly shrink.  I always gzip from the command line, "gzip filename" is all you need.

yea, it's 100 kb smaler :P

but thanks, i will try somthing else :)

greetings

---

### Post by peabody on 2007-01-16
Hmm, it should certainly shrink more than just 100k.  My guess is that whatever is converting the document to pdf is doing it by making each page an image.  That's a bad way to do it as you've seen as it blows up the file size.

---

