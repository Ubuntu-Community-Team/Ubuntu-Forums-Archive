---
title: "Browser rendering issues with 18.04"
date: 2018-09-05
forum: General Help
---

### Post by vebut on 2018-09-05
[COLOR=#242729][FONT=Arial]I'm reporting this here since there is no regular "submit report" form on launchpad. The ubuntu-report command from the ALT+F2 menu wants a specific package or software, but this issue is across ALL browsers on 18.04.

This is a cross-post from AskUbuntu.com, but I'm not sure if this forum is more considered "official" and that it reaches the correct people. I guess mods can delete this thread if they consider it a duplicate.

On Ubuntu 18.04 I'm experiencing a lot of browser rendering issues with fonts and margins/paddings and I don't know if this qualifies for a bug report since I don't know if I'm the one doing something wrong.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tested this with Firefox and Chrome, and different versions at random, and all of them have the same issue under 18.04, but the same browsers and versions on 16.04 are unaffected.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Below are illustrations of the problem, and please note that I used the screen snipping tool so the two parallel images are not centered. It's not the position of the table that is the problem, it's the text inside of the table - so ignore the misalignment of borders etc.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Not only are tables affected, but all of text on web pages, so for instance if a website use bootstrap4 buttons or modals etc.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**This is how it should look like (Ubuntu 16.04)**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Chrome on the left and Firefox on the right. Note that the top and bottom padding are centered and correct. This reflects the correct results on other operating systems too, such as Windows and Mac, iOS and Android.
[IMG]https://i.stack.imgur.com/5kQUn.png[/IMG] [IMG]https://i.stack.imgur.com/fosaT.png[/IMG]

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**This is how it looks on Ubuntu 18.04**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Chrome on the left and Firefox on the right. Note how the text is offset and that the top padding is much less than the bottom padding, aka the text is not vertically centered.
[IMG]https://i.stack.imgur.com/8jDx7.png[/IMG] [IMG]https://i.stack.imgur.com/2YBW0.png[/IMG]

Is this a known bug? It makes websites look terrible and it makes development of websites a real pain. The effects are more noticeable with different font sizes etc, and can at times break website UI.

The issue can also be noticed on Ask Ubuntu on all elements as seen below. Note how all text have vertical misalignment.
[IMG]https://i.stack.imgur.com/2SPiN.png[/IMG]

Again, none of these problems exist on 16.04 or any other operating system.

I found a reply somewhere on someone thinking it might have to do with a libfreetype6 bug, and thus i tried updating to a later version were it supposedly was fixed, but that didn't solve anything - there was no change.[/FONT][/COLOR]

---

### Post by ruhulamin3482 on 2018-11-27
I am having this problem as well... I am a web developer.. I have to design in the browser. I think I might have to move to another OS.. 

There's no reply?? .. wow

---

### Post by DanPerecky on 2019-04-04
Don't know about spacing issues.... but to make grey almost-unreadable fonts clearer, there is an Add on for Firefox - **Font Contrast**

Nice, and free. And I don't see any downsides to using it (so far).

:popcorn:

---

