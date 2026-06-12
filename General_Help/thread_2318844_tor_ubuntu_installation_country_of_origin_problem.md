---
title: "tor ubuntu installation country of origin problem"
date: 2016-03-29
forum: General Help
---

### Post by ghostwolf2 on 2016-03-29
[COLOR=#333333][FONT=Verdana][FONT=Lucida Grande]hi,
I just reused an old laptop that ran like a dog using windows - now installed ubuntu desktop 14.04 - runs heaps better and are mostly stable [IMG]http://torforum.org/images/smilies/icon_e_smile.gif[/IMG]
One problem though - after installing tor browser where I want to fake a swedish origin, i,e updated /etc/tor/torrc by adding the following lines ..
ExitNodes {se} 
StrictNodes 1

But the tor browser fail to give me a swedish ip [IMG]http://torforum.org/images/smilies/icon_e_sad.gif[/IMG] - the ip returned is either German, French, Dutch, Russian or US based - seem like my setting is completely ignored for some reason ? [IMG]http://torforum.org/images/smilies/icon_question.gif[/IMG] 
Have no idea why this happens - Everything I read simply state that I need to add the ExitNodes node, node, node and StrictNodes 1
In the past when using a windows based system this worked just fine,
Another thing I noticed that differs between a windows install and the ubuntu one is that the torrc under ubuntu have everything commented out in the torrc - looks like the template with noting activated - from memory the windows based one had some stuff activated - so not sure if I need to activate/add some more stuff to the torrc under ubuntu
The tor version I installed is .... 5.5.4[/FONT]
[/FONT][/COLOR]
[ghostwolf]("http://torforum.org/memberlist.php?mode=viewprofile&u=5411") [COLOR=#000000]Posts:[/COLOR] 2[COLOR=#000000]Joined:[/COLOR] Mon Mar 28, 2016 12:06 pm[RIGHT][COLOR=#536482][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

