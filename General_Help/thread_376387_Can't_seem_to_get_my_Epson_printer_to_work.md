---
title: "Can't seem to get my Epson printer to work"
date: 2007-03-04
forum: General Help
---

### Post by chris_n00b on 2007-03-04
Well I've been using Ubuntu for a few months (6.06 Dapper) and started to understand things. I felt that it would be a good idea for me to have a printer attached incase I need to print off a resume or letter etc...

Anyway I have an Epson C40S.  I have been to linuxprinting.org and have searched through a lot of threads but don't know if I'm making the error or not. I downladed what I think is the source code for the drivers from [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C40]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C40")

They list a C40, C40SX and C40UX. I downloaded the C40 and was gonna try the C40UX but I don't think it matters since its the same driver right? My C40 has only a USB port on the back by the way.

I downloaded the tar.bz2 file and then installed it like:

1. navigated to the directory. since it was on my desktop, I did cd /home/chris/desktop/gutenprint-5.1.0.tar.bz2
2. ./configure
3.make
4.make install

Is that it?  It still doesn't recognize my printer and can't print any test pages. I know the printer works since it was hooked up to a windows machine and printed fine.

Do I need to do something else? OR did I do it wrong? How do I uninstall and then reinstall? Im still new to Linux and dont know commands all that well yet. :(

---

### Post by paydaydaddy on 2007-03-04
Still a noob myself but from what I have done I think you need as your first command:

sudo apt-get install build-essential

Don't do anything on my say-so wait for one of the more knowledgeable people to jump in and confirm that I'm right. I found a lot of help installing my printer by searching the forums.

---

