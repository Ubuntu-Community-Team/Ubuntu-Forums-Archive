---
title: "Java issues with firefox"
date: 2005-09-22
forum: General Help
---

### Post by Third Thoughts on 2005-09-22
Alright, I recently had to do some cleaning on my system and part of this meant uninstalling and re-installing firefox. In the process I got rid of all my java stuff and so I've had to re-install that too. I made my own package with the sun binary and created the appropriate sym link in the /usr/lib/mozilla/plugins folder, enabled java in the preferences area, and restarted the browser. I know java itself works because the command java -version gives me version info, but firefox is still giving me the "missing plugins" schtick whenever I try to view a java app. I'm running a older version of firefox, its just the one in the hoary repositories (1.0.2), but I got it working with java before. Any suggestions on how to deal with this issue?

~Andrew S.

---

### Post by Foaming Draught on 2005-09-23
"I made my own package with the sun binary and created the appropriate sym link in the /usr/lib/mozilla/plugins folder, enabled java in the preferences area,"

If I wanted to go through that sort of palaver, I'd be running a newbie-unfriendlier distro than Ubuntu. So to avoid it, until Firefox 1.5 comes out with Java (will it?) I use Epiphany for pages which require Java, like some chat rooms.
This doesn't directly answer yr question, but it's not meant to be flippant, it solves the problem.

---

### Post by Third Thoughts on 2005-09-23
[QUOTE=Foaming Draught]
If I wanted to go through that sort of palaver, I'd be running a newbie-unfriendlier distro than Ubuntu.[/QUOTE]

I run Ubuntu because I find its the easiest (of the two I've tried the other being Fedora) to get multimedia support up and running. I never had video support to my satisfaction in FC3 or 4 even after lots of tinkering. Getting video support etc took me about fifteen minutes in Ubuntu. Do you have another distro you'd suggest? I'm pretty happy with Ubuntu, it seems to have a good balance of flexibility and ease.


>  I use Epiphany for pages which require Java, like some chat rooms.


Whats the advantage of Epiphany? I'm not familar with the software so I'm just curious.

~Andrew S.

PS I solved my own problem by upgrading from Hoary to Breezy. Doesn't answer my question, but it still solves the problem ;-)

---

### Post by phex on 2005-09-23
To be honest. NONE. Epiphany uses the Mozilla Gecko Engine to render html on the screen. The same is used for Firefox and the simple old Mozilla browser, which will no longer be continued because of the great success of Firefox. The difference lies there, that Epiphany is implemented by the Gnome team and that it is starting a bit faster than Firefox although both use GTK+. Thats it. Nevertheless, i prefer Firefox over Epiphany. But this is my own taste. ;)

---

### Post by Foaming Draught on 2005-09-23
Sorry, I'm not making myself clear. I run ubuntu precisely because it is so amazingly friendly for a non-techie and I don't usually have to, as the OP puts it, ""make my own package with the sun binary and create the appropriate sym link in the /usr/lib/mozilla/plugins folder, enable java in the preferences area,". But for this particular Java problem, to be lazy, I just run Epiphany which has Sun Java already installed and enabled. 
I'm also a Firefox fan, and have no brief for Epiphany. It helps me with one or two bulletin board chatrooms which require up-to-date Java, for everything else I use Firefox. However, in passing, I have noticed marked improvements over last time I tried Epiphany (a year ago?).

---

