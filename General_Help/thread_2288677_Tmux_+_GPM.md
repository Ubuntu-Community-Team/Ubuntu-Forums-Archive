---
title: "Tmux + GPM"
date: 2015-07-29
forum: General Help
---

### Post by Hiltuspeke on 2015-07-29
Hi.

I am trying out an x-free user interface with my primary machine for my old Asus netbook. Tmux makes multitasking and display usage very efficient, and using GPM to run mouse in terminal makes some tasks (web browsing for example) way easier.

 
 
 Pretty soon after installing GPM I found out that programs that work well with GPM-mouse (Elinks, Midnight Commander, Mcedit etc.) while running in bare console, won't take any commands from mouse while running inside Tmux.  

 
 
 I also have few lines in .tmux.conf that allow me to choose windows and resize panes with mouse. Currently this only works when running Tmux in terminal emulator inside X.  
 [FONT=arial]I don't know if Tmux is compatible with GPM,  and I don't care if I can't use these commands with mouse in console, but my productivity would get a significant boost if I could get GPM-mouse-commands through Tmux to the program running in it.
[/FONT]
[FONT=arial] [/FONT][FONT=arial]Is this even possible, and if so, how?[/FONT]
[FONT=arial] [/FONT][FONT=arial]
 [/FONT]
[FONT=arial] [/FONT][FONT=arial]Here is the piece of my .tmux.conf that has something to do with the mouse.[/FONT]
[FONT=arial] [/FONT][FONT=arial]
 [/FONT]
[FONT=arial]     	 	 	 	[/FONT][FONT=arial]   ```
[/FONT][FONT=arial]setw -g mode-mouse on
set -g mouse-resize-pane on
set -g mouse-select-pane on
set -g mouse-select-window on[/FONT][FONT=arial]
```[/FONT] 
 
  
Any help will be greatly appreciated.

---

