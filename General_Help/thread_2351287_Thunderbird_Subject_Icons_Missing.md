---
title: "Thunderbird Subject Icons Missing"
date: 2017-02-01
forum: General Help
---

### Post by LinuxRocks on 2017-02-01
HI Forum,

I have installed Ubuntu 16.04 and updated. I am using Thunderbird as my e-mail client and when I get e-mails that have icons in the subject line, they are presented as boxes with numbers in them.. Like this image:

[IMG]https://joeman1.com/images/codeview.png[/IMG]

Here is how the same image looks using Fedora 25 and Thunderbird:

[IMG]https://joeman1.com/images/birthdayimage.png[/IMG]

What do I have to install to make that happen?

Thanks!
Joe

---

### Post by LinuxRocks on 2017-02-17
Keeping this one alive... Anyone???

---

### Post by billrbilly on 2017-02-17
Looking at the first image it looks like it's using **[SIZE=2]BIRTHDAY CAKE (U+1F382) [/SIZE]**

Here's some info on the font support
[http://www.fileformat.info/info/unicode/char/1f382/fontsupport.htm](http://www.fileformat.info/info/unicode/char/1f382/fontsupport.htm)

> [COLOR=#333333][FONT=&amp]The default image is using the Symbola font[/FONT][/COLOR]

Is the Symbola font installed on your machine?
You can look in Synaptic package manger..
I'm not 100% positive, I don't believe you need the whole
ttf-ancient-fonts package installed just ttf-ancient-fonts-symbola

---

### Post by LinuxRocks on 2017-02-17
> **billrbilly said:**
> Looking at the first image it looks like it's using **[SIZE=2]BIRTHDAY CAKE (U+1F382) [/SIZE]**

Here's some info on the font support
[http://www.fileformat.info/info/unicode/char/1f382/fontsupport.htm](http://www.fileformat.info/info/unicode/char/1f382/fontsupport.htm)



Is the Symbola font installed on your machine?
You can look in Synaptic package manger..
I'm not 100% positive, I don't believe you need the whole
ttf-ancient-fonts package installed just ttf-ancient-fonts-symbola

Hey billrbilly,

Thanks! That looks like it fixed some of the other ones too :)...

Just out of curiosity... How did you find out what code that was, or have you ran into this before?

Thanks so much!
Joe

---

### Post by billrbilly on 2017-02-18
Most of the characters are included in the first image you posted, inside the box
It's just a matter of tracking down which font is unsupported...

Glad to help :D
Bill

---

### Post by LinuxRocks on 2017-02-18
HAH, I never though to actually put the code into Google, but voila - when I do, there is the info...

You ROCK!

Thanks again!
Joe

---

