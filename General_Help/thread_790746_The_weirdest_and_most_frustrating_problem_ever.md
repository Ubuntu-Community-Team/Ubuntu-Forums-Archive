---
title: "The weirdest and most frustrating problem ever"
date: 2008-05-11
forum: General Help
---

### Post by Rhapsody on 2008-05-11
This is a problem that simply defies any sort of explanation. No matter where it is, no matter what I do, I cannot launch any file by the name of 'firefox-bin' anywhere in /home. Konsole will simply claim it doesn't exist. I can try launching it through the firefox startup script ("firefox2/firefox/run-mozilla.sh: 424: firefox2/firefox/firefox-bin: not found"), I can try launching it directly ("bash: firefox2/firefox/firefox-bin: No such file or directory"), I can prove it exists by dragging and dropping it from Konqueror into Konsole (same error as the last one).

I can run Firefox through the repositories, but not from /home for some reason and it's left me very frustrated as to why. It doesn't even matter if it's a different 'firefox-bin' (I have one for Firefox 2 and one for Firefox 3, which generate exactly the same error). Why can't Kubuntu see this file in particular?

---

### Post by dreadlord_chris on 2008-05-11
```

whereis firefox-bin

```

Must admit to being a little confused though - why are you trying to run Firefox that way (firefox-bin)? The Firefox executable on my Kubunutu system is just called firefox. Have you tried just **firefox** without the **.bin**?

---

### Post by p_quarles on 2008-05-11
I am assuming that this "firefox-bin" program is the Linux copy of Firefox that is downloadable from Mozilla's site. There is really no reason to run this program, but you can if you want, obviously.

Anyway, the reason you can't launch it the way you are trying to is because the program is not in your executable path. This means that you need to type out the full path to get it to run. E.g.:
```
~/firefox/firefox-bin
```
You can also modify your .bashrc (or the rc file for whichever shell you use) to make a custom executable directory for your user. 

Again, there is no reason not to use the Firefox that comes with Ubuntu.

---

### Post by Rhapsody on 2008-05-12
Thanks for the help, but Kubuntu is still just as determined that there is no such file.

The very first thing I did was to launch it by simply using the 'firefox' script, but that just exits with an error ("/home/rhapsody/firefox2/firefox/run-mozilla.sh: 424: /home/rhapsody/firefox2/firefox/firefox-bin: not found") and trying to run 'firefox-bin' directly confirms that ("bash: /home/rhapsody/firefox2/firefox/firefox-bin: No such file or directory"). 'whereis firefox-bin' generates "firefox-bin:", while '~/firefox2/firefox/firefox-bin' generates "bash: /home/rhapsody/firefox2/firefox/firefox-bin: No such file or directory". Just to confirm, an ls in /home/rhapsody/firefox2/firefox lists a file called 'firefox-bin' as one of the results.

Why is Kubuntu so determined that firefox-bin doesn't exist?

---

### Post by jatos on 2008-05-12
Check the following thing is the file:

1. the permissions (Should either be, 700, 750 or 755)
2. the file ownership

Then try going into konsole, going to the firefox-bin directory and typing './firefox-bin' and see if it still comes with the error - make darn sure you got the ./ though.

---

### Post by bingoUV on 2008-05-12
One reason I can think of for ls showing a file, and trying to execute giving "file not found" error is that the file is a symbolic link to nowhere. Instead of doing ls, do 
```

ls -l

```
If it were lack of execute permission on firefox-bin, it would say "permission denied". If it were lack of read perm on the containing directory, ls itself would be unable to show the file.

---

### Post by chandra on 2008-05-12
Try

locate firefox-bin

and see what you get.

---

### Post by chandra on 2008-05-12
Oops! That should have been

```
locate firefox-bin
```

---

### Post by Rhapsody on 2008-05-12
Well I gave up, deleted both Firefox folders, then re-extracted them to test further suggestions. That seemed to satisfy Kubuntu, as things immediately started working. I don't think I'll ever know why Kubuntu was doing what it was doing.

---

