---
title: "Sidebar keeps fading away."
date: 2018-06-14
forum: General Help
---

### Post by petercartersr on 2018-06-14
[LEFT][COLOR=#263238][FONT=Roboto][/FONT][/COLOR][COLOR=#263238][FONT=Roboto][LEFT][COLOR=#263238][FONT=Roboto][COLOR=#263238][FONT=Roboto]I am running a Dell [/FONT][/COLOR]precision[/FONT][/COLOR][COLOR=#263238][FONT=Roboto] 3500; my OS is Ubuntu 18.1 Bionic beaver. My sidebar keeps fading away. I have repeatedly gone into the tweak tool and towed it to remain static, and it still slides away. I've clicked the button to restore defaults and then selected the option for the launcher to stay open, and again, it slides away. I upgraded to 18.1 hoping that would fix it and yet it acts the same. Any help would be much appreciated.[/FONT][/COLOR]
[/LEFT]
[/FONT][/COLOR]
[COLOR=#263238][FONT=Roboto][/FONT][/COLOR]
[/LEFT]

---

### Post by bijayalaxmi1808 on 2018-06-14
I really did not understand when you say slide away !
Can you attach some screenshot (if it is ?possible) of the exact issue you are facing?

Otherwise it seems like there is not much info to answer to your problem.

---

### Post by petercartersr on 2018-06-14
I have two screenshots here; the first one has the toolbar, the second one is after it slides away. I know that this is a feature that can be enabled or disabled. However, where my problem comes in is even when I turn off the feature it still slides away to the right. 
[IMG]https://www.dropbox.com/s/1c7h0sp500h7083/Screen2.jpg?dl=0[/IMG]
[https://www.dropbox.com/s/2mw96v72tq8pgbg/Screen1.jpg?dl=0](https://www.dropbox.com/s/2mw96v72tq8pgbg/Screen1.jpg?dl=0)

[IMG]https://www.dropbox.com/s/1c7h0sp500h7083/Screen2.jpg?dl=0[/IMG]
[https://www.dropbox.com/s/1c7h0sp500h7083/Screen2.jpg?dl=0](https://www.dropbox.com/s/1c7h0sp500h7083/Screen2.jpg?dl=0)

---

### Post by ajgreeny on 2018-06-14
It looks and sounds as if you may have the Dock set to Autohide when a window overlaps it.

Go to Settings -> Dock and change that setting to Off to see if that solves your problem.

---

### Post by petercartersr on 2018-06-15
Yes, that is what I did, and it acts as if I didn't, it just blinks and the check mark remains,  it will not let me uncheck it. When I close the settings window, the docker still slides away. I have used Ubuntu for years, and that is one of the first things that I do. Just a pet peeve of my but I can't stand it. Anyway, I have been trying to fix it for eight months now, with no success.

---

### Post by ajgreeny on 2018-06-15
Strange!

Can you check ownership of all in your home with command ```
ls -la
```
Everything should belong to you and if that's not so it may account for your inability to edit the files that are configuring that setting.

---

