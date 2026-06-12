---
title: "Display resolution problem"
date: 2020-06-08
forum: General Help
---

### Post by magus7091 on 2020-06-08
I've been fighting with this for ages, but I was able to tolerate it until now, and no one has given any advice that helped. When I boot my computer, the greeter and any terminal sessions I open display at a larger resolution than my tv can properly display, and my tv is my ONLY way of displaying. I've changed the settings in GRUB, added scripts to multiple locations and bent over backwards to try to fix it and it never ever ever works. Ever. I was able to tolerate this until today when I tried changing my resolution but my tv said it's not supported. So now, when I log in, the incorrectly sized greeter and terminals is all I can see and as soon as I log in to plasma, the screen dies. I can't provide output from commands, or read the contents of config files because the edge of the screen cuts off. Xrandr says something about "open display" which I assume, based on searches is saying "cannot open display" but I can't see it, or anything else. Before this I could always use my graphical desktop to see, as it was a resolution that my tv would display, and fit, but now I don't even have that. So I need to figure out how to fix this mostly blindly.

---

### Post by GhX6GZMB on 2020-06-08
How do you connect to your TV?
VGA, HDMI, CVBS, RGB...?
What's your TV resolution?

---

### Post by magus7091 on 2020-06-08
HDMI, and I'm not sure what the tv resolution is, it was given to me pretty much as-is. I do know that it worked properly at 1360x768, before I changed it, though I don't recall now what I changed it to.
--EDIT--
Is there a config file I can edit or delete to force the resolution to reset to what my greeter is stuck at?

---

### Post by CatKiller on 2020-06-08
> **magus7091 said:**
> Is there a config file I can edit or delete to force the resolution to reset to what my greeter is stuck at?

The resolution of the logged in session is *often* stored at ~/.config/monitors.xml.

---

### Post by pauljw on 2020-06-09
Not all of the configuration can be done from Ubuntu, you must use the tv remote and enter the menu of the tv itself and set the resolution up there so you can match it in Ubuntu.

---

### Post by magus7091 on 2020-06-09
There's no configuration that has anything to do with that, only a "PC options" that can change the vertical and horizontal position. And that doesn't even apply to HDMI input. It simply says unsupported format. I changed my resolution from 1360x768 to something my TV doesn't support. I just need to figure out how to change it back to 1360x768. I'm running kubuntu 20.04 with a GeForce GTX 750 card, using nouveau drivers. I know a lot of issues can happen with Nvidia cards, and that's pretty much the only explanation I can figure because every time a search result has found anyone with my original issue, it's always been an Nvidia card, and they've always gone unanswered. So all I need is to figure out how to change my resolution setting on my computer back to 1360x768

---

### Post by magus7091 on 2020-06-09
Fixed the problem by doing
sudo mv ~/.local/share/kscreen ~/.local/share/kscreen.bak && sudo reboot
This caused my desktop session to revert to the, apparently unchangeable, 1920x1080 default resolution.

Now, if anyone can help me fix that, that'd be amazing.

---

### Post by CelticWarrior on 2020-06-09
Does it display correctly with 1920x1080 (FHD)? If so keep it.

---

### Post by magus7091 on 2020-06-09
It displays, not correctly. It's too large for my display so all 4 edges are cut off and objects are grainy and hard to read. The only resolution that displays properly is 1360x768. I can set this resolution once I'm in my desktop session but the login and F# terminal sessions are stuck at 1920x1080 which is why I'd said seeing what I was doing was extremely difficult.

---

### Post by NM5TF on 2020-06-10
@magus7091.....

you might find the answer here......[https://askubuntu.com/questions/1041677/how-to-change-the-login-screen-resolution-in-ubuntu-18-04](https://askubuntu.com/questions/1041677/how-to-change-the-login-screen-resolution-in-ubuntu-18-04)

even tho it says Ubuntu 18.04 one of the 3 answers may work for you....

tommy

---

### Post by CelticWarrior on 2020-06-10
Answers above may help with Grub customization. However your thread seems to be above resolution in general, in the user's session.

Regarding that I must echo post #5. It is indeed a matter of overscanning, something very typical in so many TVs. The solution is not lowering the resolution - the resolution should always be set to the TV's/monitor's native resolution, i.e., to the highest it supports - as reducing it inevitably results in distortions. TGhe solution is to use the TV's own settings to adjust (disable overscanning). Unfortunately this is a feature seldom described in user's manuals and, depending on the model, it may also be absolutely not intuitive to find. Some brands use an unassuming key toggle in the remote, others it's something users need to find in sub-menus inside the usual settings menus, LG puts it in the additional settings menu (Q Menu)... The point is every TV should have that feature/setting but there's no standard therefore it's up to you to find out yours. You may post the brand/model to have someone else check it for you.

---

