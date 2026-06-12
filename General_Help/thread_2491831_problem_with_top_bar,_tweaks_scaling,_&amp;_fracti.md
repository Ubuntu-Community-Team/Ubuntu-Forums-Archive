---
title: "problem with top bar, tweaks scaling, &amp; fractional scaling"
date: 2023-10-22
forum: General Help
---

### Post by jgw on 2023-10-22
I have found that if I set the fractional scaling to 1.50 the top bar is bigger and easier to read.  I also have found that if I set fractional scaling in system settings things get much bigger than not setting that and setting fractional scaling to 1.50 in tweaks.  

My resolution is set at 1680x1050  (1920x1080 bigger than my monitor/TV).  I would actually like it a bit smaller as stuff like software & updates, software updater run off the page.  They don't do that when scaling not set at 1.50 but makes the top bar almost unreadable.  

Wondering if anybody has a solution to this one.

Thank you..............

---

### Post by MAFoElffen on 2023-10-22
What graphics renderer engine are you using? Xorg, wayland or x-wayland?

EDIT: I searched and found that you did a run a system-info report for 1fallen (way back when), but that was sent to Termbin, which only keeps their pastebin's for a short period of time, so no longer their. I could have looked up your hardware from that. I have since asked you to run it, but you never posted where that went to...

Could you please run that again. That would fill in a lot of the blanks to see what we are trying to find a solution for and what things are set to.

---

### Post by Claus7 on 2023-10-23
Hello,

just go to /usr/share/themes and pick up the theme you are using. Enter that theme and from there enter gnome-shell folder. There you will find the file gnome-shell.css. 
Open the file as root and change on top the line font-size. A value close to 16 would be appropriate from what I read from your post. Save, close and log out and back in.

Regards!

---

### Post by jgw on 2023-10-23
MAFoElffen - thanks for the reply!

First...  I have been having a lot of problems with things not working but I am fixing stuff by doing stuff which may have caused more stuff to happen but, so far, things are working.  I am currently using Wayland.   I had to move graphics from nvidia to  NVC1 (xorg) to get access to my top bar for instance.  I just noticed that I had Nvidia X server setting in startup programs.  Didn't seem to make any difference but I stopped that because I no longer am using Nvidia.  

The system-info is one I have had for a bit, now.  I think I could get another one if I can find the address.  I also may not be using it right but this is what I have.  I run it as ./system-info:
system-info:[https://pastebin.ubuntu.com/p/rnj6HmPyDQ/](https://pastebin.ubuntu.com/p/rnj6HmPyDQ/)

---

### Post by jgw on 2023-10-23
Claus7 - thanks for the reply.........

Here is what is at the top of gnome-shell.css:
/* Global Values */
stage {
  font-size: 11pt;
  color: #3D3D3D; }

I think that you want me to change the 11pt to 16pt.  My question is whether that would make things larger?  (larger is my problem)

Thoughts?

---

### Post by coley9225 on 2023-10-23
I noticed in your OP that your running at 1680x1050 rather than 1920x1080, stating that it runs off your screen at the higher resolution. I had the same problem. Just a suggestion, but go into you TV settings( not computer settings) and look for a setting for your screen. Make sure it is set to "normal", not wide screen or some other options in there. Then try going back to 1920x1080 in you monitor settings and see if that makes everything stay on the screen. It may not help with your current problem, but worth a try. If it is still a little screwy, you can always go back to the power resolution. Good luck.

---

### Post by MAFoElffen on 2023-10-23
Wait... That is the path for systemwide. For per/users wouldn't the user edits be? (Yaru)
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls ~/.themes
Adwaita       Emacs                Prof-Gnome-Darker-3.6    Raleigh    Yaru-light
Adwaita-dark  HighContrast         Prof-Gnome-Light-3.6     [COLOR=#ff0000]Yaru[/COLOR]
Default       Prof-Gnome-Dark-3.6  Prof-Gnome-Light-DS-3.6  Yaru-dark

```
(Yes, my themes are tweaked. LOL)

And to find his personal user css files
```

ls ~/.themes/Yaru/*/*.css

```
Then add the font edit to there (in the user css file, after the import), where it would override the system setting?

Just thought I would point that out.

---

### Post by Claus7 on 2023-10-24
Hello,

> **jgw said:**
> Claus7 - thanks for the reply.........

Here is what is at the top of gnome-shell.css:
/* Global Values */
stage {
  font-size: 11pt;
  color: #3D3D3D; }

I think that you want me to change the 11pt to 16pt.  My question is whether that would make things larger?  (larger is my problem)

Thoughts?

the answer is affirmative. You should use this, without changing fractional scaling though either in settings->display or scaling factor under tweaks->fonts.

In case you do have used fractional scaling, then you should use a smaller value there, so as to see things smaller. If you do not like the result, you could revert the changes back to the original value.

Regards!

---

### Post by jgw on 2023-10-24
Thanks for the reply........

This is all very strange.  Its not everything just some things.  Like software & updates and software updater.  On this machine its all about thunderbird - its gone huge.  The interesting thing is that when I search for thunderbird size its all about stuff being smaller.  

Right now I am at a different machine and will study on the bad one later or tomorrow.

---

### Post by Claus7 on 2023-10-25
Hello,

you are welcome. The only I did is come across your issue and posted an answer, while tampering with tweaks and settings ~ a week ago in order to set the desired font size. I do not remember exactly which option, yet when selected it was increasing things not so uniformly and thus I abandoned the idea of configuring things that way. The best way was the one I mentioned to you. I'm not aware if something else is the problem, yet the solution I'm proposing you can both be easily implemented and undone later.

Unfortunately I'm not using thunderbird so I cannot tell. I do not know if thunderbird has its own configuration. You could try all solutions and see what fits best.

Regards!

---

### Post by jgw on 2023-10-25
Thunderbird also has a forum where I can ask questions.  So far, however, there have been no solutions but I continue to try.  

That forum starts at forums.mozillazine.org

---

