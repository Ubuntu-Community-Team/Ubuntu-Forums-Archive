---
title: "Opening (media) files in windows-network"
date: 2004-11-14
forum: General Help
---

### Post by rookie on 2004-11-14
Hello,

I'm completly new to Linux and Ubuntu, so please forgive me if I ask some newbie questions...

i have the following problem:

I have a Ubuntu-PC and 2 Windows xp PC's. The xp Pc's are my file servers, where I store mp3's, videos,pictures, ebooks etc. 
I can access those network-drives via Computer/Network/Windowsnetwork etc. and I even managed to create shortcuts on the desktop to access the network-drives.

However, I can't open the files stored on those drives, no matter if I use totem player, vlc player or xmms for audio/video files or if I try to open a pdf with xpdf. Nothing happens.

I can, however, listen to audio files and watch videos from the network when I use mplayer. This leads me to the assumption that the problem has nothing to to with access-rights. 

The problem with mplayer is that it is invisible: I rightclick on a medialfile and choose 'open with mplayer'. In hear the music, but I don't see the player which makes it impossible to adjust volume or use fast-forward etc.

I'd appreciate any help, thanks a lot!

---

### Post by Magneto on 2004-11-14
try gmplayer 
you might have to install gmplayer
mplayer is a commandline program and to run it with a gui u need gmplayer

the problem isnt permissions its whether or not the applications you are using were configured with Samba support- samba is the opensource networking program that allows you to interact with windows networking

---

### Post by Razvan on 2004-11-14
[QUOTE=Magneto]try gmplayer 
you might have to install gmplayer
mplayer is a commandline program and to run it with a gui u need gmplayer

the problem isnt permissions its whether or not the applications you are using were configured with Samba support- samba is the opensource networking program that allows you to interact with windows networking[/QUOTE]
 you should try gmplayer! mplayer really is only the box thet plays the file...no volume adjustment or anything :-)

gmplayer is a graphical user interface (GUI) for mplayer that allows you to openfiles from inside mplayer and so on.

---

### Post by TravisNewman on 2004-11-14
Also, be sure you've installed w32codecs from the Marillat repo

See the Multimedia Howto in the howto section to get all the necessary info

---

### Post by rookie on 2004-11-14
Thanks for your replies

I tried to install gmplayer with sudo get-apt install gmplayer, but it didn't work.
I then tried to follow exactly the way that is mentioned in the how to/mulitmedia thread, but after some time I only get error messages nand I'm unable to complete the procedure.

Is everything concerning Linux so difficult and time-consuming? I mean all I want to do is instalingl an Audio player...

---

### Post by TravisNewman on 2004-11-14
[QUOTE=rookie]Thanks for your replies

I tried to install gmplayer with sudo get-apt install gmplayer, but it didn't work.
I then tried to follow exactly the way that is mentioned in the how to/mulitmedia thread, but after some time I only get error messages nand I'm unable to complete the procedure.

Is everything concerning Linux so difficult and time-consuming? I mean all I want to do is instalingl an Audio player...[/QUOTE]
 You don't need to compile anything really, just enable the universe repo, and enable the Marillat repo, then you can install w32codecs and gmplayer without compiling, etc. I meant to see that MM Howto just for how to do those 2 things really

---

