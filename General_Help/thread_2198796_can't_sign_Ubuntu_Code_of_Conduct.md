---
title: "can't sign Ubuntu Code of Conduct"
date: 2014-01-10
forum: General Help
---

### Post by Buntu Bunny on 2014-01-10
I spent the better part of this morning trying to sign the Ubuntu Code of Conduct. Everything went well until I got to

```

gpg --clearsign UbuntuCodeofConduct-2.0.txt
```

I got the error

```
gpg: can't open `UbuntuCodeofConduct-2.0.txt': No such file or directory
gpg: UbuntuCodeofConduct-2.0.txt: clearsign failed: file open error

```

I researched this and followed [these instructions at AskUbuntu]("http://askubuntu.com/questions/151998/why-cant-i-gpg-sign-the-ubuntu-code-of-conduct"), changing the 1.1 to 2.0. I still get the same error message. 

Suggestions?

---

### Post by Bashing-om on 2014-01-10
Buntu Bunny; Hello my friend ;

I fought signing the document also for the longest time, What I finally found was I was using the wrong key to authenticate.

If I might suggest, delete everything you have done to this point and start all over. The directions do work - hey I recently did this -, step by step, one step at a time and copy and paste all that you can to preclude errors. Make sure you are working with the correct files ! Double check at each step.

edit:
> 
-rw-rw-r--  1 sysop sysop      8579 Dec  9 13:04 UbuntuCodeofConduct-2.0.txt


[INDENT][INDENT]Can not help directly, but I have a lot of
[INDENT][INDENT][INDENT]empathy for ya !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-10
Buntu Bunny; Addendum !

This is the file you are going to submit (has your GPG sig attended to it).
> 
 -rw-rw-r--  1 sysop sysop      9116 Dec  9 15:49 UbuntuCodeofConduct-2.0.txt.asc


[INDENT][INDENT]I do hope this helps
[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2014-01-10
> **Bashing-om said:**
> Buntu Bunny; Hello my friend ;

.... <snip> ....

[INDENT][INDENT]Can not help directly, but I have a lot of
[INDENT][INDENT][INDENT]empathy for ya !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

You may not always have answers, but you are always an encourager! I took your advice, read carefully, and double checked everything. 

What I finally figured out is that 

```
wget -O- https://launchpad.net/codeofconduct/2.0/+download | gpg --clearsign | xsel --clipboard
```

copied the correct response directly to my clipboard. I was thinking it should show up in terminal(!) After I ran that code all I had to do was Ctrl+V into the appropriate box on Launchpad. Done!

Always a relief to have someone in my corner, and you've been that. Thanks Bashing-om!

---

### Post by Bashing-om on 2014-01-10
Buntu Bunny: Hey !

Not a problem .  Glad ya got it all sorted out.

We are all in this together ->
[INDENT][INDENT]one for all and all for 1
[/INDENT][/INDENT]

---

