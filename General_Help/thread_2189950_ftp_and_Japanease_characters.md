---
title: "ftp and Japanease characters"
date: 2013-11-24
forum: General Help
---

### Post by KeepItSimpleStupid on 2013-11-24
If you anonymous ftp to ftp.picosystems.net and change to the driectory pub, filenames are not displayes correctly using ftp's commenad ls.  They are when using mget.

ftp> o ftp.picosystems.net
Connected to [www.picosystems.net](www.picosystems.net).
220 (vsFTPd 2.2.2)
Name (ftp.picosystems.net:ubuntu): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files
ftp> ls
227 Entering Passive Mode (219,94,234,19,142,225).
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Jul 21 06:03 pub
drwxr-xr-x    2 0        0            4096 Nov 21 09:20 tmp
226 Directory send OK.
ftp> cd pub

ftp> mget *1999.pdf
mget **&#22826;&#38525;&#35480;&#38651;**_TAIYOYUDEN_PRODUCTS_1999.pdf? n
ftp> ls *1999.pdf
227 Entering Passive Mode (219,94,234,19,226,40).
150 Here comes the directory listing.
-rw-r--r--    1 0        0        65597618 Mar 23  2012 **????????????**_TAIYOYUDEN_PRODUCTS_1999.pdf
226 Directory send OK.
ftp> 


Th file will transfer correctly with the Japanease filenames using mget and answering yes.  You can use ls and  mget *.pdf too.

The issue affects Firefox too.  Here is the bug filed there:  [https://bugzilla.mozilla.org/show_bug.cgi?id=942495](https://bugzilla.mozilla.org/show_bug.cgi?id=942495)

Problem areas shown in bold.

---

