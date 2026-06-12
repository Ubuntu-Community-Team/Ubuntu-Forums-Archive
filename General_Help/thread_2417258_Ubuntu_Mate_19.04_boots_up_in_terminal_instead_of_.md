---
title: "Ubuntu Mate 19.04 boots up in terminal instead of Mate desktop environment"
date: 2019-04-22
forum: General Help
---

### Post by nishi10 on 2019-04-22
After installing Ubuntu Mate 19.04 I wanted to change the lockscreen wallpaper and didn't find a direct way of doing in the wallpaper/display setting. Hence I renamed the wallpaper currently used for the lockscreen and replaced it with a soft link with the wallpaper of my choice - and it worked fine.


Then after reading through some forums, I stumbled upon installing lightDM-gtk-greeter package from the terminal. However, I didn't find a quick way to control lockscreen wallpaper and hence I removed it via terminal commands: 
```sudo apt-get purge lighDM*```


And then rebooted the system which led to booting up in the terminal mode.
I assume/guess after purging (this may not be the right/clean way to remove a package) there should be some init file which I may have to tweak. Maybe that init file is still looking for lightDM stuff and as it is not there it got defaulted to booting up in terminal mode.


Please, can anyone help :)
1. guide me through this? how to recover
2. and explain what may have gone wrong
3. and good practices to uninstall applications the right/clean way?


PS: This is my day 2 using Linux for a desktop environment. Pardon for asking something obvious.

---

### Post by &amp;KyT$0P# on 2019-04-22
It would help to know exactly what was purged.  Log in in terminal mode, then check [FONT=Courier New]/var/log/apt/history.log[/FONT] for the log entry showing the results of running the rogue command, by running this -

```
less /var/log/apt/history.log
```

Please post the full log entry here (everything between the associated Start-Date and End-Date).

As for what went wrong?  LightDM is the program that displays the graphical login screen, so purging it will result in the system using terminal mode for the login.

---

### Post by coffeecat on 2019-04-22
Forum Feedback and Help is not for general support enquiries.

*Thread moved to **General Help**.*

---

### Post by oldrocker99 on 2019-04-22
Uh, lightdm being absent is why you're booting to terminal. Lightdm is a **display manager**, which is what you log in to get the windows manager (the desktop)

Try reinstalling lightdm, and reboot. It may well solve your problem.

---

### Post by nishi10 on 2019-04-23
[FONT=ubuntu]Correcting my terminology here: by lock screen, I meant greeter screen.
What was I trying to do: change the wallpaper on the greeter screen.

[/FONT]
[FONT=ubuntu]Initially I failed to find a native/pre-installed application which changes the login/greeter screen's wallpaper. I installed lightDM-gtk-greeter package and then I found a simpler/native way to change the wallpaper so instead of removing gtk-greeter I purged every package that was named lightDM* [/FONT]#-o[FONT=ubuntu]
Which also removed slick-greeter and the settings package. (That was not the clean way of doing it, I agree)

[/FONT]
[FONT=ubuntu]So from your feedback, I reinstalled lightdm slick-greeter and lightdm-settings and now I have got the desktop environment back and I see there is indeed an application called: **Login Window** where I can easily change the greeter screen's wallpaper and I don't need lightDM-gtk-greeter for that.

[/FONT]
[FONT=ubuntu]This time I did apt-get remove lightdm-gtk-greeter lightdm-gtk-greeter-settings so that it won't conflict with slick-greeter.

[/FONT]
[FONT=ubuntu]Thanks a ton, all! [/FONT]

---

