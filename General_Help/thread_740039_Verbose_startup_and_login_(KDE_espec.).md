---
title: "Verbose startup and login (KDE espec.)"
date: 2008-03-30
forum: General Help
---

### Post by nfox on 2008-03-30
Hi,

     I have KDE (Gutsy) on one of my laptops and now (as in only since today) when I log in, the desktop loads then instantly jumps to Compiz, the screen goes black as it reloads the desktop then the cursor turns to a hand (url-esque) and I lose all input. Black screen freezes completely but sound will continue to play like if firefox reopens to a page that will seem to be the only response from the PC. 

     If I log in with Flux all is well I can even successfully start Compiz from it (separate question about that below) so I'm thinking that it's not Compiz related. I even moved the .desktop entry for it up out of ~/.kde/Autostart/ to be sure but it still loads Compiz. 

     My current thinking would be to get a list of everything that runs when I log in and pinpoint where it goes wrong. With Alt+F2 allowing boot-time verbosity, I think this should be an included feature of Ubuntu for power users

     Also, I would like to know how to grab the command that is run when I'm in Flux that allows me to successfully start Compiz.
I know that Flux *doesn't* inherently support it due to it being an integrated window manager yet it still works. I have the option in Fluxmenu to choose either Kwin or Compiz and it seems to work. Kwin, as stated above, will still crash but Compiz does start properly. I would like to let that autostart at login. With that, I could load Flux (~4sec. login time) and then start Compiz, Kicker and Kdesktop automatically and run quicker than a regular KDE session.

---

