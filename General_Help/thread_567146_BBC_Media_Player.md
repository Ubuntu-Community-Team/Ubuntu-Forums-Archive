---
title: "BBC Media Player"
date: 2007-10-04
forum: General Help
---

### Post by gandalf355 on 2007-10-04
Hi,

When loading up the BBC player, it says I require Real Player 10.5 which it says isn't available, requiring a manual installation which then doesn't work.

Is there another application that the BBC player is compatible with?

Cheers.

---

### Post by gandalf355 on 2007-10-04
Forget I ever asked...I dug a little deeper and found the answer to my problem...making it blatantly obvious I'm a newbie!

---

### Post by gandalf355 on 2007-10-04
Ok next problem...

I've downloaded the .bin file to my desktop but when i try to run it it comes up with the following error message:
[B]
Cannot open /home/chris/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.[/B]

Any ideas as to what my next move is?!

Thanks!

---

### Post by lincolnlad on 2007-10-04
I'd get realplay from Canonical's commercial repository:

Instructions here:

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

That will install a .deb which your package manager will keep upto date.

The BBC website also uses Windows Media, so you can play that through the firefox totem plugin with the codecs installed.

For more info see this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins)

---

### Post by Bablefish on 2007-10-04
To nstall Realplayer 10 use this terminal command

sudo apt-get install realplayer

---

