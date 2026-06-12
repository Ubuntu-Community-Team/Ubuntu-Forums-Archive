---
title: "can't print in gimp ( sorry for repeat)"
date: 2005-05-07
forum: General Help
---

### Post by neighborlee on 2005-05-07
I am unable to print in gimp , yet printing is working everywhere else...printing works in mdk 10.1 official leading me to believe some package I guess is missing to allow this to work right..I just dont have a clue what as I checked synaptic and all seems to be here including cups ..

The drop down list does not have my printer but i'm using one that is supposed to work....weird thing is I wonder what mdk is using..btw my printer is a HP officetjet 5500 which is supported in linux . 

Is there some cups command I wonder that mdk runs that ubuntu does not out of the box?....

thx anyone
cheers
neighborlee

---

### Post by ming0 on 2005-05-08
I had this problem, and fixed it, but am editing video in windows ATM.

[font=Verdana]I remember that in the printer setup (in gimp), there was a box that had the print command--something like: lpd -avc[/font]
[font=Verdana][/font] 
[font=Verdana]I just made up the options and the command, but if you take some of the options out, you should be able to print.[/font]
[font=Verdana][/font] 
[font=Verdana]If you can't get it working, post again, and I'll probably be back in Ubuntu in the next few hours, and can look.[/font]

---

### Post by neighborlee on 2005-05-08
[QUOTE=ming0]I had this problem, and fixed it, but am editing video in windows ATM.

[font=Verdana]I remember that in the printer setup (in gimp), there was a box that had the print command--something like: lpd -avc[/font]
[font=Verdana][/font] 
[font=Verdana]I just made up the options and the command, but if you take some of the options out, you should be able to print.[/font]
[font=Verdana][/font] 
[font=Verdana]If you can't get it working, post again, and I'll probably be back in Ubuntu in the next few hours, and can look.[/font][/QUOTE]
--------
I know of the command you speak of yet no amount of editing it is working here....do you actually have same printer I do ?,,if so that would be great since yours is working..

look fwd to reply

cheers
neighborlee

---

### Post by ming0 on 2005-05-09
Unfortunately I haven't got the same printer, but since we had the same symptoms, maybe we have the same problem?

I have a Samsung ML-1430

Here's the Gimp Info: 
Printer Name: ML-1430

Setup Printer > Command: lp -s -dML-1430

I have it set at PostScript Lvl 2, and have no ppd file specified.

Hope this info can help you!

---

