---
title: "mpd (Music Player Daemon) angst..."
date: 2005-04-20
forum: General Help
---

### Post by rick_hewes on 2005-04-20
Hello,

I have installed mpd. (Music Player Daemon)

Executed dpkg-reconfigure mpd. 
Exectuted /etc/init.d/mpd start-create-db

The DB is created. All is well. (after a few changes with the DB location)

The problem is when I come to use gmpc. It fails to play and from the mpd.error;

"Problems opening audio device" ...

If i run mpd as the user I log in with its all works hunky dory. So I guess it is a permissions thing to access the audio device. 

Does anybody know how to overcome this problem ??

Thanks,

Rick.

---

### Post by secstate on 2005-10-16
*bump*

I'm having this problem too.  Worst thing is, I just upgraded to Breezy and this never happend to under Hoary.

---

### Post by wixtech on 2005-10-17
I had the same problem and found the fix here: [http://ubuntuforums.org/showthread.php?t=31763](http://ubuntuforums.org/showthread.php?t=31763)

It appears that our problem is that mpd is not usingthe ALSA device for sound output.  Basically, I needed to edit the mpd.conf file to include the following line: ao_driver "alsa09" (sudo nano /etc/mpd.conf, then add 'ao_driver "alsa09" as the last line of the file and save the file).

Then, just restart mpd (sudo /etc/init.d/mpd restart) and you should be good to go.  Good luck and good listening!  By the way, the gmpc client for mpd is quite nice!

Regards,

Wixtech

---

