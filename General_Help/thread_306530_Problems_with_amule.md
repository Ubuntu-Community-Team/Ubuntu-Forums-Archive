---
title: "Problems with amule"
date: 2006-11-25
forum: General Help
---

### Post by javierfh on 2006-11-25
Hi,

is it only me or amule is totally unstable?
I open it and well it opens and starts to download, but randomly crashes...in fact i guess havent managed to have it working ever for more than 15 minutes. Sometimes it is just two minutes.

Anyone has been through same kind of problems? anyone has a solution?
Im some thread i read that someone launch it in command line,with amuled but i cant manage to do that.

I would really appreciate all help in that subject.

Thanks in advance,

Javi

---

### Post by chek2fire on 2006-11-25
same problem here

---

### Post by javierfh on 2006-11-25
Does anyone know at least some alternative to amule? I mean something similar to emule, but for linux.

Javi

---

### Post by barkholt on 2006-11-25
> **javierfh said:**
> Hi,

is it only me or amule is totally unstable?
I open it and well it opens and starts to download, but randomly crashes...in fact i guess havent managed to have it working ever for more than 15 minutes. Sometimes it is just two minutes.

Anyone has been through same kind of problems? anyone has a solution?
Im some thread i read that someone launch it in command line,with amuled but i cant manage to do that.

I would really appreciate all help in that subject.

Thanks in advance,

Javi

Runs without problems on my Kubuntu Edgy (aMule 2.1.3). What kind of error messages does it dump to the console?

I don't know how updated they are, but you could try to check out imule and xmule as alternatives.

---

### Post by javierfh on 2006-11-25
> **barkholt said:**
> Runs without problems on my Kubuntu Edgy (aMule 2.1.3). What kind of error messages does it dump to the console?

I don't know how updated they are, but you could try to check out imule and xmule as alternatives.

Hello,

im using 2.1.3 in Ubuntu Edgy and well ..to be honest i dont know how to get these logs you ask for.
I just launch the ui from the applications menu and then just runs and without any reason just crashes and vanishes.

Any idea how can i get the information from the crash reasons?


Javi

---

### Post by javierfh on 2006-11-25
Got something, 

i launched it from command line and this is the output i got.. can anyone see anything wrong? any idea what is refering at?

> 
javi@javi-desktop:~$ amule &
[1] 7274
javi@javi-desktop:~$ Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
Loading temp files from /home/javi/.aMule/Temp.
Loading PartFile 2 of 2
All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Adding file /home/javi/.aMule/Temp/002.part.met to shares
Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 986767 error_code 16 request_code 56 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
javi@javi-desktop:~$ 



---

### Post by barkholt on 2006-11-25
> **javierfh said:**
> Got something, 

i launched it from command line and this is the output i got.. can anyone see anything wrong? any idea what is refering at?

It seems like something goes wrong in the communication with the X server, I have no idea what it is :)

Are you running anything fancy like Compiz/Beryl? Are you running on 32bit/64bit system? X86/PPC? Can you try running it under KDE?

You could also try uninstalling amule and build it from source, to see if that makes a difference?

---

### Post by javierfh on 2006-11-25
Hi,

nothing fancy here :) i have dual core machine but i decided not to try the 64 bits. I was using compiz in dapper, but since i had problems back then, i  decided not to install beril/compiz either for a while, so not to that either :)
And about kde.. i guess that i cant, since im using ubuntu, in other words gnome.

But i might try probably sometime to remove it and try to build it from source.

Thanks for your support and interest..


Javi

---

### Post by Rodneyck on 2006-11-26
It happens to me as well under Ubuntu. I can usually crash it if I start going back and forth between the search tabs, all using the "global" search option. It also does it randomly as well, very strange.  It is to bad, I like amule and the download speeds are fast.

I just read about Frostwire as an alternative P2P, might try that one.

---

### Post by javierfh on 2006-11-26
> **Rodneyck said:**
> It happens to me as well under Ubuntu. I can usually crash it if I start going back and forth between the search tabs, all using the "global" search option. It also does it randomly as well, very strange.  It is to bad, I like amule and the download speeds are fast.

I just read about Frostwire as an alternative P2P, might try that one.

Hi,

well for me i can make it crash even without touching anything..its amazingly bad.
To be honest i launch it from terminal and well lately i managed to keep it on for half our or something..but..still crashes randomnly.

I wish someone will have some solution for that or tip.

Javi

---

### Post by misfitpierce on 2006-11-26
I had the same problem... found out it crashes when I close a search. Shouldnt crash as long as you leave your first search tab opened and dont close it or push clear all or w/e. Thats how ive figured out how to use it.

---

### Post by javierfh on 2006-11-26
> **misfitpierce said:**
> I had the same problem... found out it crashes when I close a search. Shouldnt crash as long as you leave your first search tab opened and dont close it or push clear all or w/e. Thats how ive figured out how to use it.

But i guess i didnt even close the search tab. And anyway, when it crashes i just  start it again and i dont have to search anymore, so shouldnt crash anymore but still does it. 
Of course, i open the transfer tab and maybe thats what it causes similar crash..
I hope someone could find way to fix it or they will publish a new release fixing that but im not very optimistic about that later one :(

Javi

---

### Post by jrjazzman on 2006-12-04
The problem is apparently caused by gtk-2.10.x.  Any way we could get the repo maintainers to build amule against gtk-2.7.2?

---

### Post by Chareos on 2006-12-08
Little workaround (well, not properly but stills do the job reasonably)

If you launch amule as deamon, then use the external gui, it still crash as reported, but won't kill the deamon, so the transfers will still go on.


Anyway I hope it will be fixed soon ! :-D

---

### Post by jrjazzman on 2006-12-08
If it's a major problem for you, you can compile from source against the older gtk libraries that were previously mentioned.

---

