---
title: "sending audio over network"
date: 2007-05-14
forum: General Help
---

### Post by duncan.hawthorne on 2007-05-14
hi, ive been looking around for something like this for a while, but probably due to my poor google searching ive found nothing.

i would like a vnc type solution but for sound, so that i can connect remotely to my desktop and whatever sound is playing on that computer i hear on the computer im currently working on. i know i could play files by just sharing the folders, or some mpd type solution (which im also actually confused how to do, any help?) but im interested in hearing exactly what would be outputted by the sound card.

can vnc do this, or is some new program required

---

### Post by mssever on 2007-05-14
> **duncan.hawthorne said:**
> hi, ive been looking around for something like this for a while, but probably due to my poor google searching ive found nothing.

i would like a vnc type solution but for sound, so that i can connect remotely to my desktop and whatever sound is playing on that computer i hear on the computer im currently working on. i know i could play files by just sharing the folders, or some mpd type solution (which im also actually confused how to do, any help?) but im interested in hearing exactly what would be outputted by the sound card.

can vnc do this, or is some new program required
I'm quite sure that VNC only interacts with the X server, not the sound server.

Check to see if you can connect to a remote sound server, or if you can forward a sound server's output. The fact that it's called a server suggests that it probably has some sort of networking capabilities. There might be software that can do this. Or, you might have to write your own. At the minimum, it's probably possible to replace the sound device with something that sends the sound over the network. But doing that would require some programming.

I've thought of doing that myself, but never seriously enough to do research. I'm interested if you find a solution though.

---

### Post by encompass on 2007-05-15
If this is a local netowrk... I used to do XDMCP for my connections... now that was cool... Playing dvd's on a computer that has only a cd-rom :P

---

### Post by tgalati4 on 2007-05-15
If you want to listen to files over the Internet, you can set up an mp3 server such as gnump3d.  You can password protect the directories.

Here's an example:

wingsoffaith.org/media.php

If you just need to share music on a local network, then use Banshee or Rhythmbox and set music sharing on in preferences.

One machine will have your main music directory, the other machines can then see the music share as long as the master machine is up and running either Banshee or Rhythmbox.  iTunes can also see these shares.  Unfortunately, iTunes 7 cannot share music with Linux boxes.  You have to go back to iTunes 6 to enable iTunes shares to be visible on Linux.

Another option is to put all of your music on a master machine in a specified directory using one of several music programs (Amarok, Banshee, Rhythmbox, Lsongs, etc).  Set up a Samba share for that directory.  You other machines should then detect this directory under Nautilus (File Manager) under Network.

Then you can import the music library on each external machine using the Samba share.  By default most of the programs will create a new track database, but won't copy the music files from a Samba share.

Samba requires some configuration to work properly.  There are several tutorials on the forums.

There are a few other options, like esound server (ess) for pushing sound to a remote machine the same way the xserver can push a display to a remote machine.

Good luck.

---

### Post by tehbeermang on 2007-05-17
> **tgalati4 said:**
>  Another option is to put all of your music on a master machine in a specified directory using one of several music programs (Amarok, Banshee, Rhythmbox, Lsongs, etc).  Set up a Samba share for that directory.  You other machines should then detect this directory under Nautilus (File Manager) under Network.

Then you can import the music library on each external machine using the Samba share.  By default most of the programs will create a new track database, but won't copy the music files from a Samba share.

Samba requires some configuration to work properly.  There are several tutorials on the forums.  Samba worked right out of the box with Feisty on my laptop. My music is on a shared drive on my desktop machine, running XP Home (one foot in the grave). 

Talking to the downstairs box over wireless was the first order of business. Playing music stored on it was a good test. I had some decent speakers hooked up and a worried look from my wife across the room.

"Oh great, I bet you want to build something now."

---

### Post by duncan.hawthorne on 2007-05-17
im already familier with sharing music via samba or similar ways (though thanks for writing up a nice comprehensive summary).

but i literally want to take the exact output of the sound card, so that when controlling through vnc or similar i get sound as well as video so its like im really at my computer. I could then do everything with this one method rather than needing different methods for each type of media.

imagine playing a simple game using vnc and hearing the sound as well or having a voip chat with someone whilst using vnc and hearing the voice (this would require output and imput so might be harder, but definitely to be able to hear them should be doable like vnc) or watching a video through vnc and getting the audio too, or set up a microphone remotely and listen to it through the network. all of these things wouldnt need individual programs if we could just forward the audio over the network, or watching internet  videos over the network from the familer surrounding of my desktop pc

---

### Post by mssever on 2007-05-17
> **duncan.hawthorne said:**
> im already familier with sharing music via samba or similar ways (though thanks for writing up a nice comprehensive summary).

but i literally want to take the exact output of the sound card, so that when controlling through vnc or similar i get sound as well as video so its like im really at my computer. I could then do everything with this one method rather than needing different methods for each type of media.

imagine playing a simple game using vnc and hearing the sound as well or having a voip chat with someone whilst using vnc and hearing the voice (this would require output and imput so might be harder, but definitely to be able to hear them should be doable like vnc) or watching a video through vnc and getting the audio too, or set up a microphone remotely and listen to it through the network. all of these things wouldnt need individual programs if we could just forward the audio over the network, or watching internet  videos over the network from the familer surrounding of my desktop pc

Have you tried Terminal Server Client? It looks like it has the ability to do what you want, though I haven't tried it.

---

### Post by Einheit on 2007-05-21
You can do this with NX server. You can get it here:

[http://nomachine.com/](http://nomachine.com/)

They supply deb packages that should work with Ubuntu. I have only used it myself with SuSE 10.0, but it does work great for that. Just follow the instructions on the Downloads page. While parts of it are non-free software, their license does allow for free (as in beer) personal use, and  they do contribute much of their code for the NX server to the FreeNX project (which unfortunately does not work quite so well yet).

---

