---
title: "Help! Deleted a spam post on my SMF forum and viruses installed!"
date: 2008-06-09
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-09
Hi every1,

I have an SMF forum setup for a client, and my Dad ( who I work with )found a spam post of porn. He clicked delete and he said about 30 windows opened and his computer went nuts. I came home and he was virus scanning his computer and I said forget that it's gonna need reformatting as it's vista.

I'm running through the reformat now. The thing is my Dads USB drive was plugged in and he quickly unplugged it when he realized something was wrong. What should I do about the hard drive? What's the chances if it being infected? If it is should I take it into Ubuntu and extract the important data? Should I be worried about the other computers on the network? Is my forum at risk? Could some malicious code be added to the PHP? Are others visiting the forum at risk? ( which will be my clients customers )

Any help on what I should do would be really appreciated. The first forum I thought of to ask for help was here! 

Cheers

---

### Post by tom66 on 2008-06-09
If you can backup stuff in Ubuntu, do. 

Ubuntu won't be infected by any of the viruses in Windows (and even if it was, they'd never succeed because Linux is locked down).

You might want to just copy the files on to the Ubuntu drive, it's highly unlikely the virus can read ext3, or the type of filesystem Ubuntu/Linux uses.

---

### Post by garethsimpsonuk on 2008-06-09
So you think the drive might be infected? is it likely? it's a lot of data but some of it is important, my Dads in the army and it has confidential files on. What about the forum? if it's been donce it can be done again I have all security enabled though ( it's on a namesco server by the way )
It's making me think about the security of my ubuntu home server, I didn't realise I was so at risk. 
Has anyone heard of this? A script that runs when you try to delete the post

---

### Post by garethsimpsonuk on 2008-06-09
I didnt even think how am i going to get rid of the virus post? it's still there

---

### Post by tom66 on 2008-06-10
Ubuntu *shouldn't* be infected. But, to make sure, get the lynx program (sudo apt-get install lynx) then delete the virus using the text web browser. It might be a bit different...

---

### Post by garethsimpsonuk on 2008-06-10
yea that's good idea. The thing is didn't delete when my Dad done it
Does anyone know if the USB drive is in trouble? How did this happen? Is it an SMF exploit

---

