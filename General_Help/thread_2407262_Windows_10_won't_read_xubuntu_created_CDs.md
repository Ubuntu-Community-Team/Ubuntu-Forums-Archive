---
title: "Windows 10 won't read xubuntu created CDs"
date: 2018-12-01
forum: General Help
---

### Post by Ralph L on 2018-12-01
I run Xubuntu 18.04 LTS with the latest updates.  I am trying to create a CD for friend (who runs Windows) containing some pdf files and with a wget created html set of files. Windows 10 would not read the CD I created with Xubuntu, so I created a new CD with just a single pdf file.  Windows 10 would not read that either.  To ascertain whether Windows would read any CD at all, I tried some Windows CDs that I had sitting around.  Windows read them just fine.  So there is something peculiar about Xubuntu created CDs that is incompatible with Windows 10.
I created the CDs with xfburn selecting the "New Data Composition" option. Then I clicked "Add" and selected the files I wanted on the CD.  Then I clicked "Proceed to Burn".  Everything seemed to work ok.  When I brought up Windows 10, it recognized the CD, showed the CD name fine, and showed the files on the CD.  However, when I clicked to open a file, Windows went into an infinite loop trying to process the file.  I finally had to kill Windows to get out of the loop.
I also tried writing a CD with k3b.  I clicked "New Data Project", selected Project>Add Files, selected the files I wanted on the CD, and then clicked "Burn".  K3b responded with "Fatal error during recording: Input/output error".  

Anybody know how to, in Xubuntu, burn a CD with a few pdf and html files on them that can be read by Windows 10.
Thanks in advance.......

---

### Post by ajgreeny on 2018-12-01
Did you check that the CD was closed (finalised) after burning; if not it will not be readable in any other hardware than that which burned it.
Can you read the CD on your own Xubuntu machine?
Do you know if it can be read by any other machine running Ubuntu or other Linux distro?

Normally CDs are finalised automatically so this should not be a problem, but it is worth asking.

---

### Post by Autodave on 2018-12-01
My first thought would be that the recording speed may have been too fast.  Are the files you are trying to record on an external drive: your transfer speed from the source could be the cause.

---

### Post by Ralph L on 2018-12-01
AJGreeny and Auto Dave:  Thank you for responding.  Here are the answers to the questions you asked.
1.  I waited until xfburn ejected the cd.  I presume that means it was finalized.
2.  I have 2 xubuntu machines.  Both of them read it fine.
3.  After I wrote the original post,I brought out an old machine with Windows Vista on it.  It read the cd fine.  It seems that only Windows 10 won't read it, although Windows 10 reads other Windows created cds--like my wife's Bicycle Bridge release disk.
4. The cds are being written and read on internal cd drives on both the xubuntu computers (laptops) and the Vista computer (laptop).

I take it, from what you are telling me, that the format of a cd is the same for both Xubuntu and Windows.  I thought there might be two different formats.  In order to keep from using up all my cd-r disks I switched to using a cd-rw for my tests.  I noticed that when I put a xubuntu formatted (and containing a file) cd-rw in the Windows 10 drive, it wanted to format it rather than read it.  When I put that Windows 10 formatted cd-rw into my xubuntu machine and tried to write it, xfburn insisted on reformatting it.  Seemed strange to me.  Like neither system liked the other's formatting.

One other question.  Am I correct in using the "New Data Composition" option in xfburn to created the cd?  Is there another option I should be using instead??

---

### Post by gsahli on 2018-12-01
About recording standards:
[https://docs.microsoft.com/en-us/windows/desktop/imapi/disc-formats](https://docs.microsoft.com/en-us/windows/desktop/imapi/disc-formats)

---

### Post by scdbackup on 2018-12-02
Hi,

yes, "New Data Composition" would be the Xfburn task to use. It creates
an ISO 9660 filesystem which is supposed to be readable on about all
operating systems. (If some of its files have size 4 GiB or more, then the
list of operating systems shrinks a bit.)

Up to the description about formatting CD-RW everyting looks like the
drive of the Windows 10 computer does not like the media which were written
by the drive of the Xubuntu computer. This would not be a matter of operating
systems, but rather of decaying drive hardware.

Now for the issue of formatting CD-RW. This can be done, but is rather
unusual for burn programs. Program cdrwtool out of udftools does it
for making the CD-RW random-access writable. Media capacity shrinks by
about 100 MB and with a read-write filesystem like ext2 the drive will
make miserable noises.

Some people give the procdure of blanking the name "formatting". But a
burn program should know the difference. So what text exactly does Xfburn
display when it insists on reformatting the CD-RW ?

It is normal that a burn program first wants to blank a used CD-RW vefore
it is willing to write a new session on it. If the medium was closed during
the former burn run, there is no way to write to it before blanking happened.

Have a nice day :)

Thomas

---

### Post by Ralph L on 2018-12-09
Thanks again to everybody that responded to this.  I really appreciate it.  I have been too busy for the last week and a half to respond to this, but I now have time.
1.  As I said in an earlier post, I was able to read the xubuntu xfburn created cd with Windows Vista, so I gave it to my friend and he read it fine with Windows 7.  So the problem seems to be only with Windows 10.
2.  The Windows 10, on which I can't read the xfburn cd, is a dual boot (the original O.S. that came with my laptop plus the xubuntu 18.04 that I added).  Using the same laptop (now having xubuntu 18.05 in addition to Windows 10) I xfburn-ed the cd that Windows 10, on the same laptop, can't read.  So it is not a drive hardware problem.  The same cd drive was used to both write and read the cd.
3.  [https://docs.microsoft.com/en-us/win...i/disc-formats](https://docs.microsoft.com/en-us/win...i/disc-formats) lists 3 cd formats:  ISO 9660, Joliet, and UDF (Universal Disk Format). From the comments above I take it that xubuntu writes only the most basic ISO 9660.  From that website it seems that UDF is replacing ISO 9660 as the most common format.  

Does anybody know if there is a parameter to cause xubuntu to write UDF, or a Windows 10 parameter to make it read basic ISO 9660 format??

---

### Post by scdbackup on 2018-12-09
Hi,

Xfburn does no UDF, because libisofs does no UDF. K3b may use mkisofs or
genisoimage which can produce UDF for DVD video.

But i really would be astonished if MS-Windows 10 could not read ISO 9660.

Have a nice day :)

Thomas

---

