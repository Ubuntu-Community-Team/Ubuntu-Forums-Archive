---
title: "Cannot proceed past login page."
date: 2014-07-03
forum: General Help
---

### Post by jason109 on 2014-07-03
I am running Ubuntu 12.04 x64 on my Lenovo Thinkpad W530. I have it dual-booted (the other partition being win8) running off of a Samsung SSD I purchased about 6 months ago. 

I installed Ubuntu along side Win8 when I first got the computer last year. It had run fine with minor issues up until yesterday. I had installed several programs on it when I first go it (krita, shutter, ccsm, etc.) just to kind of play around with Ubuntu and get familiar with it/experiment (I am by no means a programmer or person who is proficient in using, fixing, or developing linux software). 

A while ago I did an update or something (I cannot remember) and this update left a bunch of files on my desktop (about 30 or so). I had no idea what these files were or where they came from, but I could not delete them (I would get an error: permission denied). I inspected the files, and they all seemed to be negligible in size and the only thing they had in common was the icon (which had a little lock in the corner - I'm assuming this has something to do with permissions). 

I attempted to get rid of the files by becoming root and deleting them from my desktop. For some reason, I now cannot log into Ubuntu anymore (every time I enter my password, a black screen quickly flashes, then brings me back to the login screen). I researched this problem and have tried all of the different fixes that others have posted, but nothing has worked. One of the things I tried doing was using ctrl+alt+f1 to login manually, but this leaves me with a "fopen: permission denied" error.

 I believe I may have somehow accidentally damaged or altered the login profile files but I'm not sure (I don't think I deleted them because they were still there after I tried to delete them, but their icons changed and no longer had the lock symbol). 

Additional info: I was able to login to the guest account but that does me no good as I cannot access my main user account.

---

### Post by Dreamer Fithp Apprentice on 2014-07-03
> **jason109 said:**
> I attempted to get rid of the files by becoming root and deleting them from my desktop.A lot more detail there might improve your chances of getting a useful reply. EXACTLY what did you do? What did you see on your monitor? What did you type? What keys did you press? What buttons did you click? Not a summary, the exact steps. Did you in fact delete anything? And, if you "became root" (which can be done but isn't a normal procedure in 'buntus) do you know for certain if what you deleted, if in fact you did delete something, was in /home/YOUR-USER-NAME/Desktop as opposed to /root/Desktop? Do you know the names of the files? Don't know that I can help, but you'll have a better chance somebody can if you give more specific facts.

---

### Post by jason109 on 2014-07-03
[FONT=arial]I can't remember EXACTLY what caused the files to appear in the first place, but I believe it was the result of an update as I hadn't added any programs or applications in a long time. What I saw on my monitor was a desktop filled with icons (normally my desktop is blank, with no icons). To become root I went to terminal, typed in [/FONT]

sudo passwd root

[FONT=arial]and entered my password. From there I also attempted to use terminal to delete the files from my desktop (I am not entirely sure because this was a few days ago) but I believe I used a command to the effect of

rm /desktop

Note: this may not have been exactly what I typed, I am still new to linux.

I don't know if I deleted anything because as soon as I executed the command the desktop was shown, the icons of the files that I attempted to delete changed from having the lock symbol to not having it, and then I was kicked off of Ubuntu and my computer restarted. After restarting I entered my password and then the screen flashed black for about 1.5seconds. During this very short time period I noticed what looked like the usual "termination of processes" screen you see when restarting your computer from Ubuntu, but instead of restarting I was redirected back to the login screen, thus creating a loop where I cannot log in to my primary account. 

If something was in fact deleted, it was probably deleted from /root/desktop as I was signed into root on terminal, and I don't recall typing a specific directory other than what is stated above (there were many files, and I though that if I just tried to remove everything from the desktop that would get rid of them all).[/FONT]

After attempting to log in manually (by pressing ctrl+alt+f1) at the login screen, Ubuntu displays information (the date/time of the last time I tried to log in, and some other generic information). It then displays "fopen: permission denied" and leaves me with the option to begin entering code.

I honestly don't know anything more than this. I have looked on many different forums and found many other people who have posted the same/similar problem but none of the solutions have worked so far. If requested, I will show exactly what "fixes" I've tried so far, but since they haven't work I don't know if they are even relevant.

---

### Post by Dreamer Fithp Apprentice on 2014-07-11
Doesn't sound promising. If I were you, I'd boot from alternat media (such as a live disk) and poke around with a file manager like nautilus or thunar and see if I could find anything worth trying to change. I'm not hopeful about that. If you can't make it work that way, I'd copy any files you want to save to some other partition or drive and reinstall. Sorry I can't think of anything more specific.

---

### Post by sp40140 on 2014-07-11
Try this thread: [http://ubuntuforums.org/showthread.php?t=2233593&p=13070914#post13070914](http://ubuntuforums.org/showthread.php?t=2233593&p=13070914#post13070914)
I just posted there.

---

### Post by Dreamer Fithp Apprentice on 2014-07-13
+ 1 for that, sp40140! 
I have a system on another partition I had pretty much given up on. Only reason I hadn't installed something else over it was that I hadn't gotten around to it. Deadflower's trick fixed it.

Definitely worth a shot if you haven't already fixed your system or reinstalled, Jason109.

---

