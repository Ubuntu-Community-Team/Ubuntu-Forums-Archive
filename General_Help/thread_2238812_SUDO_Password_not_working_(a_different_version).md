---
title: "SUDO Password not working (a different version)"
date: 2014-08-10
forum: General Help
---

### Post by Filipe_Garcia on 2014-08-10
Hello all!
I'm new to Ubuntu (not absolutely new to linux, but still a n00b), just have a fresh install of 14.04!

So, I've been noticing something... When I boot the OS into Desktop (Unity), the SUDO password does not work. Not in the command line, nor (for example) trying to install something from the Software Center. Basically, nothing that requires root password works. It gives me a message of wrong password.

After a while (still haven't been able to determine exactly how much, but let's say 10/15min), it works like nothing happened.


Anyone has any idea of what is happening? Any workaround?
I searched the forum (and Google), and the only things I could find are situations where the root password simply doesn't work, which is not my case after a few minutes. Am I missing something?


Thank you!

---

### Post by TheFu on 2014-08-10
There is no such thing as a "sudo password" - sudo uses the normal login password for the userid, provided that userid is in the appropriate group which is also in the sudoers configuration file.

So - **yes, you are missing something.**  None of my systems have a root password at all. sudo has been more than enough.

If you paste the output from the **id** command here, we can easily tell if sudo should even work for any specific ID.

---

### Post by Filipe_Garcia on 2014-08-10
Here's what's happening:

fgarci03@Garcia:~$ id
uid=1000(fgarci03) gid=1000(fgarci03) groups=1000(fgarci03),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
fgarci03@Garcia:~$ sudo nano a.txt
[sudo] password for fgarci03: 
Sorry, try again.


I tested now, and it took 10minutes untill sudo worked...
Thanks you for the clarification on these terms!

---

### Post by TheFu on 2014-08-10
Can you ping the machine by name? 
**ping Garcia**
Does that work?  Sudo cares that the machine name can be validated.  BTW, mixing case in the hostname is sometimes a bad idea because not every script will normalize the hostname.  Don't know if that's an issue here, just something to be aware.

[http://serverfault.com/questions/38114/why-does-sudo-command-take-long-to-execute](http://serverfault.com/questions/38114/why-does-sudo-command-take-long-to-execute)

---

