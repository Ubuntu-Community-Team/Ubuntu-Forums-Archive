---
title: "Upgraded to 7.10, and scanner still broke"
date: 2007-12-06
forum: General Help
---

### Post by 999alfred on 2007-12-06
When I first installed Ubuntu 6.x, can't remember which, I had a scanner that worked every time I plugged it in. I had to run scanbuttond to get xsane to preview, but it worked. Then I upgraded to 7.04 and the scanner broke. You plug it in and run 
:~$ scanimage -L
device `canon630u:libusb:003:002' is a CANON Canoscan FB630U flatbed scanner

and it looks ok. But, run 
$ scanimage -T

and you will hear the scanner calibrating to the top, but then nothing. It just sits there fat dumb and happy. Now, sometimes after it sits there for several minutes and you HAVE NOT canceled, ctnrl-C, it will start. But, sometimes it won't.

This happens each time you plug it in or reboot with it plugged in.

Now, if it does run that first time, all is fine after that. But, that's if it ran, and that's a big IF.

So, how do I make it work reliably?

999alfred

---

### Post by der_vegi on 2007-12-25
Yeah, I have the same problem here on a Dell Inspiron 530n with Gutsy from the Dell ISO installed. My scanner simply refuses to work, while it does on another machine with Hardy Alpha. I have filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/118843](https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/118843) .

Anyone any idea how to fix it? I am downloading the Hardy kernel right now, maybe that will work. Just have to wait a while, until it is downloaded, with ISDN connection it takes a little while... :(

---

