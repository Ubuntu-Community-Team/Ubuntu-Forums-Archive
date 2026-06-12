---
title: "visudo editor"
date: 2008-04-30
forum: General Help
---

### Post by Kilarin on 2008-04-30
Hello!  I'm trying to add truecrypt to my sudoers file so I can mount/dismount truecrypt volumes without having to enter the root password every time.   

In Ubuntu 7.10   Truecrypt 4.3 I had this line in sudoers:
```
donald ALL= NOPASSWD: /usr/bin/truecrypt
```

Which worked fine until I upgraded to ubuntu 8.04 and truecrypt 5.1a.  Now suddenly I have to enter the root password every time.  

SO, I was following the instructions on this page: 
[http://www.linewbie.com/2008/01/install-and-configure-truecrypt-with-gui-on-ubuntu-710.html](http://www.linewbie.com/2008/01/install-and-configure-truecrypt-with-gui-on-ubuntu-710.html)
Which recommends adding a truecrypt group and putting that into the sudoers file.  So, I've added the truecrypt group in "users and groups", no problem.

BUT, I'm running into a "you're a stupid user" problem when I try to add the truecrypt group entry to the sudoers file.

When I type sudo visudo, I get this odd editor that I THINK is the nano editor?  And, that thing won't seem to let me add a new line without messing up all kinds of other things.  Even simple cut and paste seems to go goofy.  So, I thought I'd just use gedit instead.

BUT: 
```
export EDITOR=gedit
sudo visudo

or
export EDITOR=gedit && sudo visudo

```

still just brings up the nano editor.   

So, why can't I use gedit?  I suppose that learning nano would be good for me, but I'm disturbed that I can't get gedit to work.

Any help would be appreciated.

---

### Post by Monicker on 2008-05-01
> **Kilarin said:**
> Hello!  I'm trying to add truecrypt to my sudoers file so I can mount/dismount truecrypt volumes without having to enter the root password every time.   

In Ubuntu 7.10   Truecrypt 4.3 I had this line in sudoers:
```
donald ALL= NOPASSWD: /usr/bin/truecrypt
```

Which worked fine until I upgraded to ubuntu 8.04 and truecrypt 5.1a.  Now suddenly I have to enter the root password every time.  

SO, I was following the instructions on this page: 
[http://www.linewbie.com/2008/01/install-and-configure-truecrypt-with-gui-on-ubuntu-710.html](http://www.linewbie.com/2008/01/install-and-configure-truecrypt-with-gui-on-ubuntu-710.html)
Which recommends adding a truecrypt group and putting that into the sudoers file.  So, I've added the truecrypt group in "users and groups", no problem.

BUT, I'm running into a "you're a stupid user" problem when I try to add the truecrypt group entry to the sudoers file.

When I type sudo visudo, I get this odd editor that I THINK is the nano editor?  And, that thing won't seem to let me add a new line without messing up all kinds of other things.  Even simple cut and paste seems to go goofy.  So, I thought I'd just use gedit instead.

BUT: 
```
export EDITOR=gedit
sudo visudo

or
export EDITOR=gedit && sudo visudo

```

still just brings up the nano editor.   

So, why can't I use gedit?  I suppose that learning nano would be good for me, but I'm disturbed that I can't get gedit to work.

Any help would be appreciated.


AFAIK, that export option will only work with command line editors.

---

### Post by kerry_s on 2008-05-01
the closest thing for gui editor that works on sudoers is xedit. its already installed. just->
sudo xedit /etc/sudoers

add your lines, then click save 2x, then quit.
left & right mouse click on the scrollbar to move the page up or down or pageup/pagedown or arrow keys. :)


to select your console editor->
sudo update-alternatives --config editor

to learn vi, save this page->
[http://www.uga.edu/~ucns/stddocs/vi-tutor.txt](http://www.uga.edu/~ucns/stddocs/vi-tutor.txt)

open it with vi
vi vi-tutor.txt

---

### Post by Kilarin on 2008-05-12
> to learn vi, save this page->
[http://www.uga.edu/~ucns/stddocs/vi-tutor.txt](http://www.uga.edu/~ucns/stddocs/vi-tutor.txt)
That got me through it.  thanks!

---

### Post by Kilarin on 2008-05-13
Well, it got me through editing the sudoers file.  BUT, that didn't solve my problem.  I should have realized from the begining what it was.

When I installed truecrypt 5.1a, it apparently left the old truecrypt installed and named the new one something different or placed it somewhere different. 

typing: truecrypt at the prompt runs truecrypt 5.1a.  
BUT, typing /usr/bin/truecrypt -V  runs the old version 4.3a

So, the problem all along was just that I needed to change the path/name of truecrypt that was already in my sudoers file.  Obvious really.

BUT, now I have the age old problem of, how the heck do I figure out where truecrypt 5.1a is installed?

Any help would me much appreciated.  thanks!

---

### Post by Monicker on 2008-05-13
Try
```

which truecrypt
```

---

### Post by Kilarin on 2008-05-13
> which truecrypt
HURRAY!  Now THATS a nice command to know, thank you VERY much!

---

