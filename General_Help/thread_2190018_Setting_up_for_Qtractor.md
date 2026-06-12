---
title: "Setting up for Qtractor"
date: 2013-11-25
forum: General Help
---

### Post by Richard_York on 2013-11-25
I'm a non-geek, enjoying the move to Ubuntu from Windows, still learning, and much to learn!

I still also have a Windows Vista machine running Cubase LE4 for audio recording (all acoustic, with mic, not electric instruments) and don't like it - too prone to crash, and not intuitive to my mind.
So I'm looking at Qtractor as a possible alternative, and if it goes well will swap the Vista machine to Ubuntu for it.

Reviews say I need JACK first. Ubuntu's Software centre offers JACK Rack, JACK audio mixer, and a whole lot more JACK items. It also lists "jack" (note the lower case) which says it's a CD ripper, and is too new to have any reviews. Do I need /all/ of these???

There doesn't appear to be a Qtractor manual either, though reviews say it's easy to use, and less complex than Ardour, which is why it's tempting.
So I'm puzzled - what do I actually need to do to get it going? I installed Qtractor itself of the Software Center and haven't yet tried to drive it, but the initial screen looks nothing like the images it shows on its own Software Center page, nor on the review pages I found.

Any help much appreciated please, answers in non-technical language even more appreciated :-)

(Or would I do better to convert the other laptop to Ubuntu Studio, or is that a whole different question? )

With thanks,
Richard

---

### Post by ccmiller12 on 2013-11-25
I believe this might be the manual for Qtractor. [http://www.rncbc.org/archive/qtractor-0.3.0-user-manual.pdf](http://www.rncbc.org/archive/qtractor-0.3.0-user-manual.pdf)

The installation instructions there seem quite complicated. I recommend installing via terminal.

First get the PPA repositories:

[COLOR=#555555][FONT=consolas]sudo add-apt-repository ppa:kxstudio-team/ppa

[/FONT][/COLOR]Then update (always do this after grabbing repository packages):

[COLOR=#555555][FONT=consolas]sudo apt-get update

[/FONT][/COLOR]Install

[COLOR=#555555][FONT=consolas]sudo apt-get install qtractor 

[/FONT][/COLOR]Hope that helps ;-)

Cmiller

---

### Post by Richard_York on 2013-11-25
Thanks very much, that seemed to work fine. You're right, the manual looks fairly forbidding on the subject of installation, I'm glad I haven't got to build it as well as simply telling it to install!

Initial opening is giving me a whole bunch of messages, ending with :  "Cannot use real-time scheduling (RR/5)(1: Operation not permitted)

 JackClient::AcquireSelfRealTime error "

So no doubt I'll be asking more soon, since I don't know what that means, though sadly I haven't time to actually get into playing with this new toy for a few days.
Thanks for your help on installation meanwhile.

Richard

---

