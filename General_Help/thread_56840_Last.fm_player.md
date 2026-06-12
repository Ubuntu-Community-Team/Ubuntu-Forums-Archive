---
title: "Last.fm player"
date: 2005-08-14
forum: General Help
---

### Post by Bo Rosén on 2005-08-14
I downloaded the Last.fm player for Linux and it runs well from the command line. But how do I add the last.fm protocol to Gnome/Firefox so the player starts when I click on a radio link on the Last.fm website? I used to know how to do this, but Gnome has changed too much for my poor brain to keep up.

Thanks

[color=Red]Update: [color=Black]Naturally, I found the answer just after I posted. It's all there on the Last.fm forum.[/color][/color]

---

### Post by us3rQUE on 2005-11-15
1.) Goto  the address bar in firefox type: 
    about:config

2.) Right click then, select New, Boolean, type in Preference Name:
    
   network.protocol-handler.external.lastfm

   next step, set the value to: TRUE

3.) Right click again, then select New, String type in Preference Name:
   
    network.protocol-handler.app.lastfm
    
     next step, set the path to the Last.FM player (ex; /usr/bin/player)

[note for step 3 I had to close Firefox and restart it then access "about:config" in order to set a new string.]

4.) Close firefox, and reopen - you have registered the protocol lastfm:// with your last.fm player.

---

