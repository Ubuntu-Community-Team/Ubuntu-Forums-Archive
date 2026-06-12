---
title: "kylix3 unreadable menu's"
date: 2005-09-01
forum: General Help
---

### Post by Webgnome on 2005-09-01
He all,

today I installed Kylix 3 on my ubunty notebook. I fired it up ( after installing the newest patch etc ) and I noticed something strange. All menu's and buttons have labels but I cant read them. 

In another thread I saw a change in the startup script and this fixed a little bit. Before I didnt have any textlabels and after the *fix i do have them but they arent, as said, readable. 

Can someone help me with this problem because i dont want to run Windows only for borland c to run

---

### Post by bdamon on 2005-09-01
A couple things you can try.

Try running from a terminal

export LANG=en_US

and

export LD_ASSUME_KERNEL=2.4.1
 
then start kylix from the same terminal and see if that helps.


Ben

---

### Post by Webgnome on 2005-09-01
Thanks m8 this worked. The only thing is.. how do I start borland with the buttons made by the installation and not screwing up my interface again?

* found a minor problem...when i try to type Edit1-> the program crashed with the message: line 25: 8131 Killed /usr/local/kylix3/bin/bcblin

---

### Post by bdamon on 2005-09-01
[QUOTE=Webgnome]Thanks m8 this worked. The only thing is.. how do I start borland with the buttons made by the installation and not screwing up my interface again?

* found a minor problem...when i try to type Edit1-> the program crashed with the message: line 25: 8131 Killed /usr/local/kylix3/bin/bcblin[/QUOTE]

You should be able to find and edit the script that launches kylix, I believe startkylix is one of them startdelphi is another. You can use locate or find to search for them. Add those two lines to the beginning. Another thing you may find you have to do is if your having crashes in the program is to turn off the integrated debugging.


Ben

---

### Post by Webgnome on 2005-09-02
Hello Bdamon

even after turning of the debugging option in kylix the program crashes when i try to type -> or any other thing that pops up that little command menu

---

### Post by bdamon on 2005-09-02
[QUOTE=Webgnome]Hello Bdamon

even after turning of the debugging option in kylix the program crashes when i try to type -> or any other thing that pops up that little command menu[/QUOTE]


I do not know what else you can try. From my experiences Kylix is a bit shaky running under the 2.6 kernel, being it has not been updated in so long. I usually run it on a debian box using a 2.4 kernel and it seems to be very stable.

Ben

---

