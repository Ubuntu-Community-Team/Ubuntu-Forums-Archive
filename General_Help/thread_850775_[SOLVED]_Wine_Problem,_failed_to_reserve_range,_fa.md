---
title: "[SOLVED] Wine Problem, failed to reserve range, failed to install I think...."
date: 2008-07-05
forum: General Help
---

### Post by vandorjw on 2008-07-05
I am trying to run Command & Conquer Renegade using wine.
however I get error message.

Also, I notice that when ever I install something using apt-get,
everything gets deferred to libc6 or something like that.:confused:

> 
[email]ubuntu@ubuntu-desktop:~/.wine[/email]/drive_c/Westwood/Renegade$ wine game.exe
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/ubuntu/.wine/drive_c/Westwood/Renegade', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\game.exe": Module not found
[email]ubuntu@ubuntu-desktop:~/.wine[/email]/drive_c/Westwood/Renegade$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
[email]ubuntu@ubuntu-desktop:~/.wine[/email]/drive_c/Westwood/Renegade$ 

--------------------
Renegade doesn't start.. even though it works on my laptop.

I did a clean install of x-ubuntu.
then, "sudo apt-get install gnome-core"
then "sudo apt-get install wine"

gnome-core was also defered to libc6 but seems to work fine
Wine, however, is soo crappy it cannot even run notepad.
(sudo apt-get remove wine, then re-installed. same problem)

PS; I still have kernel (insert many numbers here).16
not (insert many numbers).19


Please help me fix wine, or it is back to win XP for me.
(Renegade is that important... :))

---

### Post by plucky on 2008-07-06
> preloader: Warning: failed to reserve range 00000000-60000000


I had this error and used this link to fix the error [Page Zero Problem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Not sure if yours is related.

There is a [**Wine**](http://ubuntuforums.org/forumdisplay.php?f=313) sub-forum where you would probably get more help.


Good Luck

---

### Post by vandorjw on 2008-07-08
Thank you, that link solved my problem.

However, I went back to Ubuntu 7.04 since there was a bit to many bugs in 8.04 for my liking.

Cheers - CC7

---

