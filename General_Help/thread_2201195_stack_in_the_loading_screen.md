---
title: "stack in the loading screen"
date: 2014-01-23
forum: General Help
---

### Post by erelon on 2014-01-23
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]                I'm using an old thinkpad computer (Z-260). last month my  windows died and i could not be botherd to fix it (blue dead screen), so  i installed ubuntu.

  Yestaday i have decided do extend the ubuntu partition because i didn't have enough space to install packeges.
  Gparted said that there is a problem with the windows partition and  that i need to run a CHKDSK. So, i loaded a live USB with windows SP3  instalation and run it on the windows partition. The windows still didnt  work, but using live USB with ubuntu(the same one), the Gparted did  work and extended my ubuntu on the free space in the broken windows.
  Then my booting was resetted to the windows boot (and did not work), so i used the live USB of ubuntu to use boot-repare.
  After that, i got the booting window of ubuntu- and run it, the ubuntu worked.
  Today- i tried to open the ubuntu again (i got the right booting  menu), but it loaded and loaded and didnt open, when i tried to move my  mouse, my pointer was in a shape of X.

  I tried the boot-repare again, and again with changing the proparties  of it- but nothing. It hit me that the booting is not the problem.
  What shuold i do?

      

[/TD]
[/TR]
[/TABLE]

---

### Post by Dreamer Fithp Apprentice on 2014-01-23
What I would do depends on if you have important data on the system partition, if you'd put a lot of time into tweaking it, and if the system was backed up, if the user data (meaning your stuff that's not part of the working software - like ebooks, pictures, movies, music, documents, etc.) was on the same partition or a seperate one and if it is backed up.

If your user data is on another partition and also backed up, or alternately if you don't yet have anything on the system of any importance, so that you don't mind risking it, I'd try running fsck. Because it is easier, first I'd try running it from the hard drive. When it gets to the point where it hangs try holding down the ctrl and the alt key and pressing the F1 function key. If that gets you a white text on black borderless screen with something about the version and finally something like "login:" you can do it from there. Type in your user name and press enter. It will ask for your password. Type it in and press enter. If it gives you "login incorrect" and another prompt keep trying the same procedure until it gives you "Last login:" and some time, followed by a normal prompt like "username@computername:~$". Sometimes this can be difficult. I think that is because wireless keyboards sometimes don't work quite as well until their drivers are loaded and it hasn't happened yet. Or maybe it's just my imagination fueled by the fact I'm typing blind while entering the password, with no visual or other feedback to show whether a keystroke registered as one stoke, more than 1 stroke, or not at all. (My kingdom for a good clicky wireless keyboard! You don't wan't my kingdom? How about 37 cats?) Anyway, type carefully, with clean short, sharp, firm strokes, trying several times if need be, until you get a prompt. Then type in```
sudo fsck
```and press the [enter] key. Let it do its thing. I don't have to do that often enough that I can remember for sure how it ends. I think it reboots automatically when it's through, but maybe it returns a prompt. If it does, type in```
sudo shutdown -r now
```and press the [enter] key. The system should reboot and the problem may be fixed.

If what I described are NOT the circumstances, additional precautions may need to be taken before you try this because there is a small risk fsck might make things worse, not a big risk, but some. Exactly what, depends on the circumstances. Post back and tell us about in that case before doing anything risky.

---

### Post by erelon on 2014-01-24
thank you for your anser.
i checked in th web for more ansers- and got none.
(Im not a linux 100% noob, but thanks for the step by step anser...)
anyway, i serrended to my computer and because i didn have data on it, i just formated it and reinstalled ubuntu.

thank you!

---

### Post by Bucky Ball on 2014-01-24
Is everything now working? If so, could you please mark the thread as solved to help others by following the instructions in my signature. Thanks. ;)

---

