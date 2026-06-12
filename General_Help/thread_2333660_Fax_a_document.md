---
title: "Fax a document"
date: 2016-08-11
forum: General Help
---

### Post by 4kh3RAm on 2016-08-11
I would like to  fax a document.

I have a Linux capable modem.

I installed Efax and it's front end, but can not find a menu item for it.

Do I need something else ?

Trying to fax from a console.

From a console.

```
efax
efax: Thu Aug 11 21:05:21 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: Thu Aug 11 21:05:21 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 05:21 compiled Jun 21 2006 04:57:11
efax: 05:21 Error: can't open serial port /dev/modem: No such file or directory
efax: 05:21 done, returning 2 (unrecoverable error)
```
I think this is my modem.

But I do not understand the example below it.
     
```

Bus 003 Device 005: ID 0572:1329 Conexant Systems (Rockwell), Inc. 

Sending fax files

The following command will dial the number 222-2222 using tone dialing  and send a two-page fax from the TIFF-G3 files letter.001 and letter.002  using the fax modem connected to device /dev/cua1.

    efax -d /dev/cua1 \
         -t T222-2222 letter.001 letter.002
```

Anyone ?

```
andy@7:~/Documents$ sudo efax -d /dev/ttyACM0 -t "1 855 330 1239" TEST_FAX.tif

efax: Thu Aug 11 23:43:10 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: Thu Aug 11 23:43:10 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 43:10 compiled Jun 21 2006 04:57:11
efax: 43:10 Error: can't read multi-strip TIFF files
efax: 43:10 Warning: missing TIFF compression format, set to raw
efax: 43:10 Error: missing offset to TIFF data
efax: 43:10 done, returning 2 (unrecoverable error)


```

Have also tried faxxing every other known image format ??

---

### Post by coldraven on 2016-08-12
To avoid having to use sudo make yourself a member of the dialout group.
> dialout :
       Full and direct access to serial ports. Members of this group         can reconfigure the modem, dial anywhere, etc.       


From here:
file:///usr/share/doc/base-passwd/users-and-groups.html

---

### Post by kurt18947 on 2016-08-12
eFax doesn't require a modem or phone line, it's web based.

[http://www.efax.com/how-it-works](http://www.efax.com/how-it-works)

It and similar services look like a nice option for sending or receiving faxes but it seems a bit spendy for occasional use. There are free limited services such as this one:

[http://www.gotfreefax.com/](http://www.gotfreefax.com/)

or

[https://faxzero.com/](https://faxzero.com/)

I don't know about other manufacturers but Brother offers linux fax drivers for its mult-function machines. I've never installed it but presume it'd work - it would require a phone line.

[http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)

---

### Post by 4kh3RAm on 2016-08-12
> **coldraven said:**
> To avoid having to use sudo make yourself a member of the dialout group.

From here:
file:///usr/share/doc/base-passwd/users-and-groups.html

Thanks.

I read the file but did not see how to make myself a member of the dialout group.

-----------------------------------

When I tried running the front end for efax-gtk, I got this.

```
Socket running on port 9900
GPL Ghostscript 9.18: Some glyphs of the font BAAAAA+LiberationSerif requires a patented True Type interpreter.
[COLOR=#0000cd]_efax-0.9a: 09:54:36 Error: can't open serial port /dev/ttyACM0: Permission denied_[/COLOR]
efax-0.9a: 09:54:36 failed page /home/andy/Documents/TEST_FAX.pdf.001
efax-0.9a: 09:54:36 finished - unrecoverable error
```

And when running it from a console....

```
andy@7:~/Documents$ sudo efax -d /dev/ttyACM0 -t "1 855 330 1239" TEST_FAX.pdf
[sudo] password for andy: 
efax: Fri Aug 12 10:03:14 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: Fri Aug 12 10:03:14 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 03:14 compiled Jun 21 2006 04:57:11
[COLOR=#008000]_efax: 03:14 Error: can't get format of TEST_FAX.pdf_[/COLOR]
efax: 03:14 done, returning 2 (unrecoverable error)
```

---

### Post by 4kh3RAm on 2016-08-12
> **kurt18947 said:**
> eFax doesn't require a modem or phone line, it's web based.

[http://www.efax.com/how-it-works](http://www.efax.com/how-it-works)

It and similar services look like a nice option for sending or receiving the occasional fax without needing an extra phone line.

There is efax which is your link and efax-gtk which is what I am using.

[http://linux.die.net/man/1/efax](http://linux.die.net/man/1/efax)

---

### Post by kurt18947 on 2016-08-12
> **4kh3RAm said:**
> Thanks.

I read the file but did not see how to make myself a member of the dialout group.

-----------------------------------

When I tried running the front end for efax-gtk, I got this.

```
Socket running on port 9900
GPL Ghostscript 9.18: Some glyphs of the font BAAAAA+LiberationSerif requires a patented True Type interpreter.
[COLOR=#0000cd]_efax-0.9a: 09:54:36 Error: can't open serial port /dev/ttyACM0: Permission denied_[/COLOR]
efax-0.9a: 09:54:36 failed page /home/andy/Documents/TEST_FAX.pdf.001
efax-0.9a: 09:54:36 finished - unrecoverable error
```

And when running it from a console....

```
andy@7:~/Documents$ sudo efax -d /dev/ttyACM0 -t "1 855 330 1239" TEST_FAX.pdf
[sudo] password for andy: 
efax: Fri Aug 12 10:03:14 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: Fri Aug 12 10:03:14 2016 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 03:14 compiled Jun 21 2006 04:57:11
[COLOR=#008000]_efax: 03:14 Error: can't get format of TEST_FAX.pdf_[/COLOR]
efax: 03:14 done, returning 2 (unrecoverable error)
```

I install this package:  "gnome-system-tools". One of its functions is to add a "users and groups" app. It's a more useful (IMO) form of the "users" app found in Ubuntu.

---

### Post by SeijiSensei on 2016-08-12
If you can't get efax to work, take a look at [hylafax]("http://hylafax.sourceforge.net/howto/index.php").  It's probably overkill for your application, but it's been around for a long time because it works.  It's in the Ubuntu repositories.

---

### Post by 4kh3RAm on 2016-08-12
> **coldraven said:**
> To avoid having to use sudo make yourself a member of the dialout group.

From here:
file:///usr/share/doc/base-passwd/users-and-groups.html

I got it figured out.
 
```
sudo gpasswd --add andy dialout

```

Efax is working great. :-)

---

### Post by 4kh3RAm on 2016-08-12
> **SeijiSensei said:**
> If you can't get efax to work, take a look at [hylafax]("http://hylafax.sourceforge.net/howto/index.php").  It's probably overkill for your application, but it's been around for a long time because it works.  It's in the Ubuntu repositories.

Thanks.

---

### Post by coldraven on 2016-08-12
> **4kh3RAm said:**
> I got it figured out.
 
```
sudo gpasswd --add andy dialout

```

Efax is working great. :-)

Told'ya :)

---

