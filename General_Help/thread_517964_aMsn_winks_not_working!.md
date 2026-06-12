---
title: "aMsn winks not working!"
date: 2007-08-05
forum: General Help
---

### Post by UK-Wobbie on 2007-08-05
Hey all i got aMsn 0.97RC1 installed on my Ubuntu 7.40...
I have loaded the winks plugging and added the flash link in to the configure box! But it still do not work when someone sends me a wink or if i give them a wink... I do not no what i am not doing right :(

If it is the flash link i am not putting in right or is it not the right flash file! Do anyway no how to link the  flash to the configure box lol Am to dumb to no how? :)

Thanks for your help 
Rob

---

### Post by Claus7 on 2008-03-04
Hello,

I have recently installed amsn 0.98b from scratch in my system. So now I'm figuring out what is going on with other things apart from the installation. In order for the winks to play go to synaptic and install cabextract. Then go there :
 [http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)
in order to download flash player. Then according to this :
[http://www.amsn-project.net/forums/viewtopic.php?t=2366&postdays=0&postorder=asc&start=135](http://www.amsn-project.net/forums/viewtopic.php?t=2366&postdays=0&postorder=asc&start=135)
extract flashplayer and copy the file as root to /usr/bin .

Now your winks options should look like this:

CabExtract command : cabextract
[ ] Use extract32 ...  (don't choose that option, leave that box empty or you won't be able to see or add winks)
Swf player command : flashplayer
Swf player arguments : 

In Swf player command you can use also firefox after you have installed flash player, yet this worked for me only once. Just FYI.

Save and I hope that everything will be ok.

Regards!

---

