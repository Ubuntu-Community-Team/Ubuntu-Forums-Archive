---
title: "How do I make Deluge the default torrent?"
date: 2008-02-05
forum: General Help
---

### Post by Luvis8 on 2008-02-05
I searched the forums for an answer but found none.
I am using Ubuntu 7.10 and Firefox 2.0.
I have installed Deluge and it does appear in the Application/Internet tab, however when I select a file to download "Bit Torrent" is the only application which appears and when I select "other" I am brought to the file manager and cannot find any applications.
Please help as I would really like to use Deluge.

---

### Post by mikewhatever on 2008-02-05
Look here first [http://deluge-torrent.org/faq.php#6n54](http://deluge-torrent.org/faq.php#6n54). If you like a program, it's really helpful to read its FAQ.

---

### Post by Luvis8 on 2008-02-06
Thanks Mikewhatever,
I did read the FAQ and unfortunately it is impossible to follow these steps.
When I right click on the torrent file and click on "Properties", I do not get any tabs at all, all I get is a window with some information.
So it is impossible to select "Deluge" or click on "Add" as these options simply are not present. 

Some additional information which I forgot to mention in my first post:
I had first installed Bit Tornado, didn't like it so I then installed Deluge.
When I wasn't given the option of Deluge I deleted Bit Tornado.
When that didn't work I deleted Deluge, rebooted and then reinstalled Deluge.
I don't know if this information helps in diagnosing the problem.

It's still not working and hence I posted my message hoping to find someone who could help.

---

### Post by FuturePilot on 2008-02-06
Right click on a .torrent file and go to Properties. Click the Open With tab and select Deluge from the list.

---

### Post by Luvis8 on 2008-02-06
Thanks FuturePilot,
I went and did that (the only files that I've downloaded via torrent are Linux iso's so I chose one of them).
Well still no luck.
When I try download a torrent file, Firefox gives me Bit Torrent as my only choice :confused:
I even tried rebooting.
Am I going to have to reinstall Ubuntu?

---

### Post by FuturePilot on 2008-02-06
Try a .torrent file. Not a file you downloaded via bittorrent, but an actual .torrent file that ends with .torrent.

---

### Post by mikewhatever on 2008-02-06
According to your fist post, you want to make Firefox aware that Deluge is your torrent application of choice. To do this, click 'other' and and check 'Do this automatically for files like this from now on', then, in the next window, navigate to the executable or simply type the full path, /usr/bin/deluge.

---

### Post by Luvis8 on 2008-02-09
Thank you for your last post Mikewhatever, that did the trick!

---

### Post by kleo skywalker on 2008-03-04
> **mikewhatever said:**
> According to your fist post, you want to make Firefox aware that Deluge is your torrent application of choice. To do this, click 'other' and and check 'Do this automatically for files like this from now on', then, in the next window, navigate to the executable or simply type the full path, /usr/bin/deluge.

The executable file - it should be something called deluge with a little rhombus icon next to it, shouldn't it? Or is it ok to have an executable text file? That is what I have for Deluge.

I have another little Deluge problem - sometimes, when I manually add a URL, nothing happens after I click "Ok".

---

