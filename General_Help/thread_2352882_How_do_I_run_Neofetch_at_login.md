---
title: "How do I run Neofetch at login?"
date: 2017-02-16
forum: General Help
---

### Post by laggger164 on 2017-02-16
The title says it all.

I was trying to get it working myself, but I am kind of stuck. 
The Xubuntu "Session and Startup > Application Autostart" way doesnt seem to work. I made a new startup item, named it Neofetch and in the command I put "neofetch" without the quotes.
But nothing is happening, is there another way? Or am I just doing something wrong? (very possible BTW)

Thanks for the help!

---

### Post by #&amp;thj^% on 2017-02-16
I would think you need to add it to your .bashrc file located in your Home Directory. 
Just to give you an idea as to what I mean...I use "screenfetch" which is very similar to "Neofetch"
Example of my .bashrc file:
```
alias ls='ls --color=auto'
PS1='[\u@\h \W]\$ '
screenfetch -D "Arch Linux"
inxi -C -M
```
Which then, when opening a terminal now shows this:
See Screenshot .
EDIT: Just type "**neofetch**" in your terminal to see what I mean

---

### Post by laggger164 on 2017-02-16
> **1fallen said:**
> I would think you need to add it to your .bashrc file located in your Home Directory. 
Just to give you an idea as to what I mean...I use "screenfetch" which is very similar to "Neofetch"
Example of my .bashrc file:
```
alias ls='ls --color=auto'
PS1='[\u@\h \W]\$ '
screenfetch -D "Arch Linux"
inxi -C -M
```
Which then, when opening a terminal now shows this:
See Screenshot .
EDIT: Just type "**neofetch**" in your terminal to see what I mean

Alright, all I want to run is "neofetch" in the command line. Nothing else, everything else is configured in the .config file for the neofetch script.

So should I just add "neofetch" to the end of the .bashrc file? I have never done this, so I have no idea what I am doing.

---

### Post by #&amp;thj^% on 2017-02-16
> **laggger164 said:**
> 
So should I just add "neofetch" to the end of the .bashrc file? I have never done this, so I have no idea what I am doing.

Yes that is correct just add it...and i will be very happy to help you with this.
Using Code Tags return the out put of this from the terminal.
```
pluma '/home/<your_user-name>/.bashrc'
```
<your_user_name> is your user name here.
Paste back so we can see it.....** Note** "pluma" is just a text editor  I used here so substitute that with the editor you are using...IE: mousepad, leafpad, kate, gedit....I think you understand.

---

### Post by laggger164 on 2017-02-16
> **1fallen said:**
> Yes that is correct just add it...and i will be very happy to help you with this.
Using Code Tags return the out put of this from the terminal.
```
pluma '/home/<your_user-name>/.bashrc'
```
<your_user_name> is your user name here.
Paste back so we can see it.....** Note** "pluma" is just a text editor  I used here so substitute that with the editor you are using...IE: mousepad, leafpad, kate, gedit....I think you understand.

OK so I did that, however when I log out and log back in neofetch still doesnt pop up, but when I open up the terminal neofetch always starts and then I can put in commands normally. I just want neofetch to pop up when I log in, thats it, am I doing something wrong here?

---

### Post by #&amp;thj^% on 2017-02-16
I think one of us is confused on what neofetch is:[https://www.google.com/?gws_rd=ssl#q=what+is+neofetch+for+linux](https://www.google.com/?gws_rd=ssl#q=what+is+neofetch+for+linux)

> Neoftech is a cross-platform and easy-to-use system information command line script that collects your Linux system information and display it on the "terminal" next to an image, it could be your distributions logo or any ascii art of your choice.
And
> NeoFetch — See System Information from the Command Line on Linux
So it is just a Terminal Tool or Toy depending on your view.

---

### Post by laggger164 on 2017-02-16
> **1fallen said:**
> I think one of us is confused on what neofetch is:[https://www.google.com/?gws_rd=ssl#q=what+is+neofetch+for+linux](https://www.google.com/?gws_rd=ssl#q=what+is+neofetch+for+linux)


And

So it is just a Terminal Tool or Toy depending on your view.
 The thing is, I want to make it run in a terminal when I log in or boot up, not when I start the terminal every time.
Is there a way to run a command on login?

---

### Post by #&amp;thj^% on 2017-02-16
He He... Ok now I understand what you are after...but you can not have one without the other.
The only way Neofetch works is in the terminal(CLI) that we added to the .bashrc file and that will be needed to autostart Neofetch in the terminal.
Click on the Startup Applications option or Autostart.
Click "Add"
In the "name" field, type "Terminal" without the Quotes.
In the "command" field, type "xfce4-terminal" without the Quotes.
Click "Add"
You are done! Next time you login, the terminal (with Neofetch) app will be launched.
I hope this is clear enough now.

---

### Post by laggger164 on 2017-02-17
> **1fallen said:**
> He He... Ok now I understand what you are after...but you can not have one without the other.
The only way Neofetch works is in the terminal(CLI) that we added to the .bashrc file and that will be needed to autostart Neofetch in the terminal.
Click on the Startup Applications option or Autostart.
Click "Add"
In the "name" field, type "Terminal" without the Quotes.
In the "command" field, type "xfce4-terminal" without the Quotes.
Click "Add"
You are done! Next time you login, the terminal (with Neofetch) app will be launched.
I hope this is clear enough now.
Alright, so it works now, it launches the terminal on login and starts up Neofetch. Although it runs it every time I launch a terminal, it's not that annoying actually.
Thanks for the help!

---

