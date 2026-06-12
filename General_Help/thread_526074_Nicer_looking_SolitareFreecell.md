---
title: "Nicer looking Solitare/Freecell"
date: 2007-08-15
forum: General Help
---

### Post by grogger13 on 2007-08-15
I was just playing solitare and freecell on vista and i really liked the sleek design and animations and was wondering if there is anything better for linux then the default games for ubuntu

---

### Post by linuxwizard on 2007-08-15
Look at Pysol. It is the best Solitaire Suite I have found for linux. Can install through Synaptic.

---

### Post by r4ik on 2007-08-15
Have a look at,

[http://big3dsol.sourceforge.net/](http://big3dsol.sourceforge.net/)

Good luck !

---

### Post by grogger13 on 2007-08-25
I couldn't get Big3DSol to work.

I downloaded the sourceforge file and extracted the folder, but the file wouldn't do anything when i clicked on it.  I don't know what im supposed to do with it and there isn't any help about how to get it working

---

### Post by r4ik on 2007-08-25
Suppose you downloaded it from here ?

[http://sourceforge.net/project/platformdownload.php?group_id=185842&sel_platform=3531](http://sourceforge.net/project/platformdownload.php?group_id=185842&sel_platform=3531)

Read about installing tar.gz here,

[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

Good luck !

---

### Post by ferd on 2007-08-25
kpat

---

### Post by fromgi on 2007-10-03
Hopefully you'll find a game more honest than the one shipped with Ubuntu.  You would expect the cards to be randomly determined, like shuffling a deck of cards, but not here.  The next card is logically determined.  This, in my opinion, doesn't add to the excitement of any game.

---

### Post by American_Outcast on 2007-10-03
Deleted this post. I forgot I reinstalled Ubuntu recently and didn't install the correct tools....................... Let me do this the right way first and the I will ask questions if needed.

---

### Post by fromgi on 2007-11-05
Why even bother with the Solitaire supplied with Ubuntu?  Look at the code.  You would expect the cards to be randomly determined, like shuffling a deck of cards, but not here.  The next card is logically determined based on the cards not yet displayed.  Ever wonder why, in most cases, one ace is held until last?  This, in my opinion, doesn't add to the excitement of any game, but only questions it's integrity.

---

### Post by joneall on 2007-11-14
I also cannot get the thing to work. I have unpacked the tar all right, but Big3DSol won't execute. It tells me

./Big3DSol: error while loading shared libraries: libwx_gtk2d_adv-2.8.so.0: cannot open shared object file: No such file or directory

But I have libwxgtk2.6-0 installed. So what gives?

Thanks.

---

### Post by maybeway36 on 2007-11-14
Does kpat do this too?

---

### Post by disturbedite on 2007-11-14
> **joneall said:**
> I also cannot get the thing to work. I have unpacked the tar all right, but Big3DSol won't execute. It tells me

./Big3DSol: error while loading shared libraries: libwx_gtk2d_adv-2.8.so.0: cannot open shared object file: No such file or directory

But I have libwxgtk2.6-0 installed. So what gives?

Thanks.
i think you've got that wrong.  look closer at the file it needs:  libwx_gtk2d_adv-[COLOR=Red]**2.8**[/COLOR].so.0...
you prolly need to install libwxgtk2.8...

---

