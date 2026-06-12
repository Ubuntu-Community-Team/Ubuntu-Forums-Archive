---
title: "How do I uninstall mplayer"
date: 2005-04-22
forum: General Help
---

### Post by NiceGuy on 2005-04-22
Hi, first off I'm a real noob to Ubuntu and linux in general (in fact I only installed it on thursday) so you'll have to bare with me... 

I installed mplayer following the instructions I found here: [http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

That went ok but when I tried to play a movie file it had no sound and gave an error message. I googled and found out that there was a conflict with the esd audio driver. I also found out that the way to get around this problem that was to incorporate the esd driver into mplayer, but how I don't know how to.

I then read that you could get a version of mplayer specifically for Ubuntu but couldn't find how to get it other than downloading a .deb file and then using the "dpkg --install file.deb" command.

However I've read that this isn't the 'correct' way to install applications and can cause 'problems' and besides I think it'd be prudent to uninstall the mplayer version I've already got before I install this one.

The only problem is I don't know how to uninstall mplayer!  ](*,) 


Any help would be great!

---

### Post by ejohney on 2005-04-22
probably the easiest way is to just type "sudo apt-get remove mplayer".  or you can find it in synaptic and remove it from there.

---

### Post by NiceGuy on 2005-04-23
Unfortunately I've tried that and I get the message: 'E: Couldn't find package mplayer'

- any other suggestion?

---

### Post by lorap on 2005-04-23
hi friend!
do the next and you'll meet no problems watching any movie or listening to any music:
1.System-->Administration-->Synaptic Package Manager
2.Settings-->Repositories
once you've the repositories window open mark all checkboxes possible regardless any warnings then press Settings button and mark all checkboxes again except Download Upgradable Packages.then press Ok button.some download process'll begin and once it completes press Reload button.that'll rebuild your package databse again.then press Search button and write in VLC then press Ok button.
once you've it picked up mark it for install and press Apply button :-)
that's all:-)
have a nice day friend!
pavel

p.s.:
well,don't forget to press ctrl+alt+backspace to reload grafic kernel.

---

### Post by NiceGuy on 2005-04-23
Thats sounds like a plan but with two provisos:

1. I still want to uninstall mplayer if I can (or is this not nessessary?)

and

2. I'll need to make some more space on my HD, which is a bit full at the moment. 

Just out of interest how much space will doing this take up?

---

### Post by lorap on 2005-04-23
hi.
it doesn't take much space at all,i mean vlc player.
all operations i've mentioned earlier were about to make you able download all software possible.
to uninstall software you've installed but nomore need just press the Search button,write the player's name then Ok.after the synaptic picks it up to you mark it for complete uninstall,then press Apply button :-)
vlc doesn't need any codec been installed,everything's sawed inside it.
have a nice day!
pavel

---

### Post by Ufo on 2005-04-23
Hi

 I have same kind of situation going on.
I installed mplayer from source sometime when I installed warty. I think I used these instructions:

[http://www.ubuntuforums.org/showthread.php?t=94&highlight=mplayer](http://www.ubuntuforums.org/showthread.php?t=94&highlight=mplayer)

instructions look similar to one you used.

Now I would like to uninstall it before upgrading to hoary and then install only pakages from Ubuntu repositorys.

I have found instructions to uninstall it running

make uninstall

in directory where source is and where you have run

make install

when installing mplayer. Unfortunately I have removed source and that directory sometime. So now I think I will try to go thru the installation procedure again and do "make uninstall" and to remove everything else that has been installed in those instructions too.

---

### Post by Turin Turambar on 2005-04-23
[QUOTE=Ufo]Hi when installing mplayer. Unfortunately I have removed source and that directory sometime. So now I think I will try to go thru the installation procedure again and do "make uninstall" and to remove everything else that has been installed in those instructions too.[/QUOTE]

I guess you can also remove it by doing a "mplayer" search and then delete all mplayer-related files/dirs. I had the same problem as you and this fixed it.

---

### Post by Ufo on 2005-04-23
Yes, it seemed that after " sudo make uninstall" it removed some staff.
But when running

sudo find / -name mplay*

there where still mplayer related directories and files, so maybe this "make uninstall" procedure was useless.

Well, anyway now it should be gone for good.

I hope NiceGuy also got this solved  :grin:

---

### Post by fordfan753 on 2005-04-23
Your sound problem may not be ESD related...you may just need the W32Codecs package, available from the marriat repositories. Add these to /etc/apt/sources.list then reinstall mplayer.

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

If you really do want to get rid of mplayer and you installed the .deb packages using #apt-get install mplayer
then just make sure you have the "multiverse repositories enabled in /etc/apt/sources.list you may have to add them in if you dont already have them, but its not too hard to find how to do that on the wiki. Then try
#apt-get remove mplayer
this will only work if you have the multiverse repositories enabled.

However if you built it from source and you DONT have the extracted folder try installing mplayer from the multiverse repositories, this should write over the data installed by the source, then remove using the above command, this should fully remove mplayer.

---

### Post by NiceGuy on 2005-04-23
Thanks to everyone!!!!!!  :grin:  :grin:  :grin:  :grin:  :grin:  :grin: 

I managed to uninstall it (which required reinstalling it first :roll: ) and then I downloaded VLC (as lorap sugested - thanks  :grin: ) and now I can play pretty much anything!!!

Really Chuffed!

Thanks again!!

---

