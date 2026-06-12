---
title: "Smplayer 22.7.0 won't play dvd"
date: 2023-03-07
forum: General Help
---

### Post by lou6 on 2023-03-07
I installed the latest version of smplayer today but it won't play a dvd.  Tried both mpv and mplayer as multimedia engine with no success.  My system is Xubuntu 22.04 and the default player (parole) works fine as does vlc.  I've been an smplayer user for many years and hate to give it up. Any help appreciated - TIA

---

### Post by Qew on 2023-03-07
Maybe install libdvd-pkg, which will download and compile the necessary packages to play DVDs.

1 - Ensure that Multiverse repository is enabled.

2 - In a console run: sudo apt install libdvd-pkg

3 - sudo dpkg-reconfigure libdvd-pkg

4 - Enjoy your DVDs.

For further help, this thread will help (more detailed than my post): [https://askubuntu.com/questions/1294860/vlc-not-playing-dvd-and-cant-install-libdvd-pkg-in-20-10](https://askubuntu.com/questions/1294860/vlc-not-playing-dvd-and-cant-install-libdvd-pkg-in-20-10)

---

### Post by lou6 on 2023-03-07
Thanks for responding - I did all the things you suggested earlier today with no joy.  Prior to that, I could not play dvds at all - now parole (the xubuntu default) and vlc will play dvds but smplayer will not.  Of course I can simply let parole do the job but I hate to give up on good old smplayer...

---

### Post by lou6 on 2023-03-08
Finally solved this (for Xubuntu 22.04).  In Removable Drives and Media Video DVD's I entered  "smplayer dvd://" (without quotation marks)
Now smplayer plays dvds automatically.  I imagine the same solution would work for audio cds...

I'll mark this closed.

---

