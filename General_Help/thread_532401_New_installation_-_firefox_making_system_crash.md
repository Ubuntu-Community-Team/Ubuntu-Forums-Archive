---
title: "New installation - firefox making system crash"
date: 2007-08-22
forum: General Help
---

### Post by moonorchid on 2007-08-22
I just installed Fiesty on a brand new machine I built yesterday (not an easy process because of errors regarding my graphics card), and my entire system has crashed 5 times - each time, it's while I'm using firefox. The screen is filled with multi-colored small horizontal bars, and the only thing I can do is restart the system. 

After searching the forums, I thought I'd see if the problem is caused by flash. I went to my personal site which has no flash elements, and could only navigate through 2 or 3 pages before the crash happened again. (which is what's occurred each time, 2 or 3 pages in) Although other people have had problems with firefox crashing their system, I can't find a problem similar to mine.

Here's what I'm dealing with: 

 - Biostar Geforce 6100-M9 nVidia Socket 939 motherboard
 - AMD Athlon 64 4000 CPU
 - 250 G hard drive and 512 memory (plus 2 G of virtual memory)

This is the first time I've ever installed or used Linux, and my geekiness factor is limited. Please let me know if you need additional information, and forgive me if this is answered somewhere else. 

Thanks!

---

### Post by moonorchid on 2007-08-22
Okay, update: I installed Epiphany through the synaptic package manager, and have so far not had the same crashing issue. yay! 

One of my geeks is going to do a memory check to see if that's the issue. I'll post another update if we discover more about the problem.

---

### Post by macjones on 2007-08-23
Does your screen look like this ?

[http://ubuntuforums.org/showthread.php?t=392973](http://ubuntuforums.org/showthread.php?t=392973)

could it be happening mainly on Javascript pages....?

a suggestion from here

[http://www.mail-archive.com/devel@xfree86.org/msg07999.html](http://www.mail-archive.com/devel@xfree86.org/msg07999.html)

is to try...

Option "DRI" "no"

in your /etc/X11/xorg.conf

I fixed it on some old compaq's by going back to vesa from i810.

---

### Post by moonorchid on 2007-08-23
[I][INDENT][QUOTE=macjones;3237725]Does your screen look like this ?

[http://ubuntuforums.org/showthread.php?t=392973](http://ubuntuforums.org/showthread.php?t=392973)[/INDENT][/I]

Not exactly like that, but it's similar. Total crash, as they described.

[INDENT]*could it be happening mainly on Javascript pages....?*[/INDENT]

That is a great question. It seemed to happen on any web page I went to - firefox, flickr, and my drupal site.

[I][INDENT]a suggestion from here

[http://www.mail-archive.com/devel@xfree86.org/msg07999.html](http://www.mail-archive.com/devel@xfree86.org/msg07999.html)

is to try...

Option "DRI" "no"

in your /etc/X11/xorg.conf[/INDENT][/I]

See, this is where my geekiness is limited. I'm not a programmer, and have never used Linux before. So I have no idea what you are talking about. :) I can have one of my geeks walk me through this, however, so thank you!

I will post again on here when I have more info about the problem and/or solution. 

Thanks!

---

