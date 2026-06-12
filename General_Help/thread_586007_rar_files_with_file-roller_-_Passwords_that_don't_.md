---
title: "rar files with file-roller - Passwords that don't exist?"
date: 2007-10-21
forum: General Help
---

### Post by blackaardvark on 2007-10-21
I've found that file-roller will not extract some files and it tells me there's a password, when there isn't.  Right now I have to use WinRar with wine which works fine. 

Is there a more elegant and non-wine dependant way of doing this, and why does it happen in the first place?  

thanks in advance.

---

### Post by Beggar on 2007-10-21
Someone smarter then me will have to figure out why it doesnt work, but in the meantime have you tried unrar from the command line?

---

### Post by elgalloloco on 2007-10-23
> **blackaardvark said:**
> I've found that file-roller will not extract some files and it tells me there's a password, when there isn't.  

I keep getting the same problem...:confused:

---

### Post by Toadmund on 2007-11-12
Me too, trying to unrar some .iso's, keeps repeatedly asking for a password, one is supplied, but it does not work, keeps asking.

Does not work.

---

### Post by orkerone on 2008-03-26
Got the same problem here...

---

### Post by mishathegoat on 2008-03-29
Same problem anyone find a good solution?

---

### Post by monraaf on 2008-03-29
Install the **unrar** package (the non-free version). It's a command line tool that should work with all rar archives.

---

### Post by danwood76 on 2008-03-29
I personally have had no issues unraring with fileroller, after installing unrar-nonfree from the repos.
Havent tried the free version, is this what you are all using?

---

### Post by TenPlus1 on 2008-03-29
When file-roller comes across a .rar file that hasn't passed the md5 checks, it'll pop up asking for a password for some reason ?!?!  The only way to get around this is to UnRar the archive using terminal and use the -kb switch to keep broken files...

Unrar e -kb <file.rar>

---

### Post by nebu on 2008-03-29
try repairing the rar files with gpar..... this is a little time consuming.... but it works....its available with the synaptic package manager.....

another way of going around this is installing winrar using wine....... this works out very well

---

