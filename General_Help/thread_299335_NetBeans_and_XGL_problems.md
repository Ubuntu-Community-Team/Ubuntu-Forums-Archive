---
title: "NetBeans and XGL problems"
date: 2006-11-14
forum: General Help
---

### Post by igknighted on 2006-11-14
I am trying to use the NetBeans IDE while logged into an XGL session, but I am having some issues.  I installed via the binary from Sun, and it installed fine.  The program runs, I don't get any error messages even when running from the terminal, but after the loading splash when the program's window comes up it is blank.  I can hold my mouse over the window and it will act like things are there (resize handles within the window, the hand for links, etc.) but it is a blank white screen.  Is there a way around this or will it not work with XGL?

---

### Post by aktiwers on 2006-11-14
I have the exact same problem..  and didnt find a solution for it.
But im a begginner at Java programming, so I use BlueJ.. Its only for beginners, But works fine though..

---

### Post by igknighted on 2006-11-14
For a beginner let me recommend using a text editor and the console tools... fast and effective, plus (at least for me) it gets you closer to the program.  I use Kate because I use KDE, I recommend SciTE for GNOME.

---

### Post by darcof on 2007-01-23
try with this, put into the script file of NetBeans  this line:  export AWT_TOOLKIT=MToolkit 
save the file and have fun! :) 



> **igknighted said:**
> I am trying to use the NetBeans IDE while logged into an XGL session, but I am having some issues.  I installed via the binary from Sun, and it installed fine.  The program runs, I don't get any error messages even when running from the terminal, but after the loading splash when the program's window comes up it is blank.  I can hold my mouse over the window and it will act like things are there (resize handles within the window, the hand for links, etc.) but it is a blank white screen.  Is there a way around this or will it not work with XGL?

---

### Post by donut_irl on 2007-01-30
I had the same problem, and this fixed it.

Thanks :)

---

### Post by Mba7eth on 2007-02-02
Bravoooooo [COLOR="Red"]darcof[/COLOR]
Mine is solved too :grin: 
 :guitar: :guitar: :guitar:

---

### Post by greypegasus on 2007-02-25
I don't have to ask then..
Thank you..

---

### Post by jtax on 2007-03-01
hey, thx for the help!  Just wanted to add that i tried putting the export code at the end and it didn't work, but placing it at the top worked fine.

---

### Post by Nikitas350 on 2007-04-25
Thanks. It solved my problem...

---

### Post by buzzler on 2007-05-11
i'm using netbeans 5.5 and jdk6 and beryl on feisty
i dont use this method

> try with this, put into the script file of NetBeans this line: export AWT_TOOLKIT=MToolkit
save the file and have fun! 

i simply load netbeans with the blank window, use beryl manager to change from beryl to metacity (GNOME window manager), and then load back beryl

it works

---

### Post by akersj on 2007-05-12
as a total n00b starting with NetBeans on Ubuntu for the first time ... where is this configuration file to edit?

---

### Post by christiano on 2007-06-02
You must add :

export AWT_TOOLKIT=MToolkit

...to the file:

[Netbeans install path]/netbeans-5.5.1/etc/netbeans.conf

/Christian

---

### Post by Nikitas350 on 2007-06-20
if you do ti. then some times your keyboard locks. Any solution?

---

### Post by vivienma on 2007-06-29
> **igknighted said:**
> For a beginner let me recommend using a text editor and the console tools... fast and effective, plus (at least for me) it gets you closer to the program.  I use Kate because I use KDE, I recommend SciTE for GNOME.

hey stupid kids, imaging coding a large system using your small text editor? are you crazy or just a beginner of coder yourself?

---

### Post by v3d on 2007-09-16
> **Nikitas350 said:**
> if you do ti. then some times your keyboard locks. Any solution?


yes i have same problem.. keyboard locks after openning a window inside netbens. after close the file and open it the keyboard runs again? Is there a solution?

---

### Post by xcesarfrancox on 2007-09-20
When I change from netbeans to another window and then go back to netbeans my keyboard is locked!! is there any solution?

---

### Post by Kenniej on 2008-03-18
This thread may be old , but DAMN THNX darcof !!! totally solved my prob in a wip ^_^


Grtz,
Kenniej

---

