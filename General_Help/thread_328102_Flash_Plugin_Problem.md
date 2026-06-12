---
title: "Flash Plugin Problem"
date: 2006-12-30
forum: General Help
---

### Post by fredster001 on 2006-12-30
Hi,

I tried to play a flash game on [www.teagames.com](www.teagames.com) (with firefox) and it said i needed a plugin. I remembered having to do this with firefox on windows. So i went to here: 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

downloaded the file and installed EXACTLY as it says you should. However know whenever i try to view a flash box or anything with flash in it with firefox the browser closes straight away.

Any ideas on how to fix this?? I have tried re booting with no success.

thanks 

fredster001

---

### Post by meng on 2006-12-30
Are you running 32-bit or 64-bit Ubuntu?
Regardless of adobe's instructions, the easiest way to install flash is like this:
sudo aptitude install flashplugin-nonfree

---

### Post by taurus on 2006-12-30
Make sure you restart firefox.  And at the address field, see if flash is on the list!

```
about:plugins
```

---

### Post by fredster001 on 2006-12-30
ok, put the command that meng suggested into the terminal it all installed, but it hasnt solved the problem.

Not sure whether i am using 32 bit or 64 bit ubuntu. It's version 6.10 if that helps.

Is there a command for all the firefox plugins on this site?
[https://addons.mozilla.org/firefox/plugins/](https://addons.mozilla.org/firefox/plugins/)

Thanks

---

### Post by taurus on 2006-12-30
At the prompt, type

```
uname -a
```

---

### Post by fredster001 on 2006-12-30
which prompt? You mean just straight into the terminal. Should tht fix the flash problem or download plugins?

---

### Post by taurus on 2006-12-30
Type that command into a terminal to see whether you are using 32 or 64 version?  

Here's a link regarding flash 9!!!
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)

---

### Post by fredster001 on 2006-12-30
Excellent i followed the instructions on that page and flash now works.

Thank you very much...

I typed 

uname -a

into the console and it told me this:

Linux freddie-home 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Do you know any other commands for the other firefox plugins?

Thanks

fredster001

---

### Post by taurus on 2006-12-30
You are running the 32bit (x86) version of Edgy...

I usually use automatix2 to install all the plugins for firefox, including the flash!!!

[http://www.getautomatix.com](http://www.getautomatix.com)

---

