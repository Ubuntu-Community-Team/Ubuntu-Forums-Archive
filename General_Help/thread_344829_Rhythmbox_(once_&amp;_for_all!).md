---
title: "Rhythmbox (once &amp; for all!)"
date: 2007-01-23
forum: General Help
---

### Post by dothedorky on 2007-01-23
I've been getting quite comfy in my LTS ubuntu, but have avoided uploading or making a music library because of past experiences. 

I've got all the music i'd like to load on a double layer dvd+r. (i also have a dvd player).

I tried to take the music from this dvd (mp3's) over to rhythmbox a while ago, with no luck. Either the songs wouldn't play at all, or they'd be uploaded for as long as i keep rhythmbox open, if i closed it and reopened it, my library wasn't there.

Any suggestions?

---

### Post by djf_jeff on 2007-01-23
First, for the mp3 to play, you must install the right codec : 

apt-get install gstreamer0.10-plugins-ugly

Second, rhythmbox is a little picky with a library. If you reopen rhythmbox when the file is not accessible, rhythmbox remove them from the library. So, you must make sure that your files is always available.

---

### Post by dothedorky on 2007-01-25
by 'having files always available' do you mean i have to keep the dvd disk in the drive just so it continually reads the music files? if that's the case, i must say that's sad.

i need to find a way to convert .mp3s to whatever music extension ubuntu uses (im assuming .ogg) and get them to stay permanently in the library. 

i've downloaded those extensions, music won't play, and music won't save. 

back to square one?

---

