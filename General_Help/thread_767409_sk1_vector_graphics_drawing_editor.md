---
title: "sk1 vector graphics drawing editor"
date: 2008-04-25
forum: General Help
---

### Post by gobuntu on 2008-04-25
Dear friends,

I installed sk1 from their site.

It does not show in the Applications/Graphics drop-menu.

So, in a terminal I typed "sk1" and got this reply:

"Cann't find Python binding for LittleCMS!"

Can someone please help on what I need to do, in order to run sk1?

Thanks!

---

### Post by kakao on 2008-05-15
> **gobuntu said:**
> 
"Cann't find Python binding for LittleCMS!"


Have you found a solution to this? On Hardy I'm getting the same error after installing the [Feisty packages]("http://sk1project.org/modules.php?name=Products").

---

### Post by asiastar on 2008-11-25
Bump.

I recently updated from 8.4 to Ubuntu 8.10 and now get that error too. I have all the necessary packages installed, as mentioned in a [post on their website]("http://www.sk1project.org/forum/printpage.php?forum=1&topic=38.") 

At this [French post]("http://forum.ubuntu-fr.org/viewtopic.php?id=202887"), it is mentioned that the packages need to be installed in a certain order. Maybe I made the mistake there. Is that possible? Sorry, I'm a noob and don't really know.

Could someone help me out please? 

If it is the case that the order needs to be maintained for the installation, how do I uninstall Sk1? I downloaded the deb file from their website, but can't find an uninstaller. 

That the order is important is also indicated on [another post on the Sk1 website]("http://sk1project.org/forum/topic.php?forum=1&topic=48"). The poster mentions uninstalling his first attempt and re-installing.

If someone told me how to do that, I'd probably get it to work. I'm totally fine with copy&paste terminal commands...

Any help? Somebody? Anybody?

---

### Post by buixuanduong1983 on 2008-12-24
Did you find the answer for your question? I checked the [forum in Sk1 website]("http://sk1project.org/forum/topic.php?forum=1&topic=48") and found this command to solve that error and it works for me (Ubuntu 8.10):

sudo ln -s /usr/share/python-support/python-liblcms/lcms.py /usr/lib/python2.5/site-packages/lcms.py

---

### Post by amr2205 on 2009-01-08
> **buixuanduong1983 said:**
> Did you find the answer for your question? I checked the [forum in Sk1 website]("http://sk1project.org/forum/topic.php?forum=1&topic=48") and found this command to solve that error and it works for me (Ubuntu 8.10):

sudo ln -s /usr/share/python-support/python-liblcms/lcms.py /usr/lib/python2.5/site-packages/lcms.py

Thanks! It worked for me! :D

---

### Post by RJARRRPCGP on 2009-01-21
Anyone getting this error message?

**Cannot find Python binding for LittleCMS! **



And I still get the same error message even when I typed the following, which I was instructed to do at the sk1 message board:

**sudo ln -s /usr/share/python-support/python-liblcms/lcms.py /usr/lib/python2.5/site-packages/lcms.py**

The above mentioned error message just repeats! Am I required to reboot after making the symlink?

---

### Post by hollymcr on 2009-03-02
I also had problems with this error but got mine working.

After I first got the error I found advice elsewhere to:```
sudo gedit /usr/lib/python2.5/site-packages/sk1/app/managers/colormanager.py
```
.. and then edit line 9 from 
   from lcms import
to
   from lcms.lcms import

Then I found this thread and tried the "ln -s" trick. Neither worked.

However, then I tried undoing the gedit change (ie "lcms.lcms" back to "lcms") and sK1 loaded fine.

So in case anyone else gets here after trying the first fix, undo it before (or after!) trying the second fix!

PS: I'm on Intrepid (8.10).

---

### Post by stani on 2009-05-20
I've made packages for Jaunty and Intrepid in my PPA repository (including 64 bit):
[http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html](http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html)

---

### Post by ogromano on 2009-08-02
Hi..

I can't get this to work on 8.04. I followed all the steps on their website and everything seems to have installed fine but I just get the following on a terminal after typing sk1:

Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named sk1

I see some people got similar errors, but their output listed more clues to follow... I need help. Still a linux newb so it's difficult for me to trace or look for any other info.

---

### Post by confusio on 2010-03-25
Hi
I am running Ubuntu 9.10 and SK1 is running properly
What I did is as follows:

1- in terminal execute sudo ln -s /usr/share/python-support/python-liblcms/lcms.py /usr/lib/python2.5/site-packages/lcms.py

2- created a launch in the desktop, simply executing the sentence "sk1" et voila

THE APP IS UP AND RUNNING!

---

