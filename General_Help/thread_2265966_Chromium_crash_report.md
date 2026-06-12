---
title: "Chromium crash report"
date: 2015-02-18
forum: General Help
---

### Post by EarendilTheMariner on 2015-02-18
[COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]CHROMIUM CRASH[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]18 Feb 2015[/SIZE][/FONT][/COLOR]

  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]I'm running a fully updated Xubuntu 14.04 OS on my HP dx5150 SFF desktop PC.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Everything was working pretty well for the last 6 months, and I was running Firefox and Google Chrome browsers without any problems.  Until Google Chrome recently crashed.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Fortunately,[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]dixie__[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3] helped me uninstall Google Chrome and then install Chromium browser on Feb. 16.  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Afterwards, [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Chromium appeared to be working fine, [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]and[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3] when I went to the CBC.ca news website [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]I[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3] played a news video without any problems.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]But later, I went to the BBC.com news website and it was working until I tried to play a video link.  None of the video links were working.  They all said “Download Flash Player now” in the video boxes.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]So, I realized I probably didn't have any plugins installed.  So I went browsing for Silverlight, and tried to install it, but I couldn't seem to install it.  Then I read that Silverlight is not supported by Chromium.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]So, then I installed Adobe Flash.  And right after I installed it, my computer really slowed down and almost froze.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]So, I checked all my Chromium plugins and realized that Silverlight was installed, and Flash was also installed, and they were both active at the same time.  Did that cause the crash?[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Then Ubuntu told me that Chromium closed unexpectently and crashed.  A similar crash had happened before,, when I was running Google Chrome.[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]I screen capped the Chromium crash logs and pasted them here...[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]http://imgur.com/a/hLjuR[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Here are the crash logs that I got when Chrome had crashed just[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]t bef[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]ore the last crash:[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]http://imgur.com/a/BptcU[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]So, then I went to the Freenode Chromium-support channel, and they told me that Silverlight and Flash plugins don't work with Chromium, and I need to install the PPAPI plugin  (Pepper Flash)[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Should I follow his advice?[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Here is the link he gave me...[/SIZE][/FONT][/COLOR]
  [COLOR=#000000] [FONT=Liberation Serif, serif][SIZE=3]http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Should I disable Silverlight and Adobe Flash plugins, and then install the PAPPI Pepper Flash?[/SIZE][/FONT][/COLOR]
  
 
  [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]Full report:  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]http://pastebin.com/07eB6cBw

Sincerly,

EarendilTheMariner
[/SIZE][/FONT][/COLOR]

---

### Post by EarendilTheMariner on 2015-02-19
[LEFT] [COLOR=#000000][FONT=Liberation Serif][SIZE=3]My chromium seems to be running ok on xubuntu 14.04, but after an hour or so, the browser caused my HP dx5150 PC to make whining sounds and my whole OS slowed down.

I had disabled all my plugins shortly before this freezing problem.
[/SIZE][/FONT][/COLOR]
[/LEFT]
  [LEFT] [COLOR=#000000][FONT=Liberation Serif][SIZE=3]I[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]t took me almost 5 mins to boot up LibreOffice Writer, [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]while Chromium was running.  T[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]hen it took another 4.5 minutes to boot up Firefox.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT]      [COLOR=#000000][FONT=Liberation Serif][SIZE=3]When I closed Chromium, my [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]X[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]ubuntu OS went back to normal, and speeded back up and the whining sounds disappeared.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT]      [COLOR=#000000][FONT=Liberation Serif][SIZE=3]So, obviously Chromium is causing the freezing problem for my OS.  Did this happen because I disabled the Adblock Plus?[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] [COLOR=#000000][FONT=Liberation Serif][SIZE=3]I suspect there's something more serious wrong with my installation of Chromium.

     I haven't even installed my Pepper Plugin yet.  I was about to do so, when I noticed this problem.

I think I should resolve this freezing issue, before I install the PAPPI Pepper plugin, right?

     So, how should I resolve this problem with Chromium?
[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] 
Sincerely,

EarendilTheMariner

 [/LEFT]

---

### Post by dino99 on 2015-02-19
i'm a chromium user, but only with gnome-shell (because its my fav choice  :guitar:) and it never have crashed. I only have pepperflashplugin-nonfree installed because all the other choices are crappy and/or outdated/unmaintained.

So you need to know all the related "flash" packages installed on your xubuntu pc: open your file manager to list them. Then purge them all (sudo apt-get purge ...) and finally install the pepperflashplugin-nonfree driver.
then log-out/in to test the new 'stable' xubuntu ):P

** you indeed check your logs don't you ? and clean your system also ? (clean, autoclean, autoremove) and run 'apt-get install -f' from time to time ?

---

