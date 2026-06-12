---
title: "Screen resolution error; system won't pass login screen"
date: 2019-03-04
forum: General Help
---

### Post by hashxix on 2019-03-04
The strangest thing happened to my system. Suddenly, it seems Ubuntu  wasn't able to recognize my monitor resolution, so I wasn't able to see  the graphical system through my screen. It was like when the computer is  off but the monitor is on, the monitor shows a standard message asking  to verify connection with the computer and cables. 


  After verifying connections and etc, trying a few times through  different methods, finally I was able to boot into the system and the  screen was working, but monitor resolution was all messed up, it had  somehow changed to 'Auto' and it was all widened up. I don't understand  why this happened. I was working on the computer and went downstairs to  get a coffee, when I came back this stuff was happening.

  I honestly don't get it if the problem was with the screen or with  Ubuntu, but anyway, when I was able to work with the system I decided to  change resolution manually to 1920x1080. I guess I did something wrong  there, because now when I try to log in to the system, the screen that  asks for my user and password shows just fine, with the usual size and  all, but when I enter the password and confirm, my monitor shows a  message asking to verify the connection with the computer (this happens  when the computer is off and monitor is on, or if there is a problem  with the cables...). But it's not the case.


  This would seem like a problem with the monitor itself, but it is  not, since I am able to boot on and work with Ubuntu in recovery mode,  using the same monitor. 


  Can anyone clarify what is happening here? How do I change my monitor  settings back to auto, or something that makes me able to boot into my  system sucessfully (outside of recovery mode). Monitor is connected  through a RGB-PC cable and system is Ubuntu 18.04.2 LTS (Lubuntu). 

  I guess the only way to change the monitor resolution in my main  system would be through the command line in recovery mode, so how should  I do that? Anyway, sorry if it is a bit confuse, I am confused myself. I  can clarify any points if necessary.

  
Thanks!

---

### Post by hashxix on 2019-03-04
This is difficult to explain. I guess I will later score a video of my screen to clarify what I am talking about. When logging in to Ubuntu, password screen shows just fine, but when I enter password, this stuff happens to the monitor (same as it happens when computer is shut off but monitor is on). When I boot in recovery mode though, it works, but screen is all widened up. Would appreciate any help since I am clueless about what should I do here in order to fix the resolution/screen problem in my standard Ubuntu,

---

### Post by CatKiller on 2019-03-05
> **hashxix said:**
> the screen that  asks for my user and password shows just fine, with the usual size and  all, but when I enter the password and confirm, my monitor shows a  message asking to verify the connection with the computer
That sounds like your user's resolution setting has been set to something that your monitor can't handle. That setting is stored in a text file - ~/.config/monitors.xml, from memory. Deleting that file should make your user account use the same auto-detected resolution as the login screen.

You should be able to do that from one of the virtual TTYs that you get to buy pressing Ctrl-Alt-F2. The different function keys will give you a different TTY. Your graphical login screen will be on either 1 or 7, depending on how recent your version of Ubuntu is.

---

### Post by hashxix on 2019-03-06
Hello, thanks for taking the time to answer this and sorry for the delay getting back to you. Sorry to bother again, but where should I press Ctrl-Alt-F2? During boot? Would it work if I delete the file during in a recovery mode session? I am using Ubuntu 18.04.2 LTS. Sorry to ask such basic questions, but I don't wanna screw it up.

---

### Post by CatKiller on 2019-03-06
> **hashxix said:**
> Sorry to bother again, but where should I press Ctrl-Alt-F2? During boot? 

Any time after it's booted but, since you can't see anything when you're logged in, from the login screen would be the best place. There are 7 TTYs, which you can access by pressing Ctrl-Alt and the appropriate function key. Once you've done your text stuff, the login screen will probably be on 1 or 7 for when you want to switch back.

> Would it work if I delete the file during in a recovery mode session?

Yep, that should work too, although you'd then need to reboot to see if it worked. Deleting it from a live session (using the install disc) would work, too.

> I am using Ubuntu 18.04.2 LTS. Sorry to ask such basic questions, but I don't wanna screw it up.

A sensible precaution.

One thing that I should have said: when you want to delete something, but you're worried that it might break something, renaming instead of deleting is a sensible thing to do: that way you only need to rename it back if it all went wrong.

---

### Post by hashxix on 2019-03-07
Nice, CatKiller. Gonna try it out and get back to you, thanks for the help!

---

