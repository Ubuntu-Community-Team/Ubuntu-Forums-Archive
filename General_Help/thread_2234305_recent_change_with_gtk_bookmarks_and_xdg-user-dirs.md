---
title: "recent change with gtk bookmarks and xdg-user-dirs"
date: 2014-07-13
forum: General Help
---

### Post by scott092707 on 2014-07-13
I have been trying for a while to find out why Nemo and PCManFM do not show my xdg-user-dirs places in their sidebars.  I swear that they used to, but now (14.04) they did not.

["Why do you not just store them as bookmarks?", I have been asked...
Well, since I went to the effort to have xdg-user-dirs point at my private partition personal data, I feel I should not have to do the same thing *again* in *each* File Manager and any other program that accesses standard places.]

I say "did" (earlier) because...

Wonder of wonders!
  On July 6(?), I booted my machine to find that both PCManFM and Nemo  had my xdg-userdirs directories as bookmarks - and that the  ~/.config/gtk-3.0/bookmarks file which now contained the directories  that xdg-userdirs re-defined, was being used by each one (this was NOT  the case the previous day).
I DID NOT SET THIS UP!  I had been testing each one and both bookmarks  files (the other being ~/.gtk-bookmarks) the prev. day, and when I shut down, each File Manager was using a  different bookmarks file, and PCManFM when first brought up actually  showed the last bookmark that I had been testing, although it  disappeared shortly thereafter, since it was not in the  ~/.config/gtk-3.0/bookmarks file it was now using.


  I sorted the /var/cache/apt/archives directory by date, but found nothing recent for either PCManFM or Nemo.
There WAS a new Linux kernal (3.13.0-30-) the day (or two) before, however...
  What could have changed in Linux that would make both FMs suddenly  decide to llist my xdg-userdirs directories, and what created/modified  the ~/.config/gtk-3.0/bookmarks file to use the xdg-userdirs info?
I checked each of the following days, and each day, the  ~/.config/gtk-3.0/bookmarks file  date was now the current day at boot  time.  This was not happening before.
I tried in two different Linux forums (fora?) to ask what might have changed, but received no answering comments.

Could something in some other [L]ubuntu package recently installed have changed things?
(I usually look at the list of packages that the update-notifier suggests, to see what is there and what has changed, but nothing appeared to be anything that would change bookmarks or was xdg-user-dirs - related, but I could easily have missed something...)

Any insight you could give would be appreciated.

-Scott

-----------------------------------------
scott@scott-AsusM2N68-AM-Plus:~$ uname -a
Linux scott-AsusM2N68-AM-Plus 3.13.0-30-generic-tuxonice #54~ppa1-Ubuntu SMP Sat Jun 28 10:36:21 UTC 2014 i686 athlon i686 GNU/Linux

sscott@scott-AsusM2N68-AM-Plus:~$ lsb_release -dsc
Ubuntu 14.04 LTS
trusty

scott@scott-AsusM2N68-AM-Plus:~$ echo $DESKTOP_SESSION
Lubuntu

[Yes, it is a non-standard Linux kernal - but tuxonice confines itself to that which concerns power management, as it is supposed to help to hibernate, so it *should* not have any bookmarks/xdg-related idiosynchrasies]

---

### Post by vasa1 on 2014-07-13
Also here: [http://ubuntuforums.org/showthread.php?t=2232752](http://ubuntuforums.org/showthread.php?t=2232752)

---

