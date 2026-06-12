---
title: "terminal commands display/new line problem under 18.04"
date: 2019-03-07
forum: General Help
---

### Post by Claus7 on 2019-03-07
Hello,

I wanted to post a problem I was facing recently because of an option and the solution followed in order to solve it. It might be trivial, yet it was somewhat bothersome and I was not able to find a solution on the net, since most problems had to do with overlapping of letters.

While opening gnome terminal I had a problem with the issuing of commands: 
1) if the path of the terminal was not long the fonts and strings were displayed as they should, yet while typing the command, before reaching the right end of the terminal, a new line was used leaving some empty space in the first line.
2) if the path of the terminal was long, then even if there was space available for issuing commands at the same line where the path ended, this was not used and a new line was used instead, yet now with the display of characters being problematic: for example when typing ls what I was able to see was l----s, where - is used to show the space between the letters l and s.

The problem was solved under Tweaks->Fonts->Antialiasing

For some reason the option chosen was Subpixel. When changed to standard things were back to normal. 

EDIT: posted too soon! problem#2 not solved. It seems that this is related with a bug about libfreetype6 package...

Regards!

---

### Post by TheFu on 2019-03-07
You don't need to use Gnome-Terminal. There are others which might be better for your needs.  

Picking a terminal program is very personal. Some people want fancy controls, tabs, integration with the Gnome-clipboard.

I want the tightest, lightest, term that supports utf8 in a system monospaced font. No tabs. No colors. X11 buffer for select & paste operations. I consider the gnome-clipboard to be an abomination.

To each their own.

---

### Post by Claus7 on 2019-03-08
Hello,

thank you for your response, yet gnome terminal was working fine all this time long. The thing is that I face that problem using a laptop and not a desktop computer. Now installing the libfreetype6 from disco, did not change anything. Also, enabling the pre-released updates did not change things either. The problem appears when the path is long, meaning taking almost a line or more.

Colors in terminal are really helpful since you can tell the difference between ordinary files and folders for one... Of course this is a matter of taste.

I think I will live with what I have for now...
EDIT: seems I have to drag the window on the right for proper display...

Regards!

---

### Post by Claus7 on 2019-04-15
Hello,

other than that it seems that it is a hinting problem. Anyway, from gnome tweaks either hinting to medium seems to work (yet it deteriorates fonts somehow) or scaling factor set to 1,02 edit[1,08-temporal] leaving hinting to the default value slight.
After restart it needs tweaking again...

edit2: cosmic had the more or less the same behavior, yet in disco things are working ok!

Regards!

---

