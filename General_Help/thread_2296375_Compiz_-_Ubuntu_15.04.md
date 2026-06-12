---
title: "Compiz - Ubuntu 15.04"
date: 2015-09-25
forum: General Help
---

### Post by Sky_Dog on 2015-09-25
Hi all,

I have a question regarding the process "**compiz**".

I am using a **JAVA program** in Ubuntu which _displays a lot of messages_ in the command line. A couple of second after starting the program, the messages are displayed and **compiz**'sCPU usage raises to more than 100%.

Is it normal? Should the compiz process use so much CPU? Or is the problem that my JAVA program displays to much messages in the terminal?

When I don't run the JAVA program, then I have no CPU usage problems.

Regards
Skydog

---

### Post by grahammechanical on 2015-09-25
Compiz is the compositor/window manager. If the screen is being redrawn, such as when we move an application window around, then compiz will use more CPU resources temporarity. Are you running the terminal full screen? Is the program redrawing images on the screen. Something in your program is causing Compiz to do some work. Certainly, a task that prints text to the ternimal window will cause Compiz to redraw the area of the terminal window. If there is a lot of text then there is a repeated redrawing task to be done.

Regards.

---

### Post by Sky_Dog on 2015-09-25
Hi grahammechanical,

I am not running the terminal in full screen. I only start the program in a small window, where a lot of text is shown every second, but I think that I am not the only one running such kind of programs. Is there a way to make the compiz process to use less CPU? The terminal only displays text, nothing else, it is not a 3D Game.

Or what can I do with this problem? I have to run the JAVA application in Ubuntu

Regards
Skydog

---

