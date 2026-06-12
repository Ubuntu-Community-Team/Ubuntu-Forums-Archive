---
title: "Grub and vnstat puzzles"
date: 2016-07-09
forum: General Help
---

### Post by col48 on 2016-07-09
No longer a show-stopper, but two possibly connected puzzles.
[B][SIZE=3]
Background[/SIZE][/B]

I have a triple-boot system, all Ubuntu.
12.04 on sdb1
10.04 on sda3 (almost never used)
8.04 on sda1 (never used)

Yesterday I did some work using 12.04 (Precise), including dealing with a few emails and some stuff with LibreOffice spreadsheets and then shut down normally.

[B][SIZE=3]First puzzle
[/SIZE][/B]
Today when I logged on, grub did not offer me 12.04 at all, just the extant 10.04 and 8.04 kernels as options.
Nothing was amiss on sdb1 as seen from 10.04 (Lucid), but I did notice by looking in the file properties that /var/lib/vmlinuz claimed it had been accessed around the time I had signed out.

Problem with boot was eventually cured by editing the boot sequence in grub (it had not been looking at sdb1; somehow another drive - one not capable of booting from - had been substituted).
*How could this have happened without my being aware of doing something out of the ordinary?*  Normally I leave anything to do with the OS well alone.

[B][SIZE=3]Second puzzle
[/SIZE][/B]
I use vnstat routinely to keep an eye on network traffic and soon before I shut down yesterday noticed that it was not reporting any data for yesterday.
vnstat uses a file owned by root in /var/lib/vnstat as a store for the data (gathered, I understand by/through the kernel).
When using Lucid, vnstat was working normally - in other words nothing was preventing the data being collected (different physical file, of course).
Once I got into Precise earlier today, vnstat was still not reporting traffic, so I pretended it was new and tried vnstat -u -i eth0 which told me it could not read the file (fair enough, owned by root) nor write to it but, despite this, subsequently data is being collected and reported.  [I]Why not before?  Is this connected with the first puzzle?

[/I][SIZE=3]**So...**[/SIZE]If anyone can shed light on these puzzles, my curiosity would be satisfied and the knowledge may be of use to someone facing the same situation.
As I say, I'm up and running as normal again, so it's just a matter of interest for me, nothing more.

---

### Post by col48 on 2016-10-19
First puzzle:

Precise was on a different disk from the other two Ubuntus.
Subsequent experience suggests that clearing the dust from inside the desktop cabinet was what was needed.
Quite why that made a difference is a matter of speculation.  What matters is that it did.

Second puzzle:
This has not recurred, or at least, I haven't noticed it.


[Marked as solved because I am no longer looking for a solution]

---

