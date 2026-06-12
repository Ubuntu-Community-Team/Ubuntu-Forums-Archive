---
title: "How to program your own text entry method?"
date: 2014-09-18
forum: General Help
---

### Post by Saffo on 2014-09-18
Hi Ubuntu Community,

I am still new to Ubuntu but I am very unsatisfied with all of the avilable text entry methods. I would really like to design my own. (For instance I think it's ridiculous that there is no easy way to type an n-dash or m-dash without going into the character map or knowing the unicode for these characters. On a Mac it is simple-- you just type option-dash.) I would really like to rearrange my own, especially since I type in multiple alphabets and I find myself constantly trying to figure out how to type different characters when it is much easier to do so on a Mac.

Is there any easy way to design your own text entry system and add it to the list of available options? Since Ubuntu is open-source I figure that must be possible, right? I do not know any coding but I can look up the unicode values for different characters that I would like to reprogram. There has got to be a way to do this, right?

Thank you very much

---

### Post by mcduck on 2014-09-18
WHat keybpoard layout are you using now then? I'm definitely able to type m-dash simply with AltGr+dash... It really depends just on the keyboard layout you are using, and in general the "international" variants of different layouts give you a lot more characters using different modifier keys.

I don't think I've ever used unicode to type any characters (outside of Windows, at least) , and the character map only for some rarely used non-letter characters...

But if you really have tried varius keyboard layouts, and switching the compose & modifier key settings around, then creating a custom layout shouldn't be too complicated.

---

### Post by dragonfly41 on 2014-09-18
Take a look at AutoKey in Ubuntu Software Centre.

It might meet your needs. Worth an experiment.

---

### Post by Impavidus on 2014-09-18
> **Saffo said:**
> For instance I think it's ridiculous that there is no easy way to type an n-dash or m-dash without going into the character map or knowing the unicode for these characters. On a Mac it is simple-- you just type option-dash
On Linux it's easy too. Just type <compose> - - . for the n-dash and <compose> - - - for the m-dash. You may have to configure the compose key though. Lots of compose sequences available and if you wish you can define your own.

---

### Post by ineuw on 2014-10-18
Autokey cannot generate mdash or other UTF 8 characters as yet. I am having the exact same problem, and I am a user of Autokey.

---

### Post by dragonfly41 on 2014-10-18
> **ineuw said:**
> Autokey cannot generate mdash or other UTF 8 characters as yet. I am having the exact same problem, and I am a user of Autokey.

Apparently so .. [https://code.google.com/p/autokey/issues/detail?id=281](https://code.google.com/p/autokey/issues/detail?id=281)

---

### Post by ineuw on 2014-10-18
dragonfly41, you dug deep, I wasn't even aware of that post/bug report. If you read the posts in their forum, you'll find a number of posts about the subject, including my own. I find it strange that in an OS like Linux, which is both Python and UTF -8 dependent, that someone would write software with such limitation. Because of this, a group of editors at Wikipedia/Wikisource cannot switch to Linux because of the lack of a keyboard macro software. Myself am very reliant on Autohotkey in Windows. It would be impossible to use the compose key for the number of characters, glyphs, diacritic and typographic characters we use, and generate without the ease of a keyboard macro program.

---

### Post by dragonfly41 on 2014-10-19
**ineuw**, I agree with the need for an alternative to AutoHotKey.   
So I decided to research further ... at the risk of morphing this thread into a different topic ...

I found this thread  ...

[http://stackoverflow.com/questions/2460674/easy-to-use-autohotkey-autoit-alternatives-for-linux](http://stackoverflow.com/questions/2460674/easy-to-use-autohotkey-autoit-alternatives-for-linux)

I decided to try SikuliX.   (There is an old version of sikuli in Ubuntu Software Centre but don't use that)

The installation has proven to be fraught with dependencies.

In my first pass at compiling I made the mistake of using version 1.0.1 (as in Ubuntu Software Centre) and not the latest nightly build (1.1.0) which is referred to in SikuliX documents.

So I purged my first attempt and started again loading the download sikulixsetup-1.1.0.jar into ~/SikuliX.

I double clicked on the jar and installation started.

I found from next attempt that some dependencies were missing in my Ubuntu 14.04 so again I purged the 
installation and using Synaptic Package Manager installed the following:-

libhighgui2.4
libhighgui-dev

install libcvaux-dev
install libcvaux2.4

install libcv-dev
install libcv2.4     (note: see later that libcv2.3 is expected in installation)

install libtesseract-dev
install libtesseract3

However I'm not sure if I need all the above.

And again I ran sikulixsetup-1.1.0.jar

But I do not install to completion.

SikuliX-1.1.0-SetupLog.txt reports at end ..

```

[error (10/19/14 9:09:28 PM)] ResourceLoader: loadLib: Fatal Error 110: loading: libVisionProxy.so
[error (10/19/14 9:09:28 PM)] ResourceLoader: loadLib: Since native library was found at /home/user/SikuliX/libs
 it might be a problem with needed dependent libraries
ERROR: /home/user/SikuliX/libs/libVisionProxy.so: libopencv_core.so.2.3: cannot open shared object file: No such file or directory

```

searching for "libopencv_core.so.2.3" only version 2.4 is installed in lib.

```

/usr/lib/i386-linux-gnu/libopencv_core.a
/usr/lib/i386-linux-gnu/libopencv_core.so
/usr/lib/i386-linux-gnu/libopencv_core.so.2.4
/usr/lib/i386-linux-gnu/libopencv_core.so.2.4.8

```

Has anyone recently installed the nightly build of SikuliX-1.1.0 on Ubuntu 14.04?

e.g. where can I get earlier version of libopencv_core.so.2.3 which SikuliX expects in ~/SikuliX/libs folder?

...

See this "hello world" tutorial to get an idea of the end goal.

[http://doc.sikuli.org/tutorials/helloworld/helloworld-mac.html](http://doc.sikuli.org/tutorials/helloworld/helloworld-mac.html)

So it appears that SikuliX could work like AutoHotKey.

---

