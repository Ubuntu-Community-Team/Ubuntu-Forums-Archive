---
title: "New User with a problem that can't be specified"
date: 2008-04-30
forum: General Help
---

### Post by Nukenfry on 2008-04-30
In a title that is.

It happens every damn day, my primary panel with Applications, Places, System etc. will stop working when I try to use it (on various occasions, not every single time I click on it, but it will do it once or twice a day). If a program does open up I have to force quit it because it will not respond. So I try simply logging out and logging back in but after putting my information in the screen just freezes, no sound to let me know it's logged me in, just a giant orange screen. Most of the time a whiteish box appears in the upper left hand corner, but nothing in it. I have to restart the computer each time this occurs. Everything else on Ubuntu works flawlessly, I like it, but it be a real shame for THIS damn minor but very frustrating problem to ruin my experience.

---

### Post by lungten on 2008-04-30
I  experience the same kind of behavior on my box running Hardy. In my case it because of the ATI card. Its a ThinkPad T43p with Mobility FireGL V3200 card. I have Compiz enabled using ATI proprietary drivers. There's no problem with the Visual Effects disabled but the problem is bearable to me with the effects enabled.

Have you got Visual Effects enabled? What video card are you using?

My suggestions:
> my primary panel with Applications, Places, System etc. will stop working when I try to use it
If you have a terminal open, just run```
killall gnome-panel
```
This will reload your panels. If you don't have a terminal open, create a shortcut key combination so that you can open terminal the next time panel freezes again. [Alt+Tab] to switch to an open terminal.

> no sound to let me know it's logged me in
Check System>Preferences>Sound>Sounds to see if you have login sound enabled.

> I have to restart the computer each time this occurs
You don't have to restart the computer. You can just [AlT+Ctrl+Backspace] to restart the GDM.

---

### Post by Nukenfry on 2008-04-30
Thanks for the response and I do in fact have ATI and I feared that was the issue. I also do have Visual Effects enabled. I am also aware of the re-logging in method and I do that, problem is after I re-put my information in nothing happens, just a blank orange screen. Then I have to re-do the log in method, click on options and restart and THEN I can get back in.

---

### Post by lungten on 2008-05-01
Well, if the problem is because of the ATI (as it seems to be), we don't really have a good solution for now. All you can do is disable to visual effects. Visual effects - though its nice to have its not a necessity.
But things have been better for me in Hardy. My card can run compiz but with some problems like the one's you mentioned earlier. It doesn't happen all the time though.
From what I hear, older ATI cards can run compiz on Ubuntu Hardy with the new ATI drivers and XOrg server.

---

