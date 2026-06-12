---
title: "Help with setting up a FTP server"
date: 2008-05-19
forum: General Help
---

### Post by Me_Rock on 2008-05-19
Hey there,

I have a Call of Duty 4 server running on my Xubuntu machine. I need to set up a public FTP server so that players can download custom maps and mods faster than the server client would normally allow.

I have gotten FTP servers working before, but they all needed passwords and I couldn't figure out how to get it to point to the correct directory. In order for players to seamlessly download the required content, the FTP server needs to be public and needs to point to a directory with all the right files in it and preferably none of the wrong :P

Any help with this would be wonderful!

---

### Post by Monicker on 2008-05-19
Are you talking about an ftp server which allows anonymous users?  Are people going to be manually connecting to it, or is this a function of the game somehow?  I do not understand what you mean by "seamlessly".  Please give more details.

---

### Post by Me_Rock on 2008-05-19
When I say public I mean you can access it without a password or login name. You type in [ftp://xxx.xxx.xxx.xxx](ftp://xxx.xxx.xxx.xxx) and bam, you are there. You can't write to it as an average joe, you can only download from it. However, the owner can put files on it.

In the game server config file, I tell the server to allow clients to download custom content from an FTP server instead of from the game server's files.

This way, if a player wants to play on a mod or a custom map that they don't have, all they need to do is connect to the server that is running that mod or map and the game downloads it for them automatically during the connecting sequence. Otherwise, the player would have to exit the game and find the content themselves.

I hope that clears things up. Thanks for the response.

---

