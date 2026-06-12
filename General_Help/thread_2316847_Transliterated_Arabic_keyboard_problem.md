---
title: "Transliterated Arabic keyboard problem"
date: 2016-03-11
forum: General Help
---

### Post by coldraven on 2016-03-11
I'm following the advice in this blog to write transliterated Arabic. [https://sites.lsa.umich.edu/kchalipa/2015/09/26/diacritics/](https://sites.lsa.umich.edu/kchalipa/2015/09/26/diacritics/)

 It's all working apart from one thing, I need two extra characters U01E7 and U01E6 ( &#487; and &#486; ). I first tried by editing the entry for 8 so it looks like this
```
key <AE08> { [ 8, asterisk, U01E7, U01E6 ] };
```
That did not work, with AltGr+8 I get these &#8226;&#8226;&#8226;&#8226;&#8226; and with Shift+AltGr these °°°°°°°

So then I tried editing the X key to look like this
```
key <AB02> { [ x, X, U01E7, U01E6 ] };
```
That did not work, with AltGr+x I get these &#7829;&#7829;&#7829;&#7829; and with Shift+AltGr+x these &#7828;&#7828;&#7828;&#7828;

But looking at the layout chart  shows it exactly as planned. I've tried rebooting and it still won't work :( Any ideas?

---

### Post by coldraven on 2016-03-12
I followed the links to here and did this: [https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions)

> You may have to clear the pre-compiled keymaps before your modifications work:
```
cd /var/lib/xkb/
sudo rm *.xkm
```

Now everything is misbehaving :( If I press the Super key I get a login screen!
Ctrl+Alt+right/left arrow used to switch workspace, now it minimises this browser.
All the key mapping that worked yesterday has gone.

Coupled with the bug that randomly changes the keyboard from UK to US several times a day I'm getting a bit impatient with Ubuntu. Maybe another distro will not have these problems

---

### Post by coldraven on 2016-03-13
Dear mods, I think that the help in my previous post should be edited*. My laptop is now almost useless after deleting the the pre-compiled keymaps. I cannot get to the Dash by any means, I cannot get a terminal. :(

Edit: *Maybe use rename Instead of deleting all the xkm files

---

### Post by coldraven on 2016-03-13
More bad news! 
I was reading this in the hope that I could fix my laptop:
[http://askubuntu.com/questions/510024/what-are-the-steps-needed-to-create-new-keyboard-layout-on-ubuntu](http://askubuntu.com/questions/510024/what-are-the-steps-needed-to-create-new-keyboard-layout-on-ubuntu)

When use Ctrl+Alt+F1 to get a shell it closes my browser. When I return to the DE with Ctrl+Alt+F7 all programs that were running are closed. So my attempts to search for an answer is lost each time. How can I recreate the pre-compiled keymaps?
I cannot use Ctrl+Alt+T for the same reason and as I said in my last post I cannot get to the Dash anymore. Woe is me :(

---

### Post by Bashing-om on 2016-03-13
coldraven; Hey ...

From grub can your boot to terminal ?
What release are you running .. systemd/upstart ? The method to boot to terminal differs.

In upstart ...maybe try:
```

sudo apt-get --reinstall install xkb-data

```


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by coldraven on 2016-03-13
> **Bashing-om said:**
> coldraven; Hey ...

From grub can your boot to terminal ?
What release are you running .. systemd/upstart ? The method to boot to terminal differs.

In upstart ...maybe try:
```

sudo apt-get --reinstall install xkb-data

```
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]

Firstly to answer you question I'm running 15.10 which AFAIK uses upstart.
Secondly, you genius that fixed it! I don't normally throw kisses onto the interwebs but in your case I'll make an exception ===> xxxxx :)

As I'm connected via wi-fi I used Ctrl+Alt+F1 to get a terminal and used your command. I figured that at grub the wi-fi probably would not have yet been enabled.
Thanks again, now I can start all over  with the Arabic transliteration. I definitely will not be deleting any pre-compiled keyboard settings!!!

---

### Post by Bashing-om on 2016-03-13
coldraven; He he ...

Great .. no genius here ... I just been around a bit .. sometimes the sow finds an acorn !
Every time I mess with this system, I find deeper what I do not know . I do work to make that not happen and someday I may graduate.

see if : 
[http://madduck.net/docs/extending-xkb/](http://madduck.net/docs/extending-xkb/)
points ya in a good direction for the Arabic transliteration. 

[INDENT][INDENT]an adventure in learning
[/INDENT][/INDENT]

---

### Post by coldraven on 2016-03-13
Dear Bashing-Om, I am actually laughing out loud. This forum is the reason that I came here originally, by which I mean that I adopted Ubuntu in the first place.
Peace. BTW I could tell you what Om actually means. It saved my life. Here we go: It means I existed a moment ago, I exist now and I believe that I will exist a moment into the future.
Hope this helps :) (I have had an interesting and quite varied life)

---

### Post by Bashing-om on 2016-03-13
coldraven; Yeah !

I wondered where I got that "Bashing-om" from .. <- that about sums it up !
Sometimes I am beating on bash, most of the time bash is beating on me.
Bash == an extentsual existence. A rapidly moving target.

[INDENT][INDENT]take care
look forward to more fun
[/INDENT][/INDENT]

---

