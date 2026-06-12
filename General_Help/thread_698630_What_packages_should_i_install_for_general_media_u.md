---
title: "What packages should i install for general media usage?"
date: 2008-02-16
forum: General Help
---

### Post by NoSmokingBandit on 2008-02-16
Im setting up a computer for my church but i wont have internet access once it is there, so i was wondering what packages i should install while i have it at home. Its really just going to be used for playing dvds, avi movies, mp3's and all that stuff, cd's, and maybe some powerpoint presentations. I know im going to need Open Office, but thats really as far as i got (im really terrible at this linux thing, lol). What should i put on the list?

---

### Post by foolsh on 2008-02-16
```
sudo apt-get install vlc* gstreamer*
```
should take care of most if not all video formats
plus you'll want to install flash from the adobe site.
the one in the repos is not work as far as I know.

---

### Post by Rocket2DMn on 2008-02-16
Have a look here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
install the restricted extras and visit some of the links at the bottom.  You will need libdvdcss2 for DVDs and w32codecs (or w64codecs if you use a 64 bit Ubuntu) from the Medibuntu repositories.

---

### Post by NoSmokingBandit on 2008-02-16
great, im about to get this computer up and running in a few minutes, thanks for the help.

Oh, btw, does VLC do full-screen? Im going to be using this with a projector and it would be nice to not have any panels or stuff on the screen.

---

