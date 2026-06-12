---
title: "starting x through command line"
date: 2007-09-26
forum: General Help
---

### Post by cinematography on 2007-09-26
* When I press ctrl-alt-f3 I see a log in window
* I then log in using my username and password
* After this step, how do I start x if I'm already logged in? 

When I try to 'startx', I get the following message:
"Server is already active for display 0"


Any help would be greatly appreciated.

---

### Post by LuisFelipeLive on 2007-09-26
when you press ctrl+alt+3 you are going from display 0 to display 3, and the x server starts automtically when you boot your computer in display 0, so if you close the x server running at the display 0, you can run the x server at display 3




sorry for my bad english, its my first post and i speak spanish :p

---

### Post by zach12 on 2007-09-26
sudo startx maybe

---

### Post by bodhi.zazen on 2007-09-26
startx -- :1 

This will start a new session on Ctrl-Alt-F8

See this link for details : 

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

### Post by cinematography on 2007-09-27
startx -- :1 did the trick

Thanks a lot for the replies!

---

