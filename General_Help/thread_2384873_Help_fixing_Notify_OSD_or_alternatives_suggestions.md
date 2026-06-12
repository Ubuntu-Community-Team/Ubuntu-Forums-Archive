---
title: "Help fixing Notify OSD or alternatives suggestions"
date: 2018-02-13
forum: General Help
---

### Post by mirkorm on 2018-02-13
Hello,

It's my first post on the forum so I wasn't sure where to post it and sorry for my bad english, I'm italian

I set up a light htpc and one feature I really need is the audio volume pop-up notification. The volume OSD initially didn't show up at all while the brightness indicator worked as expected, but I finally managed to make it work by installing xfce4-volumed (I really don't know why since from what I know my system uses notify osd for pop-up notifications).

The problem now is that the pop-up wouldn't appear over a full screen application, which is where I actually need it: I need a visual feedback of volume level when I adjust it while I'm watching a movie most of the times (eg. kodi, netflix, vlc, youtube at full screen). The other problem is that the notifications last too much (10 sec) so I tried to install a modified version of notify osd with the configuration tool as suggested [here]("https://askubuntu.com/questions/50/how-do-i-change-how-long-notifications-are-displayed") and set the duration to 1 second, now the brightness indicator works good as always and does as expected, but the audio volume one gives me problems here too: after 1 sec it blinks and kind of starts again, then after another 1 sec blinks again and stops after an additional 1 sec, during 3 sec total and giving two distracting blinks in the meantime. 

Now: I assume that my volume level on screen notification is somehow corrupted (the blink part that doesn't apply to brightness too gave that idea) so I'd like your help to find a way and check if and where the problem lies (eg conflicting apps, damaged program files). As for fullscreen I read that the developers messed a bit with notify-osd over full screen because some people didn't want notifications over full-screen so they decided to only show critical notifications over full-screen (but from what I understand brightness, volume and battery are considered critical, and even brightness doesn't show over full-screen, so I hope there is some hidden parameter to tweak to force notifications to be shown over full-screen).

If you even have any obvious clue to help me solve these problems please tell me since I'm very new to linux, and if you think it's impossible to fix those things on notify-osd or you don't have a clue please suggest me some alternative to notify-osd that gives me automatic (I said automatic because if I have to click on it to make it show, it's  not what I'm looking for, I need it while I'm on full screen) on-screen notifications whenever I hit a volume key to change it and works on full screen, I tried installing volnoti but I wasn't able to make it work. So again, if you can help me with installing volnoti please do, if you don't, you now know what kind of feature I'm looking for, so please help.

Thank you

---

### Post by coffeecat on 2018-02-13
Welcome to the forum, *@mirkorm*.

I've moved your thread from the Resolution Centre, which is for forum account issues, to ***General Help***, which is for technical support.

So that forum members can help you with this, please post details of which operating system you are using (Ubuntu, one of the Ubuntu flavours, or something else), and which release number (16.04 or 17.10, or whatever). Also, if not the default desktop environment of your distro, please state which desktop you are using. You mention xfce4-volumed, but I'm not clear whether or not you are actually using Xfce. The advice given depends on all this information.

---

### Post by #&amp;thj^% on 2018-02-13
This should not be DE dependent: [https://developer.run/23](https://developer.run/23)
And helpful setup script: [https://github.com/dunst-project/dunst/blob/master/dunstrc](https://github.com/dunst-project/dunst/blob/master/dunstrc)

---

### Post by mirkorm on 2018-02-13
Thank you for your answer, to install the setup script, from what I understood I should put the file dunstrc into usr/share/dunst but te problem is that there's no dunst folder, so I don't know how to use the script.

Anyway I managed to install dunst but the volume notification only gives a written percentage on volume level and not a visual one, using my pc as a tv I stay several feet away from the pc screen so I can't quite read what it says and so becomes a bit distracting, have you tested dunst or found a way to get a better indication bar popup?

Thanks

---

