---
title: "Trying to view a webcast - need Opera or Firefox help"
date: 2005-05-05
forum: General Help
---

### Post by maruchan on 2005-05-05
Hi, I'm trying to view video content on the web like:

[http://www.pbs.org/wgbh/pages/frontline/shows/persuaders/view/](http://www.pbs.org/wgbh/pages/frontline/shows/persuaders/view/)

or the Quicktime.com movie trailers.

Unfortunately I'm not able to view this stuff in either Firefox or Opera. I prefer Opera, though. Does anyone have suggestions on how to make it work? I have these packages:

w32codecs
helix player
kaffeine
totem

...and none of them kick in when I need it most :) 

I tried to install Realplayer from Synaptic but it said:

> realplayer:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

Thanks for any help.

---

### Post by dave9191 on 2005-05-05
Download RealPlayer from their site and install it. 

[http://forms.real.com/real/player/blackjack.html?&src=uk-r1e_entitlements](http://forms.real.com/real/player/blackjack.html?&src=uk-r1e_entitlements)

You can get the RPM and get 'alien' to convert it to .deb. Or just download their bin file. I did that on warty and it worked fine. Then you need to add the plugin to firefox and opera and youre sorted :)

---

### Post by Xian on 2005-05-05
Install RealPlayer as mentioned above (I used the bin file). The quote below is from the Helix Community website and it meshes with my experience. Those video streams from the PBS link you provided will play just fine using RealPlayer in Opera.

[i]"There are two players that are build from open source code that were released at the same time. One it the HelixPlayer, that can't play real datatypes, and the other is a Real branded player that can play real datatypes. The reason for the HelixPlayer is that it can be redistributed without any problems.

People on the player team can give you a better answer, but I think you just want to install the realplay version of what you downloaded, not the helixplay version. Again, both are free and can be built from open source."[/i]

---

### Post by maruchan on 2005-05-05
It doesn't seem to be working...is there a way to uninstall if I installed via the .bin file? I'd like to try it again. It asked me where to install to and I just set it to the default, which is inside my home dir in a downloads folder (better locations?).

Although, the main problem seems to be that the player just sits there and says (for example) "contacting pbs.org..." and never does anything. Turned the firewall off, same results. Tried lo-band version, same thing. And this is in Firefox. Opera's plugin doesn't work at all - something about "not allowing scripted plugins". 

BTW I believe the best link is [www.real.com/linux](www.real.com/linux), which is where I ended up after installing RealPlayer 8 and then thinking, "hey, what is this?"

Also, what are you guys using for Quicktimes?

Thanks.

---

### Post by Xian on 2005-05-05
[QUOTE=maruchan]And this is in Firefox. Opera's plugin doesn't work at all - something about "not allowing scripted plugins". [/QUOTE]
This must just be a config problem in Opera since I've also got my realplayer directory in the /home path. It is playing those videos like a charm at your PBS link. Have you correctly set your file types?

You need to open your Preferences Menu and configure all applicable media types to the realplay executable file. For example, here is one for the .ra file extension.

[img]http://img.photobucket.com/albums/v469/camplear/forums/operareal.jpg[/img]

---

### Post by maruchan on 2005-05-05
Yay! You were right. :D

Your screenshot shows "ra" type files, and I noticed the errors I got were mentioning "rm", so I changed your "ra" to "rm,ra" and entered the path to the one in my home directory. Now everything works peachy!

Thanks for the help.

As for quicktime movies, I guess it's Crossover or nothing?

---

### Post by Xian on 2005-05-05
[QUOTE=maruchan]As for quicktime movies, I guess it's Crossover or nothing?[/QUOTE]
You can use [MultiShow](http://www.randelshofer.ch/multishow/download.html) to play QT movies and it does a great job, but I don't think it currently supports browser integration.

---

### Post by rwabel on 2005-05-08
[QUOTE=Xian]You can use [MultiShow]("http://www.randelshofer.ch/multishow/download.html") to play QT movies and it does a great job, but I don't think it currently supports browser integration.[/QUOTE]

Isn't JMF needed for MultiShow? How did you install JMF?

---

### Post by Xian on 2005-05-08
[QUOTE=rwabel]Isn't JMF needed for MultiShow? [/QUOTE]
I just installed the package straight off the website link I provided. It has a nice GUI installer that didn't complain about any needed pkgs, and then immediately I was able to play those QT files.

---

### Post by rwabel on 2005-05-08
[QUOTE=Xian]I just installed the package straight off the website link I provided. It has a nice GUI installer that didn't complain about any needed pkgs, and then immediately I was able to play those QT files.[/QUOTE]

thanks, it worked. Don't like the gui and it's really slow to startup :-( 
for me QT files work also with totem and vlc, I will stick with them.

---

### Post by Xian on 2005-05-08
[QUOTE=rwabel]thanks, it worked. Don't like the gui and it's really slow to startup :-( 
for me QT files work also with totem and vlc, I will stick with them.[/QUOTE]
Yeah, same here. If you find something that can be browser-integrated let us know.

---

