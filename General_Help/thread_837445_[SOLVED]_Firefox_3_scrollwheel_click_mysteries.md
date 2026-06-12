---
title: "[SOLVED] Firefox 3 scrollwheel click mysteries"
date: 2008-06-22
forum: General Help
---

### Post by linfidel on 2008-06-22
Firefox 3 is driving me crazy, and I don't know where the problem is coming from.  I tried posting to the Mozilla forum, but so far, no help.  They only seem to care about Windows.

First, can someone simply tell me what happens when you press the middle scrollwheel button by default?  On my system, it skips around in the history, sometimes to the last two, and sometimes to some random place, it seems.

This is causing me problems, because while using the wheel, it often detects a click and jumps to another page.  Perhaps I'm to exuberant while scrolling, or maybe my mouse is too sensitive, but it makes the scrollwheel unusable in Firefox.  No problems anywhere else.

Thanks to anyone that can help.

---

### Post by sidheart on 2008-06-22
I have been using firefox-3 from the day it was launched.I did not encounter any such prob.May be the mouse might be sensitive.

can u plz solve one small problem for me.I am new to ubuntu.can u help me to recover my boot partition's number as in: that (hd0,1) thing.

---

### Post by linfidel on 2008-06-22
> **sidheart said:**
> I have been using firefox-3 from the day it was launched.I did not encounter any such prob.May be the mouse might be sensitive.

can u plz solve one small problem for me.I am new to ubuntu.can u help me to recover my boot partition's number as in: that (hd0,1) thing.Thanks, but one question:  does anything happen when you press the middle button (scrollwheel)?

Now, for your question.  Try opening a terminal, and typing:
sudo fdisk -l
That's a lowercase L.

The response should show a list of devices, and the second column (Boot) tells whether that list item is the boot disk by placing an asterisk (*) in that column.

For the item that has the asterisk, the first column is the device, and should be something like "/dev/sda1".  GRUB uses a slightly different terminology.  It numbers from zero, and instead of a, b, etc, it uses HD0, HD1, etc.  So, 
sda1 = HD0,0
sda2 = HD0,1
sda3 = HD0,2
...
if you have a 2nd drive,
sdb1 = HD1,0
sdb2 = HD1,1
etc.

---

### Post by BUSHYBOB on 2008-06-22
I use the autoscrolling feature of firefox which is activated by clicking the scrollwheel, except if I click on a link with the scrollwheel it opens the link in a new tab.

---

### Post by BUSHYBOB on 2008-06-22
Just rememembered why I stopped using my wireless mouse the scrollwheel click was too sensitive and I was opening new tabs all over the place when scrolling up and down pages before I discovered autoscrolling.

---

### Post by linfidel on 2008-06-22
> **BUSHYBOB said:**
> I use the autoscrolling feature of firefox which is activated by clicking the scrollwheel, except if I click on a link with the scrollwheel it opens the link in a new tab.
Is autoscroll the same as in Windows, where it puts that circle icon with the arrows in it, and you move the mouse up and down for variable scroll?  It's hard to explain, but I assume you know what I mean.

This weird behavior I'm getting is enough to make me want to uninstall Firefox 3, and go back to 2 if I don't get some clue.  Maybe it's something from the desktop effects?  I can't find anything, but that's one thing I hate about desktop effects - there's no way I know to find out what plugin is responding to some particular keyboard or mouse press.  Anyone know if there is a way to find out?

---

### Post by linfidel on 2008-06-22
> **BUSHYBOB said:**
> Just rememembered why I stopped using my wireless mouse the scrollwheel click was too sensitive and I was opening new tabs all over the place when scrolling up and down pages before I discovered autoscrolling.
I'm using a wireless mouse (Logitech).  I never had problems other than Firefox 3.

I can't use autoscroll, though - it doesn't work.

---

### Post by cookies on 2008-06-22
> **linfidel said:**
> Is autoscroll the same as in Windows, where it puts that circle icon with the arrows in it, and you move the mouse up and down for variable scroll?  It's hard to explain, but I assume you know what I mean.

This weird behavior I'm getting is enough to make me want to uninstall Firefox 3, and go back to 2 if I don't get some clue.  Maybe it's something from the desktop effects?  I can't find anything, but that's one thing I hate about desktop effects - there's no way I know to find out what plugin is responding to some particular keyboard or mouse press.  Anyone know if there is a way to find out?

