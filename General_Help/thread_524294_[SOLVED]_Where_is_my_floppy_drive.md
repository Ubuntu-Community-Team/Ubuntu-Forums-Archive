---
title: "[SOLVED] Where is my floppy drive?"
date: 2007-08-12
forum: General Help
---

### Post by mister_lister on 2007-08-12
I have just installed dapper drake (6.06) ubuntu. Right after installation I completely updated and restarted my computer. Everything seems to be working EXCEPT I am not able to access my floppy drive. During install it did detect my floppy drive and it worked up until this point under windows. It is a regular IDE floppy drive. I do not see it listed in PLACES  or PLACES>COMPUTER. My CD ROM and File system are there but no floppy. How do I get ubuntu to see the floppy drive so  I can start copying over files I need. 

In all other versions of Linux, The Floppy was on the desktop and all I had to do was put a disk in and mount it. 

Any help will be appreciated, I found no resolution on the forums thus far.

---

### Post by Warren Watts on 2007-08-12
It should be available thru the GUI by clicking on Places and choosing "Computer"

---

### Post by mister_lister on 2007-08-12
As I wrote in my last message, the floppy drive is not available through PLACES>COMPUTER 
my CD ROM and filesytem are there but NO floppy.

---

### Post by Warren Watts on 2007-08-12
Oops....Sorry I missed that.... DUH...

---

### Post by Butthead on 2007-08-13
Hmm, go see if you have the "fdutils" package installed in Adept.:confused:

---

### Post by mister_lister on 2007-10-10
I found the solve in a chat room. It is fairly simple.

To load the floppy real time before rebooting type the following in the terminal:

"sudo modprobe -k floppy"

To make it appear at start up, Type the following in the terminal:

"sudo nano /etc/modules"

And add the text "floppy" in a blank line, save (write) and exit. Restart.


The floppy drive should appear in nautilis (places>computer) and from there on you must mount the drive by putting a disk in and right clicking on the icon for the drive and select "mount". When done, right click and "unmount" the drive when done dismounting, remove the disk..

---

