---
title: "if I wipe my Ubuntu partition.."
date: 2006-07-05
forum: General Help
---

### Post by Cloudy on 2006-07-05
Will it take GRUB too on its own, or is there anything special I ought to do to remove GRUB? I'm going to try a clean install and would like to know beforehand. #-o

---

### Post by Kilz on 2006-07-05
[QUOTE=Cloudy]Will it take GRUB too on its own, or is there anything special I ought to do to remove GRUB? I'm going to try a clean install and would like to know beforehand. #-o[/QUOTE]
It will not take part of it that starts grub out of the master boot record. But the grub files themselves will be gone. If you are installing Ubuntu again it shouldn't make a difference.

---

### Post by Cloudy on 2006-07-05
[QUOTE=Kilz]It will not take part of it that starts grub out of the master boot record. But the grub files themselves will be gone. If you are installing Ubuntu again it shouldn't make a difference.[/QUOTE]

alright, I just wanted to make sure because I'm still not over that whole "petrified of screwing something up" phase >.>

---

### Post by tonyr on 2006-07-05
No, wiping the partition will not remove the **grub** bootloader, which lives in the 
Master Boot Record (MBR).  The bootloader, however, will still be expecting to find
boot information (menu.lst) on that Ubuntu partition that you wiped, so, of course, the
information will not be found and **grub** will fail to boot anything.

This is a great argument (and one of the main ones) for giving **/boot** its own
partition, so that **/boot/grub** will not be erased when someone wants to do exactly
what you are asking about.

Depending on what your goal is (reinstalling Ubuntu? dual booting? installing some 
other Linux distro? some other OS? no OS at all?) the solutions are varied.

If you just have one HD, and you are wiping the whole thing to re-install Ubuntu,  there
is no problem.  If you have many partitions and you still want **grub** as your 
bootloader, there is still no problem.  In  both of these cases, just let the install
process install grub as it normally would.

If your situation is something else, spell it out.

---

### Post by Cloudy on 2006-07-05
[QUOTE=tonyr]No, wiping the partition will not remove the **grub** bootloader, which lives in the 
Master Boot Record (MBR).  The bootloader, however, will still be expecting to find
boot information (menu.lst) on that Ubuntu partition that you wiped, so, of course, the
information will not be found and **grub** will fail to boot anything.

This is a great argument (and one of the main ones) for giving **/boot** its own
partition, so that **/boot/grub** will not be erased when someone wants to do exactly
what you are asking about.

Depending on what your goal is (reinstalling Ubuntu? dual booting? installing some 
other Linux distro? some other OS? no OS at all?) the solutions are varied.

If you just have one HD, and you are wiping the whole thing to re-install Ubuntu,  there
is no problem.  If you have many partitions and you still want **grub** as your 
bootloader, there is still no problem.  In  both of these cases, just let the install
process install grub as it normally would.

If your situation is something else, spell it out.[/QUOTE]

Well, I think I may have screwed up during the install and I've done all I can find to fix it so I'm at my last option; reinstalling. This PC has a 200GB HD with a 170GB XP partition and a 15 GB Ubuntu partition. 

so if I uninstall Ubuntu GRUB would still list XP right?
I wouldn't be up the creek without a paddle right? 
or.. would I? ](*,)

---

### Post by Cloudy on 2006-07-05
hmm...

---

### Post by tonyr on 2006-07-05
Yes, you would be up the proverbial creek, but not without a paddle.  There are ways
to recover the Windows boot loader if you can still boot from a floppy or CD.  
What you should do first, however,  is reinstall the Windows boot loader.  
I think in Windows this is something like **fdisk /mbr** in a command shell.  
You might research that a little.

---

### Post by tonyr on 2006-07-05
There is some information about recovering the Windows XP MBR [here]("http://www.ntfs.com/mbr-damaged.htm").

EDIT: ...and [here]("http://support.microsoft.com/kb/314058/")...

---

### Post by Cloudy on 2006-07-05
Thanks! I know it's more work than its worth but I'm curious, if I installed Damn Small Linux before uninstalling Ubuntu would I still be able to get into XP just fine, sort of like DSL taking Ubuntu's place for a few minutes while I uninstall & reinstall? 

like I said, I know its more work than its worth and such but I'm curious. Thanks for the links.

EDIT: For some reason unknown to me this PC doesn't have a floppy drive; just didn't come with one. And I don't have a Windows CD, it was preinstalled.
:S

---

### Post by tonyr on 2006-07-06
I've never done the Damn Small Linux thing, but I suspect that what you suggest can be
done.  I just don't know the details.

---

### Post by Cloudy on 2006-07-06
ah, ok. thanks then. I'm going to google around and see if I can find a way to fix the Windows MBR without a cd or floppy drive..

---

### Post by tonyr on 2006-07-06
[Here's]("http://www.neowin.net/forum/index.php?showtopic=292614&pid=587624373&st=45&#entry587624373") one.  Look for the post with the attachment **mbr.bin.txt**.  What it says, essentially, is
"take this file and write it to the MBR of your target disk".

---

### Post by Cloudy on 2006-07-06
ok - thank you again for that. :)
I'll have to do it before I uninstall
right, duh?
I keep asking common sense questions. >.<

---

### Post by tonyr on 2006-07-06
Disco Stu says "Oh Yeah..."

---

### Post by Cloudy on 2006-07-06
Sure that's not Duffman? ;)

---

### Post by tonyr on 2006-07-06
Probably.  As far as my brain is concerned, Simpsons, Futurama, The Critic, South Park,
Family Guy, it's all one (and I think Dr Who is in there somewhere, too)

EDIT: homestar runner etc etc etc

---

