---
title: "Connect to server...  FTP ( with login )"
date: 2008-06-12
forum: General Help
---

### Post by timiswright on 2008-06-12
Hi all,

I've been getting very annoyed searching for answers to this one, and getting know where fast.

On my PC when I try to create my server using "Connect to Server" then using FTP ( with login ) I get the error INVALID REPLY  . 

Filezilla & gFTP work fine but I want to get it mapped so I can use bluefish to edit my sites live.

This has been driving me crazy trying to resolve. But today I've just had a break through ( I Think.... )

I loaded the live hardy heron live cd on an old Asus box and without installing anything it just started and connected to my server as I would have thought it always should have!!!

So that got me thinking that it was something I had installed on MY system so I did a clean install on another HDD but...
Same issue Invalid reply.

SO...

I loaded the live cd on my system and still no joy, So it's got to be hardware related. I've just tried a different network card but it still doesn't work.

Anybody out there with the same issues " What motherboard are you using? "

I'm on a Gigabyte GA-M61SME-S2 AMD ATHLON 4800+ AM2

I need to get to the bottom of this one fast or it's back to the old XP.

HELP!! (don't make me go back to the dark side)

Cheers,

Tim

---

### Post by iamfletch on 2008-06-21
erm i am getting the same error as you. have your resolved it? if so, how?

---

### Post by ddales on 2008-06-22
Check out "curlftpfs"

---

### Post by bgiddins on 2008-10-30
I get this on Intrepid when using Places as well - but ftp from the terminal works just fine. Using Asus P5Q-VM.

Very annoying - when I had Hardy on this hardware, it worked.

---

### Post by mia.king on 2008-12-01
Same problem here - FTP works on Filezilla or others but not on the Places (is there another name? FTPfs?). I also cannot be certain what the error is. Is there a debug log or something?

Somewhere out there says it is a problem with passive/active FTP modes.

I miss PSPad with built in ASCII FTP support. 
(also Bluefish doesn't seem to allow [TAB] for indentation.)

Is someone suggesting that curlftpfs will solve this problem?

Thanks.

---

### Post by aldrydd on 2008-12-01
Yeah... I'm having the same problem. FTP clients seem to work fine, but I can't mount my servers in Places.

I've been searching around for a couple weeks for a solution/tutorial... No dice.

---

### Post by CalderCoalson on 2009-02-22
Same problem here with ftp.izfree.com.  Nautilus gives me the following error:
```
Sorry, could not display all the contents of "/ on ftp.izfree.com": Invalid reply
```
the 'ftp' command in the terminal works fine, but nautilus does not.  This is extremely annoying because I have to save and then upload files, rather than simply editing them on the server.  Please help!

Thanks in advance,
-Calder Coalson

---

### Post by leandromartinez98 on 2009-04-16
Same problem here. This may be related to Nautilus not using the 
same ftp protocol than the command-line ftp. I don't know. But I couldn't 
find any solution. (Intrepid).

---

### Post by Charlietje on 2009-08-15
I've got the same.
Filezilla works fine, ftp via terminal works fine
When connecting to server in nautilius, it doesn't work

anyone?

---

