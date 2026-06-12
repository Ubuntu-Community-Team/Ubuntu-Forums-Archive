---
title: "Ubuntu 6.10 - keyboard problem!"
date: 2007-09-06
forum: General Help
---

### Post by jessejazza on 2007-09-06
Thought i'd installed ubu without a problem... sadly a fault has raised its ugly head. It was installed on a Compaq P3 that i had spare. Intention was to try out ubu fully before serious use and copying files 
over from my windoze machine.

I used a new keyboard and thought it was faulty. Repeats letters when typing - but inconsistent with letters. I dismissed it as just the keyboard. Tried the one from my other machine and that seemed to be 
fine. [Both keyboards are standard basic PS2 - i'm a bit old fashioned i like them simple!]. However, after a bit more use again keyboard problems showed themselves. Tried both on the windoze machine for the 
evening - FINE no problems. On the Compaq it seems to be inconsistent, different problems with different keys - go back to a 'faulty' key and it's then fine.

So i assume it could be some incompatibility with the Compaq on the software side - any ideas. Due to not being able to use the keyboard easily would i be better to just try 7.04 and hope that sorts it?

thx

---

### Post by mocoloco on 2007-09-07
I would suggest just going to 7.04, there's normally no reason to stick with older versions unless you're running a server, or unless you know something's not yet compatible with your setup.  In the Linux world and especially Ubuntu there are MAJOR fixes with each release, so it's very probable if it was a software bug it's been fixed.

---

### Post by jessejazza on 2007-09-07
Thanks - that was the route i was going to go down. I thought it was the LTS version but that is 6.04 (as LTS i thought it would get some updating). I had the disk on a book so thought i'd use it just to start experimenting with ubuntu. As you can imagine until i've got the keyboard working properly i can't find out that much about Ubu.

Failing that it must be some problem with the mobo. The only way i can solve that is to wipe Ubu and install win2k. I tried this but found that i couldn't use by windoze boot disk - what can i do to erase ubu from the hard disk?

---

### Post by mocoloco on 2007-09-07
You should be able to boot from the 6.10 LiveCD and go to System -> Administration and start the Gnome Partition Editor.  At least I'm pretty sure it's included on the 6.10 CD (I know it's no longer included on the 7.04 CD).  If it's not you can install it in Add/Remove, or sudo apt-get install gparted.  You should be able to do whatever you want with your drive using that.

If your win2k boot disk won't start I don't think you'll be able to install with it even if you wipe the hd.

---

### Post by cap0008 on 2007-09-07
I'm having similar problems with 7.04
PS2 keyboard once in a while it acts like a particular key sticks for about a second, nothing is displayed, and then all "stuck key presses" are processed in rapid succession.
This is a new install in a separate disk.  Have not had this problem at all with XP.

---

### Post by jessejazza on 2007-09-07
Thanks cap0008 - at least i'm not alone:KS

I think i've solved the problem. If you remember i tested both boards on windoze and worked fine. On ubu one was a little better than the other but slightly i thought. BOTH these keyboards are same model same manufacturer.

I just happened to call in at a well known supermarket and their computer stuff caught my eye. They'd got some black standard keyboards which i prefer and bought one. Just been typing for an hour on ubu and no problems.

SO ANYONE KNOWLEDGEABLE ON KEYBOARDS - AND HOW THEY CAN DIFFER BETWEEN MANUFACTURER.:lolflag:

Crazy but true - i promise.

---

### Post by mocoloco on 2007-09-07
In that case two suggestions.

I had an issue with a machine that after a fresh install the mouse did not work at all.  It turns out there was an issue with the ps2 driver and that particular processor chipset, and it was fixed in a subsiquent update.  So maybe try running all updates.  I found out it was being working on and when it was fixed because a bug had been filed on launchpad.

Which leads me to my second suggestion.  Search launchpad and see if a bug has been reported for this.  If not, submit one with as much useful information as you can.
[Here's]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=keyboard+repeat&orderby=-importance&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") a launchpad search that may help you find if this bug has been reported.

---

### Post by jessejazza on 2007-09-08
Thanks mocoloo.

Now i have a keyboard i can start looking into things. I just put 6.10 on because i happened to have the disk from a book. This is a spare PC for me to get linux familiar on. I was going to put 7.04 on but so many folk seem to have so many problems. No doubt different chipsets etc rather than ubu itself. 

I'll be trying shortly it shortly so we'll see. Thanks for launchpad i'll have a look.

---

### Post by jessejazza on 2007-12-17
Thanks for your help but after installing 7.04 - the problem was not solved. All i've learnt is stay with a cheapy keyboard. The more expensive ones i had were a nice wired k'board with a USB slot in the side which was quite useful - i miss it.

thanks

---

