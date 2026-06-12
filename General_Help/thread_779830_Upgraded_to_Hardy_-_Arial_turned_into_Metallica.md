---
title: "Upgraded to Hardy - Arial turned into Metallica"
date: 2008-05-03
forum: General Help
---

### Post by acl123 on 2008-05-03
Hi,
I went to do my weekly budget this morning, which I happen to do in an XLS document. I opened it with OpenOffice as usual, but for some reason all the Arial fonts have turned into the Metallica Pastor of Muppets font! What the hell?

---

### Post by p_quarles on 2008-05-03
Screenshot? :D

More seriously, did you use the update manager, or did you run a fresh install? If the latter, perhaps you forgot to reinstall the msttcorefonts package?

---

### Post by ProsperB on 2008-05-04
Got exactly the same problem here.  I upgraded "with the button".  The problem only occurs in Openoffice 2.4, not in e.g. Abiword.
All fonts are properly installed, I even reinstalled them to no avail.. :(

Edit: reading the previous post anew, I had a look at the font called Metallica (name shown on my system is just Metal, but it's close enough).
Guess what: it looks a whole lot like Arial !
Now I'm baffled... :(

---

### Post by Permafrost91 on 2008-05-04
having the same problems, I deleted the Metallica font and the problem was solved

---

### Post by ProsperB on 2008-05-04
Yeah, got to the same conclusion, but I can't find it yet...
In which directory could it be ?

Edit: I found it in /usr/share/fonts/truetype/ttf-arabeyes with the name of ae_Metal.ttf
Deleted it, 
fc-cache -fv
Start OO

The problem is still there...

---

### Post by Permafrost91 on 2008-05-04
hmm, mine was in ~/.fonts because I had it installed manually at one point. So I removed the font and the .fonts-cache file and rebooted (not sure if 'fc-cache -fv' will do the same, does it?)

But your comment made me curious, so I looked and it turns out I still have a "Metal" font installed (looks like Arial, not like Metallica). But no more weird problems with font rendering.

---

### Post by acl123 on 2008-05-05
Actually, come to think of it, I had problems with this font when I first installed it in January. It has a backwards version, but I couldn't get the backwards version to work in Gimp - it would always just show the forwards version. I posted a bug on it, but I can't find the original bug anymore.

---

### Post by ProsperB on 2008-05-06
Well, I solved my problem :)

Solution is effectively to delete the font replacing arial.
Problem was I couldn't find it...

Found this useful command on the openoffice-forums, posted by an ubuntu-user with more knowledge than me of "fontconfig"

ikke@pjoeter:~$ fc-list : file family | grep -i arial
/home/ikke/.fonts/ariali.ttf: Arial
/home/ikke/.fonts/ariblk.ttf: Arial Black
/home/ikke/.fonts/arialbi.ttf: Arial
/usr/share/fonts/JJSTS___.TTF: Jungle,Arial
/home/ikke/.fonts/arialbd.ttf: Arial
/home/ikke/.fonts/arial.ttf: Arial

Seen that middle line ?
The font with the weird name 'JJSTS___.TTF' (no wonder I didn't find "jungle" ) has TWO internal names: Jungle and Arial.

After deleting it with sudo rm /usr/share/fonts/JJSTS___.TTF
everything went back to normal.  :)

---

### Post by acl123 on 2008-05-06
Thanks that worked for me. Pity I can't type anything in Metallica font any more.
Perhaps we should post this as a bug?

---

