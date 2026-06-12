---
title: "Trouble opening .avi files in Kino"
date: 2007-05-15
forum: General Help
---

### Post by rainwalker on 2007-05-15
Okay, so Kino looks like exactly what I need to combine the two halves of a movie I have, but it's not loading the .avi files correctly. When I try to open them, it says:
> 
This is not a DV file. Do you want to import it?

and if I choose "OK" then it says
> 
The playlist is empty and the default preferences for video creation have not been specified - aborting.

with the only option being to click "OK", and it never opens anything.

Any Ideas?

EDIT: Looking through the tabs in the Preferences window, in the IEEE 1394 tab in says "The IEEE 1394 Subsystem is not responding. The raw1394 module must be loaded and you must have read and write access to /dev/raw1394." Is this important?

---

### Post by olafbooij on 2007-05-16
Hi,

The "and the default preferences for video creation have not been specified"-problem can be solved easily i guess.

Go to Edit->Preferences->Defaults and fill in the defaults (if this was not already done) (Europe: PAL, USA: NTSC, elsewhere: ?).

Greets,
Olaf

---

### Post by scott_g on 2007-05-16
Hi,

olafbooij's suggestion sounds good, but if it doesnt work:

Most avi files have some form of compression.  When Kino imports them, it first converts them to an uncompressed .avi file (huge; several gigs per 15 minutes).  So, do you have enough hard drive space/ writer permissions where the original file is stored?

It likely says:

> The IEEE 1394 Subsystem is not responding. The raw1394 module must be loaded and you must have read and write access to /dev/raw1394.

 Because you don't have a camcorder plugged into your computer over a firewire cable.

Thanks,
Scott

---

### Post by rainwalker on 2007-05-16
Oh my...
I probably have enough space, but that's going to be A BIG file.
It's two halves of a full length movie, a little over an hour each. Is there a way to keep the file from becoming that big or is it something that Kino does and can't be changed?

I'm at school right now so I'll try all this when I get home.

---

### Post by scott_g on 2007-05-16
True, it is big, but its only temporary; Kino re-compresses it as a .dv file when its done which is a more reasonable size (still going to be 10gb or more, only guessing, for the full movie), then you can export it as a DivX movie which will make it under 1gb.  

I seem to remember using a program on the Dynebolic livecd a while ago that split/joined two video files very quickly, (a matter of seconds), but I can't remember, or find, what it's called.  Avidemux might do it, but I'm not entirely sure.

Cinelerra is an excellent video editing tool as well (pretty well a premier equivalent), although it only outputs to a .dv file (which Kino likes), then you'd have to re-render it again.  So with that method, you'd have to render the video twice, but I think it'd work.  Cinelerra isn't in the repositories; its repository is:  

deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

(found on [http://cvs.cinelerra.org/getting_cinelerra.php)](http://cvs.cinelerra.org/getting_cinelerra.php)).

Hope it helps,
Scott

---

### Post by rainwalker on 2007-05-16
Yeah, I have Cinelerra too, but it takes SO long to save the whole thing after adding the two parts together.

Okay, so I set the default to NTSC but it still doesn't load the file. It asks me if I want to import it cause it's not a DV file, I choose OK, but then it says "Failed to load media file". Any ideas?

Also, I just installed some updates and in the update manager it says libquicktime0 can be updated but it's faded out so I can't select it. So I went into Synaptic and apparently it's a package I have installed that's upgradable, but with unmet dependencies. I'll put them in my next post...

---

### Post by rainwalker on 2007-05-16
> The following pakcages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
libquicktime0:
  Depends: libc6 (>=2.5) but 2.4-1ubuntu12.3 is to be installed
 Depends: libfaad0 (>=2.5) but it is not installable
  Depends: libpng12-0 (>=1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is to be installed


Any ideas? I have all of the repos enabled

---

### Post by scott_g on 2007-05-16
That libfaad0 looks like its a problem; but I'm not sure how to fix it...

Could you try going to the terminal, typing in kino to start the program, then try to import your movie, and see if there is anything strange in the terminal after the error message comes up?

Just an idea,
Scott

---

### Post by gsf747 on 2007-12-25
Just posting this in case others stumble across this thread.  Installing ffmpeg solved the avi import problem for me.  (In Debian, this means including debian-multimedia.org in the apt sources.)

---

