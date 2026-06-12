---
title: "Generic Error"
date: 2013-05-28
forum: General Help
---

### Post by sccjono on 2013-05-28
Hello all,

I have started to get a rather vague error message at start-up. After I have logged in a dialogue with "An Error Has Been Detected" appears. The only options I have are to cancel it or report it but there is no information on it at all. Is there anyway to get some more information on what might be wrong? If it is relevant I am running 13.04 x64 and the kernal is 3.8.0-22

I don't know if it is connected but a number of programs will no longer run either. For instance, ubuntu-tweak starts and the splash screen appears and then it just disappears with no error message.


Thanks,
Jon

---

### Post by stylintile on 2013-05-28
Hello sccjono,
     I had the exact same problem before.  It was an issue with apport and those errors were popping up constantly.  I used the fix I found here:

[http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport](http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport)

and that took care of it.  I hope this helps you.

---

### Post by ibjsb4 on 2013-05-28
Should apport be disabled?

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

---

### Post by sccjono on 2013-05-28
Hi stylintile and thanks for the reply. 

It was enabled for me but the section about the log was very useful. I didn't know that log existed and so I might try going through that in the hope it will give me a clue as to what is wrong.

Jon

---

### Post by grahammechanical on 2013-05-28
The Apport dialog has a Details link that when opened will show the information being collected and the library or application that caused the crash. It is also possible to load applications from the terminal. If the app crashes there will be error messages that we do not get when loading by clicking an icon.

You could also try booting into the earlier kernel, 3.8.0-21 by going to Advance Options for Ubuntu at the Grub menu. Do you them get the same problems? What you are experiencing might be due to the kernel update that took us from 3.8.0-21 to 3.8.0-22.

Regards.

---

