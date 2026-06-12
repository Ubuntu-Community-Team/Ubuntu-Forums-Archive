---
title: "renameing a lot of files"
date: 2008-02-10
forum: General Help
---

### Post by mfaust731 on 2008-02-10
hello everyone,
Let me say that i have used ubuntu for a while but I am only now begining to see the true power of the system.
I have hundreds of recordings from my homemade dvr. they are named somethhing like"my movie (Recorded on 12 03 07 WJHL).mpg"

I am trying to create a script that will rename these for me automaticaly to something like "my-movie.mpg"

I want to change the spaces to dashes, and delete everything in the (  and ).

What have so far is:

rename 's/ /-/g' *.mpg

that will change the spaces to dashes, but i dont know how to delete the ( )

thanks for helpin

---

### Post by arsenic23 on 2008-02-10
```
rename 's/\([^)]*\)//' *.mpg
``` Will remove everything inside the first set of ().
```
rename 's/\ \./\./' *.mpg
``` Will remove the unneeded space before the '.'.

And then you already know how to replace the spaces with dashes.

---

### Post by mfaust731 on 2008-02-10
that does just what i need!:)
Thanks

where can I learn what those switches mean, the man page does realy say

---

### Post by arsenic23 on 2008-02-10
[COLOR="DarkRed"]rename 's/\([^)]*\)//' *.mpg[/COLOR]

**\(** is for a literal '('
**[^)]** is any character that isn't a ')'
***** means there can be any number of the previous characters, including zero
**\)** is a literal ')'

and then we replace that with nothing, removing it from the string.

[COLOR="DarkRed"]rename 's/\ \./\./' *.mpg[/COLOR]

I'm just using '\ ' instead of a ' '.
You could just as easily write your ' ' to '-' command like this:
rename 's/\ /-/g' *.mpg

---------------------
Edit:: Sorry, you asked 'where', not 'what'.
My fault.

I'm not sure were a good place to learn the rename command is perse.  I just read up on the sed command, which is very very similiar to rename.
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