You may have Autoscroll off. Try: Edit > Preferences > Advanced > General Tab
and see if Use Autoscrolling is checked. Check it if it is not.

EDIT: Well, just saw you can't use it. :/

---

### Post by linfidel on 2008-06-22
> **cookies said:**
> You may have Autoscroll off. Try: Edit > Preferences > Advanced > General Tab
and see if Use Autoscrolling is checked. Check it if it is not.

EDIT: Well, just saw you can't use it. :/Actually, I had tried turning it off a while back, and forgot, so I turned it back on.  But it still misbehaves.

With it on, sometimes it will autoscroll, and sometimes it starts to, but then switches to another page.  

I wonder if there's some combination of clicking the scrollwheel and moving the wheel or the mouse that triggers it?  It seems like it goes into autoscroll more often when I have the mouse in the air so the pointer doesn't move, but sometimes it does switch, so maybe it's the wheel.  It's driving me nuts. :)

By the way, I just went in and renamed my .mozilla folder to use a totally new one, and still have this "feature".

---

### Post by BUSHYBOB on 2008-06-22
Do you have another mouse that you could try?

---

### Post by linfidel on 2008-06-23
> **BUSHYBOB said:**
> Do you have another mouse that you could try?
That's a good idea.  And I do.  However, I think I may have figured out a fix - at least, so far, I can't get it to do anything bad.

I modified my xorg.conf file for the mouse, and added some options:
Option          "ZAxisMapping"    "4 5"
Option          "ButtonMapping" "1 2 3 4 5"
Option          "Buttons" "5"

I'm not sure if all of them were required, but all together it seems to work now.

Buttons 4 and 5 are the scrollwheel up and down.  If you have a 7-button mouse, then buttons 6 and 7 are scroll horizontal, I think, which Firefox interprets as scroll history in some cases.  So maybe my mouse was not detected exactly right, and it was somehow emulating buttons 6 or 7 under some condition, like scroll with button pressed or something.  I may play with it some more if I get time.

Thanks for the suggestion.

---

### Post by Ereza on 2008-06-24
> **linfidel said:**
> That's a good idea.  And I do.  However, I think I may have figured out a fix - at least, so far, I can't get it to do anything bad.

I modified my xorg.conf file for the mouse, and added some options:
Option          "ZAxisMapping"    "4 5"
Option          "ButtonMapping" "1 2 3 4 5"
Option          "Buttons" "5"

I'm not sure if all of them were required, but all together it seems to work now.

Buttons 4 and 5 are the scrollwheel up and down.  If you have a 7-button mouse, then buttons 6 and 7 are scroll horizontal, I think, which Firefox interprets as scroll history in some cases.  So maybe my mouse was not detected exactly right, and it was somehow emulating buttons 6 or 7 under some condition, like scroll with button pressed or something.  I may play with it some more if I get time.

Thanks for the suggestion.
Thanks for the fix! I was having exactly the same problem, and I'm sure it's not the mouse fault. I tried enabling autoscrolling but I experienced the same effect than you.

After applying your "fix" it doesn't happen anymore. However, I would like to note that now autoscrolling does not work. For me it doesn't matter as I had it disabled on Firefox 2, but for other people it may matter.

Thanks again!

EDIT: I just checked that autoscrolling DOES work, sorry for the confusion.

---

### Post by linfidel on 2008-06-24
> **Ereza said:**
> Thanks for the fix! I was having exactly the same problem, and I'm sure it's not the mouse fault. I tried enabling autoscrolling but I experienced the same effect than you.
Great, glad it helped.  What type of mouse are you using, just out of curiosity.  I'm wondering if it's only certain mice or types of mice that have the problem.

---

### Post by Ereza on 2008-06-24
> **linfidel said:**
> I'm wondering if it's only certain mice or types of mice that have the problem.
I'm using a Logitech V200 Cordless Mouse connected via USB.

---

### Post by linfidel on 2008-06-25
> **Ereza said:**
> I'm using a Logitech V200 Cordless Mouse connected via USB.

Thanks.

Hmm, I'm using  Logitech cordless mouse, too, although I can't seem to find a model number.

---

