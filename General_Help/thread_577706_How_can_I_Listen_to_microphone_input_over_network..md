---
title: "How can I Listen to microphone input over network.  (From server to laptop)"
date: 2007-10-16
forum: General Help
---

### Post by caffeine_freak on 2007-10-16
I have a media server that I would like to put a microphone on and then listen to the audio jack mic input via the network.    

The server is in a spare room that my kids play in.   I can record a message like "come to dinner" play it via ssh session, via the mpg123 command like mp3 player,  and then listen to the response from my laptop.

I am running ubuntu 7.04 and the GUI is installed but I do not boot with it.  It is disabled on boot to save resources.

thanks

---

### Post by caffeine_freak on 2007-10-16
I don't have this working but am onto some interesting info.  I tried the commands at the end of my post but to no avail.  How this all fits together is a bit above my head and ability.  If anyone could help make sense of this it would be helptul.   for example how can i use xmms on the slave computer to run the audio that is streaming from the server.

And where exactly does one run the esd and where does one run edcat?

Okay after mucho digging I have found that esd from the esound package will do this, somehow.

This post had some interesting info. about esound and esd.

[http://ubuntuforums.org/archive/index.php/t-307813.html](http://ubuntuforums.org/archive/index.php/t-307813.html)

But I also need the client utilities which I don't think are in a package so I built them.

The source is available from here
[http://www.linuxfromscratch.org/blfs/view/svn/multimedia/esound.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/esound.html)

I also found some good info about actual commands to get this running.  Here is the link.

[http://julien.danjou.info/blog/index.php/post/2006/12/30/374-how-to-turn-your-flat-into-a-night-club](http://julien.danjou.info/blog/index.php/post/2006/12/30/374-how-to-turn-your-flat-into-a-night-club)

Quote from above link
"How to turn your flat into a night club

Par jd le samedi, décembre 30 2006, 15:17 - Zik - Lien permanent

    * fun
    * life
    * music
    * software

Today I had to clean up my flat, but I was lazy. I decided that some music will be welcomed. However, even if my flat is not so big, I have three rooms and if I play music in one of them, I can't hear it everywhere. By chance, there's a computer connected to speakers in each.

So, to listen your playlist on every computer, do like me: just install esound on each computer and run esd -tcp -public (esd without option is sufficient for your master). On your master, run also esdmon | esdcat -s slave1 and esdmon | esdcat -s slave2, and so on. This will listen to you local esd and pipe the sound to your slaves via network.

Then grab your favorite audio player which should be esd-capable (my xmms is), and play files to your local esound daemon. Listen... it plays everywhere!

Next step is to invite me, some friends and hot chicks to your party."

---

