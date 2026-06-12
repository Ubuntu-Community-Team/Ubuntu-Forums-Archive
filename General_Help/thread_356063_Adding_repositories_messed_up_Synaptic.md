---
title: "Adding repositories messed up Synaptic?"
date: 2007-02-08
forum: General Help
---

### Post by boogiepop88 on 2007-02-08
So quick question. I was going to add some custom repositories in synaptic and now i get this error


E: Type 'eb' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


and nothing shows up in synaptic everytime i reload i get the same message. So i removed the custom repos and still the same thing. The repos i was adding were the aiglx apts. I am partially confused why this happened. It did say the first repo i tried to add was no longer there or my network connection needed to be checked after that. I get that message. Internet works. I am confuzzled. Any help would be greatly appreciated. Thanks in advance!  :KS

---

### Post by meng on 2007-02-08
You must have typed 'eb' rather than 'deb' when entering custom repositories. Go back to the repositories section of Synaptic to fix the problem. Or else, drop to the terminal and edit the file /etc/apt/sources.list

sudo nano -B /etc/apt/sources.list

---

### Post by boogiepop88 on 2007-02-08
I didnt see anything wrong, i have removed all the repos through synaptic prior this is my conf

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted unive$# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multive$# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
                               [ Read 33 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell




is there a way to reinstall synaptic without a fresh install, or go back to original synaptic settings? i apologize, im a decent linux user, some stuff i still dont understand.

---

### Post by meng on 2007-02-08
Can you show the entire file please? Probably best to do it this way:
cat /etc/apt/sources.list

If you really can't see any errors now, then it won't hurt to try Synaptic again and press Reload. (Well it won't hurt anyway.)

---

### Post by boogiepop88 on 2007-02-08
ahh ok, that gives me the complete list. i do see where it is entered wrong.  

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
eb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

so how am i able to edit this. According to Synaptic, no repos are active. How would i fix this , in gedit?

---

### Post by meng on 2007-02-08
gksu gedit /etc/apt/sources.list

---

### Post by boogiepop88 on 2007-02-08
ah great! i can now apt again. ill be sure to be more careful next time. Thank you very much meng you were invaluable help,. the ubuntu community is top notch!  ):P

---

### Post by meng on 2007-02-08
Just glad to hear it worked.

---

