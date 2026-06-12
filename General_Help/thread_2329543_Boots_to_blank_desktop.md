---
title: "Boots to blank desktop"
date: 2016-07-02
forum: General Help
---

### Post by thesureone on 2016-07-02
Hello, I really wish to install Ubuntu to give it a try so I can ditch windows 10 if I enjoy it. However this happens every time I try to boot:

[https://www.youtube.com/watch?v=sJYsSz7cVDw&feature=youtu.be](https://www.youtube.com/watch?v=sJYsSz7cVDw&feature=youtu.be)

Basically everytime I try to load it, all it does is say failed to load: Fecs-inst
And then It loads the desktop however it's completely blank.

Any help would greatly be appreciated!
[COLOR=#111111][FONT=Ubuntu]
I'm using usb ubuntu 16.04 and my graphics is Nvidia GTX 960, my model is HP.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is a better picture of the only thing it says during boot: [http://imgur.com/7VKIX2E](http://imgur.com/7VKIX2E)[/FONT][/COLOR]

---

### Post by pandoragami on 2016-07-02
Did you try installing ubuntu using the pendrive linux with the ubuntu iso downloaded from their site at [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) ?

---

### Post by thesureone on 2016-07-02
Yes, that is where I have downloaded the ISO. And I use pendrive universal usb installer.

---

### Post by pandoragami on 2016-07-02
It's weird because for me it works. Were you able to test the desktop before installing it to a disk?

---

### Post by thesureone on 2016-07-02
That's what I've actually tried first in the video I selected try before installing and that's what is happening afterwards. I would have just tried to install but after seeing what happens, not to sure now..

---

### Post by pandoragami on 2016-07-03
What kind of machine are you running, how old is it, mother board type, video card. It should work on an older machine, plus the pendrive is UEFI capable or at least in my case. Mines an ASUS board with a cheap ATI card and it works fine. Is yours factory made by the way, like compaq or dell. I'm not sure but some Windows 10 machines can only run windows or maybe I have it backwards but the UEFI must be windows compatible and maybe it won't run Linux. I'm going off on a limb guessing that last sentence. 

Are you using a usb flash to run the linux desktop? did you look into your bios usb settings for "legacy support",  "UEFI support" or something along those lines.


Ok I just saw you post "[COLOR=#111111][FONT=Ubuntu]I'm using usb ubuntu 16.04 and my graphics is Nvidia GTX 960, my model is HP.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is a better picture of the only thing it says during boot: [http://imgur.com/7VKIX2E](http://imgur.com/7VKIX2E)"

Is this HP a newer model though?

That picture looks like the image on your disk is bad. I wouldn't know how to solve that one, looks like it boots though but crashes due to a kernel panic![/FONT][/COLOR]

---

### Post by pandoragami on 2016-07-03
I would recommend you try xubuntu with the same usb pendrive setup, it might be unity going nuts. [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Download the iso, burn it to a disk or use the usb pendrive software to load it and see if you can test it. Also check the bios for usb support.

---

