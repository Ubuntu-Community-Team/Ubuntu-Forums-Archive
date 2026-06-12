---
title: "hostname= connection, local ip=no connection!?"
date: 2007-09-10
forum: General Help
---

### Post by steve909 on 2007-09-10
Hello all,
I've had a problem come to light after installing Slimserver, a music streaming software and separate player.
I'd installed it (I'd actually had it working before) and went to the player to connect. All went as usual, selected wired connection, static ip, it recognised the server and the song titles and info all come up on the display.
But nothing will play. It then says it can't connect to the server.

I can get the software interface using [http://localhost:9000](http://localhost:9000) or [http://black(my](http://black(my) hostname):9000, but it won't come up using [http://my](http://my) local ip address:9000.

I've made sure the ethernet interface has entries for both 127.0.0.1 and local ip, the hostname is associated with the local ip address, all ports are open etc but can't find a way round this.

The player displays the song title but won't make a sound! If I try to play a track in the software interface, it gets to about 10secs and returns to the start of the song, no sound is heard.

Any suggestions, anyone. Slimserver site doesn't have any clues.. I've set this up several times before but just can't see what I've done wrong this time, or if this is known 'upgraded version' fault.

Steve

Solved. Seems the install of slimserver using synaptic doesn't install everything needed. Add 'deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main' to your repositories, then sudo apt-get update and sudo apt-get install slimserver as usual. Many unsigned packages are downloaded and you end up with the previous version of slimserver, but, at least it works now, using ip or hostname.
I suppose I'll wait for the 'new software available' icon to pop up for the version upgrade.

Steve

---

