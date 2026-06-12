---
title: "start up script (Musicbrainz)"
date: 2013-10-10
forum: General Help
---

### Post by lewishill21 on 2013-10-10
[COLOR=#333333][FONT=Lucida Grande]I would like to see if i can get some help with a start up script. Ones I look at will no longer work with the new set up. i get a error nohup: failed to run command ‘carton’: No such file or directory. This is the script i was using [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]#!/bin/sh[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]cd /home/musicbrainz/musicbrainz-server[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]nohup carton exec -- plackup -Ilib -r 2>&1 | tee /home/musicbrainz/mblog/server.log & [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]exit 0[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]They have change it from carton exec -- plackup -Ilib -r to plackup -Ilib -r. If i drop carton exec -- it gave me a error of plackup is not find. I do have it running though /etc/rc.local. If someone can help me i would be very happy.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Thank you[/FONT][/COLOR]

---

### Post by L486XGW on 2013-10-11
The error just means it cannot find the carton binary. Try changing to the full path of the carton command. If that carton program is in that folder [COLOR=#333333][FONT=Lucida Grande]/home/musicbrainz/musicbrainz-server you can just change it to ./carton probably[/FONT][/COLOR]

---

### Post by lewishill21 on 2013-10-11
Thanks for replying but what i have readed is it all have to do with Plackup its self that why they drop what they did its in app file to pick it up. but they talk about making a more [COLOR=#333333][FONT=Helvetica]permanent setup but i can not make head or tails of it.
[/FONT][/COLOR][https://metacpan.org/module/plackup](https://metacpan.org/module/plackup)
[https://github.com/metabrainz/musicbrainz-server/blob/master/INSTALL.md#starting-the-server](https://github.com/metabrainz/musicbrainz-server/blob/master/INSTALL.md#starting-the-server).

again thank you for replying

---

### Post by lewishill21 on 2013-10-12
/home/musicbrainz/.cpan/build/Carton-v1.0.12-JZy7Ij/blib/script/carton
/home/musicbrainz/.cpan/build/Carton-v1.0.12-JZy7Ij/script/carton




kk now if i use the Terminal to run run_server.sh it will work but if i have rc.local to load it my log tell me errors. the one that work in the terminal is as follow.


#!/bin/sh


cd /home/musicbrainz/musicbrainz-server
nohup plackup -Ilib -r 2>&1 | tee /home/musicbrainz/mblog/server.log & 


exit 0




Musicbrainz use to use: 
carton exec -- plackup -Ilib -r to start the server
Musicbrainz use now is :
plackup -Ilib -r to start the server


They have drop (carton exec -- )

---

### Post by lewishill21 on 2013-10-15
[h=3][Re: start up script (Musicbrainz)]("http://forums.linuxmint.com/viewtopic.php?f=18&t=147201&p=774430#p774410")[/h][COLOR=#333333][FONT=Verdana][[IMG]http://forums.linuxmint.com/styles/linux-mint/imageset/icon_post_target.gif[/IMG]]("http://forums.linuxmint.com/viewtopic.php?p=774410#p774410")by **[karlchen]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=74921")** on Tue Oct 15, 2013 10:52 am[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hello, lwshll.

_Action plan: [IMG]http://forums.linuxmint.com/images/smilies/icon_wink.gif[/IMG]_

[LIST=1]
[*]With root privileges correct the file /etc/rc.localCODE: [SELECT ALL]("http://forums.linuxmint.com/viewtopic.php?f=18&t=147201&p=774430#")sudo gedit /etc/rc.localto readCODE: [SELECT ALL]("http://forums.linuxmint.com/viewtopic.php?f=18&t=147201&p=774430#")su -  musicbrainz -c "/home/musicbrainz/run_server.sh"
exit 0Explanation:
Change user id to user musicbrainz, load the user's environment variables and run the script "/home/musicbrainz/run_server.sh".
Keep the "exit 0" as the comment in rc.local requests.
[*]Change the script run_server.sh to read:CODE: [SELECT ALL]("http://forums.linuxmint.com/viewtopic.php?f=18&t=147201&p=774430#")#!/bin/bash

cd /home/musicbrainz/musicbrainz-server
nohup plackup -Ilib -r 2>&1 | tee /home/musicbrainz/server.log &

exit 0Explanation:
We want the script to use bash, so we tell it to use /bin/bash instead of /bin/sh which might be /bin/dash actually.
As you found out yourself we have to drop the "carton exec --" part.
[/LIST]
Hope these 4 changes will fix all the problems and the musicbrainz server will come up finally.
As the server depends on the network it is imaginable that the network might not be available when rc.local is executed. In this case we will have to think of a workaround to delay the actual start of musicbrainz. But perhaps it will simply work now.

Kind regards,
Karl

**[karlchen]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=74921") over at linux mint has been working with me on how to fix this and i want to show you guys how we fix it and gave a big thanks to Karlchen.**[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enlightened by [COLOR=#8000BF]*Lucid Lynx*[/COLOR], enchanted by [COLOR=#00BF00]*Maya Mint*[/COLOR], productive on *[COLOR=#FF8000]Precise Pangolin[/COLOR]'s* [COLOR=#00BF00]*Minty sister*[/COLOR][/FONT][/COLOR]

---

