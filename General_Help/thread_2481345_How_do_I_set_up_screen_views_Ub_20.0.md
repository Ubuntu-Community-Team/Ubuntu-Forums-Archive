---
title: "How do I set up screen views? Ub 20.0"
date: 2022-11-26
forum: General Help
---

### Post by Robbyx on 2022-11-26
I am finding it so difficult to read some of the screen fonts that I am having to use a magnifying glass. It is not that my vision is bad but that on 1920 X 1080 some fonts come out so small I can not read them.  My processor is AMD A10-7800 radeon, graphics are AMD Kaveri. As far as I am aware there are no proprietary AMD drivers available. 

I have tried, without adequate solution, adjusting the fonts sizes. I have also modified the Scaling Factor in Gnome Tweaks--->Fonts. My attempts do not help much, especially because adjusting the scaling factor can increase the projected size of the screen beyond the actual screen size. 

The Zoom function helps in an emergency but it is very hard to continuously use because of the way it over reacts to movement. The zoomed  area is much too big and quickly becomes tiresome. It also over reacts to mouse movements. 

I realise that others have had the same problem with monitors using the same ratio as mine. 

I ask how have others set up their font sizes, scaling factor, and anything else to make it easy to read very small fonts appearing in for example the desktop below folder icons, and  in some apps which will not upscale.

---

### Post by TheFu on 2022-11-28
I have a 1920x1200 main monitor and a 1920x1080 second monitor.  I use fvwm which allows complete control over all aspects of the GUI for the windows, titles, menus, etc.  

I'm mostly a terminal user, so I specifically set the font and size of the font to be used in my terminals.  Here's a little example that places 3 terminals for my workstation to specific locations:
```
XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
xterm $XTERM_OPTS -geometry 78x9+78+0 &
xterm $XTERM_OPTS -geometry 80x21+73+82 &
xterm $XTERM_OPTS -geometry 80x25+0+117 &
```

I launch about 10 terminals in the same script, each gets sized and placed exactly where I want, so each corner accesses different systems.  Since I almost always use the terminal to perform tasks, the same font is used for all CLI programs - problem solved.  Of course, the xterm program has a <cntl>-right-mouse menu with different font sizes available to make it larger or so small that nobody can read.  Handy when I'm sharing an entire screen and don't want others seeing a specific terminal window - just change the font to "unreadable". ;)  BTW, that is exactly how it is labeled and it is definitely true.

For Firefox, I set the default font and if it is small or large, I'll use the <cntl>-scrollwheel control to increase/decrease the font without thinking.  Most browsers and thunderbird support that mode to resize fonts.

---

