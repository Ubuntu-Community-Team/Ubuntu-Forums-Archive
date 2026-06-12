---
title: "Orage problem at login"
date: 2012-12-17
forum: General Help
---

### Post by scruffyeagle on 2012-12-17
I have an installation of Xubuntu v10.04 on a Dell 9400 laptop. When I log into the OS, 2 things always happen:

1) The "tips" window displays (which I chose & want), and

2) The Orage program throws 2 boxes onto screen: The "Preferences" window, and the "Calendar" window.

I definitely DON'T want that 2nd item - but, I haven't been able to get it to stop doing it. I know this isn't necessary for having Orage, because I have another installation of Xubuntu on a Toshiba laptop, and it doesn't do it there. I haven't been able to figure out what's different between the 2 installations, to cause it to do this. Having run out of things to try, I'm inquiring here.

All 3 boxes are ending up centered on the screen. The layering sequence from topmost to bottom is Orage Preferences window, Tips window, & Calendar window.

Can anybody instruct me on how to fix this?

---

### Post by Sonador on 2012-12-17
I'm running xubuntu 12.04 so in 10.04 it may be different...

Be sure to remove Orage from Session and Startup tabs in applications menu > settings > settings manager

or try to delete (backup it) folder **~/.cache/sessions**

Also untick "Save session..." in log out window.

---

### Post by scruffyeagle on 2012-12-18
Thanks! I'll try it next time I'm in that OS. (I've got dual-booting w/ Ubuntu 10.04, & that's what I'm using at the moment.)

---

### Post by scruffyeagle on 2012-12-26
Sonador: What you suggested didn't really solve my problem, but it led me to the solution. I say it that way because Orage wasn't listed in the startups section, and only listed as a running process in the session section. But, it gave me the idea to quit Orage, and then save the session on restart. Now, it starts up w/o Orage. This is better than having 2 extra boxes pop up in the middle of the screen during startup, but not quite what I was after. Now, I have to start Orage manually to get it going. What I really wanted, was to have Orage start automatically, but NO POPUP BOXES on the screen during startup. I don't want Orage pestering me to interact with it right away... All I really want is to have the Orage icon placed on the panel. Do you know of any way to accomplish that?

---

### Post by Sonador on 2012-12-27
**Current** Orage is able to show the systray icon only - in orage preferences -> calendar start -> hide (as you can see in the attachment). Maybe it was not implemented in time of Xubuntu 10.04 release... if so you could only upgrade to newer xubuntu or newer xfce (via ppa).

EDIT: Just to make it clear - by icon on the panel do you mean _systray_ or _DateTime_ (orage panel plugin)?

---

