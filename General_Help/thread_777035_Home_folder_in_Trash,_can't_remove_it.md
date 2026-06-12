---
title: "Home folder in Trash, can't remove it"
date: 2008-05-01
forum: General Help
---

### Post by Gruss2 on 2008-05-01
Hello, somehow I accidentally dragged and dropped my Home folder into the trash and now I can't remove it.  

I still have a Home folder outside the Trash folder where it normally stays, but the one in the Trash folder will not be deleted or removed. If I try to remove it from the Trash folder, it just makes a copy...a Home folder 2.  How can I permanently remove it from my Trash folder without deleting it?  Or can I safely delete it without losing the original contents within the Home folder?

---

### Post by Urik on 2008-05-01
LOL, man ))))))))
you can empty it in 
~/.local/share/Trash/files  , if it doesn't give you a permission, use "sudo". If it warns you about an incompatible user DNA, use Windows ))

> sudo rm -Rd ~/.local/share/Trash/files/*

Be careful with "rm" command!

---

### Post by Gruss2 on 2008-05-01
Thanks! :)   That helped.   =D>

---

### Post by chrisccoulson on 2008-05-01
That's really wierd. It shouldn't even be able to get there in the first place. Nautilus should stop you copying or moving a folder in to a folder below it (for obvious reasons). I don't know how you can copy or move something like '/home/user' in to '/home/user/.local/share/Trash'

Do you remember how you managed to do it?

---

### Post by Gruss2 on 2008-05-01
It was on my Desktop with other folders I created. While doing a multiple folder delete by holding down the CTRL key, I didn't know my Home folder was also highlighted for deletion. So it was sent to the Trash with the other folders I created.

I was surprise too that I was able to accidentally delete my Home folder...GNOME should have prevented me or warned me against it. Maybe it was just a fluke. I'm just glad I don't have to see it in the Trash anymore. I wanted to see my Trash bin empty. :)

---

### Post by chrisccoulson on 2008-05-01
Just tried it on my system, and holding down CTRL will allow it to copy. The side effect is that you end up with never ending hierarchy (/home/user/.local/share/Trash/files/user/.local/share/Trash/files/user/.local/share/Trash/files etc... you get the picture)

---

### Post by Gruss2 on 2008-05-01
Right after posting my last response on the forum, just as an experiment, I right clicked on my Home folder along with a couple other folders on my desktop. Now the option to send to the Trash is grayed out, so I don't know how was able to delete it. This did happened right after I upgraded to Hardy, so maybe the protection settings didn't kick in yet. :confused:

---

