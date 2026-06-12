---
title: "[SOLVED] R.A.T 9 Mouse and Ubuntu 13.04"
date: 2013-07-03
forum: General Help
---

### Post by rbasset on 2013-07-03
_**THIS HAS BEEN SOLVED**_

So i decided to come back to Ubuntu after about a year of not using it, i missed it. However In that year I have bought the Mad Catz R.A.T.9 .

Then i installed Ubuntu, the mouse worked fine for about 30 seconds but then i noticed that the system wasn't capturing my input with the mouse.
I then searched the forums here and came accross ---

[http://ubuntuforums.org/showthread.php?t=1661126](http://ubuntuforums.org/showthread.php?t=1661126)

with a great post from [**[COLOR=#000000]thothommy[/COLOR]**]("http://ubuntuforums.org/member.php?u=543566"), now i dont speak German so i dont know what all he was saying but when i was in the Terminal i tried the following command,

> 
#!/bin/bash
sleep 20 && imwheel -k -b "0 0 0 0 8 9 10 11 12" ;


AND IT WORKED!!

I do however have a few issues such as, i type this command in, when its started imwheel i then have to log out and back in to get it working fully.
and i CANNOT get it to run at startup. I've tried to set up the command in the "Startup Applications" but to no avail doesn't work.


I then tried the rest of his script and still it didnt work.


so in conclusion i am looking for a way to get my mouse working in Ubunru 13.04 (his Tutorial was made for 10.04) without having to log out then back in i would like it to work on startup aswell.

Thanks in advance
Robert

---

### Post by 2F4U on 2013-07-04
There is a newer solution available:

[http://ubuntuforums.org/showthread.php?t=2063383](http://ubuntuforums.org/showthread.php?t=2063383)
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+question/192285](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+question/192285)

---

### Post by rbasset on 2013-07-04
Hey thanks 2F4U that worked great!

---

