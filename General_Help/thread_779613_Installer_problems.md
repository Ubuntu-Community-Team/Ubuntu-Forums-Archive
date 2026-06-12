---
title: "Installer problems"
date: 2008-05-02
forum: General Help
---

### Post by carl99fan on 2008-05-02
I am installing Limewire, I am new to Ubuntu I installed it 4 hours ago on my 1999 Beast!

When I click Install, the following message pops up:
Only one software management tool is allowed to run at the same time.
I have restarted twice, I had just Installed the updates (which did not take) but there is no other programs running that I can tell.
I even went to the processes and stopped the update manager but to no avail.
anybody have any clue?

---

### Post by empthollow on 2008-05-02
hmm, that usually means that there is an apt-get running somewhere.  I would open a terminal and type
```
sudo apt-get -f install
```
this will fix all the broken packages on the system as you mentioned that your updates didn't take.  One other recommendation, instead of limewire, try frostwire at [www.frostwire.com](www.frostwire.com) .  It is based on the limewire code but is free unlike limewire pro, and they have removed all of the drm (digital rights management) parts of the code.

---

### Post by carl99fan on 2008-05-02
> **empthollow said:**
> hmm, that usually means that there is an apt-get running somewhere.  I would open a terminal and type
```
sudo apt-get -f install
```
this will fix all the broken packages on the system as you mentioned that your updates didn't take.  One other recommendation, instead of limewire, try frostwire at [www.frostwire.com](www.frostwire.com) .  It is based on the limewire code but is free unlike limewire pro, and they have removed all of the drm (digital rights management) parts of the code.

Thank you I will, Frostwire......

Um hey! I am all to familiar with Windows and an a Ubuntu virgin.
If you could please tell me where to find this "terminal" and how to open it. lol
I am learning fast but.......

---

### Post by zaussome on 2008-05-02
z

---

### Post by zaussome on 2008-05-02
z

---

### Post by carl99fan on 2008-05-02
Nevermind just found it......
Ok I will try it.

---

### Post by carl99fan on 2008-05-02
> **carl99fan said:**
> Nevermind just found it......
Ok I will try it.

OK I got this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by carl99fan on 2008-05-02
Yea I just tried Frostwire and recived the same message....
Something is still there.
am I using the terminal right? 
seems like the the dos prompt in windows....This is fun! lol
I had ME on this computer and it lost it's "winsock" files I just had it with Windows and I swear I will NEVER go back now!
I can't beleive the performance I am getting out of this old machine.

---

### Post by zaussome on 2008-05-02
z

---

### Post by carl99fan on 2008-05-02
> **zaussome said:**
> There's no real way to use the terminal wrong unless you run [font=courier]sudo rm[/font] ... etc, I'm not going to finish that. Try running [font=courier]dpkg --configure -a[/font].

dpkg: requested operation requires superuser privilege

And i access this superuser priviledge how? 
I mean I have always considered myself a superuser of.... Well I not going to finish that!

:lolflag:

---

### Post by empthollow on 2008-05-02
type sudo before your commmand.  it means superuser do i.e.
```
sudo dpkg --configure -a
```

---

### Post by carl99fan on 2008-05-03
> **empthollow said:**
> type sudo before your commmand.  it means superuser do i.e.
```
sudo dpkg --configure -a
```


Now I'm cookin with fire!!

Thanks very much... very cool.:guitar:

---

