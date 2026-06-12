---
title: "Keyboard Shortcut to Enable/Disable Compiz on Gutsy?"
date: 2008-03-13
forum: General Help
---

### Post by crazygopedder on 2008-03-13
Ok, I finally have Ubuntu 7.10 running perfect on my T43.  I have a couple questions about compiz: Is there any keyboard shortcut to enable/disable desktop effects?  Could I make one somehow?  I know there is the compiz-fusion icon, but I see no point in it, it's just as quick (for me) to just open up appearance settings and do it from there.  IMO a keyboard shortcut would be the most convenient for switching off compiz for gaming.  If anybody has the same idea or has done this I'd greatly appreciate any help. :)

---

### Post by ibuclaw on 2008-03-13
Not too sure about keyboard shortcuts, I had a small sift through "gconf-editor" but couldn't see any key bindings that would allow it. But if you want to try and look yourself, here's where to look:

apps
=>compiz
=>metacity

Alternately, if your not fussed by not having keyboard shortcuts, you could have two launchers on your desktop.

```
 compiz --replace & 
```
To switch to compiz (effects galore), and

```
 metacity --replace & 
```
To switch to metacity (no effects).

And here are two screenshots I made just now. Showing both launchers, both desktop environments and the command (because I'm kind :) )
[[IMG]http://img358.imageshack.us/img358/3213/compizji3.th.png[/IMG]](http://img358.imageshack.us/my.php?image=compizji3.png)

[[IMG]http://img358.imageshack.us/img358/65/metacitywn4.th.png[/IMG]](http://img358.imageshack.us/my.php?image=metacitywn4.png)

Iain

---

### Post by ibuclaw on 2008-03-13
Okay, I have been pondering this a while, and after doing some tests, I have made a (very alpha) program that will allow you to switch between Compiz and Metacity.

Drawbacks at the moment are:
    - Requires a terminal to be open, and you have to have the window selected in order to do anything.
    - Current interface is NCurses, I have made it clean, so no worries there.But losing the terminal is the first thing I'll do before beta-ing it.
    - Optimisations are a must, whichever way I look at it. I would like to loose the "system" calls, if at all possible, need to find a better way of executing the binaries.

But if anyone reading this wants to commit a patch, fix or improvement (getting rid of the ncurses dependancy and having it intergrated into gnome would be great). Please help all you want! And message me back the fix through my account on the forums.

Here's what I've done so far:
```

/*	Getting a start on the working environment
	ie: The Program only responds to the keycode inputs:
	   Ctrl+Alt+M = Metacity On.
	   Ctrl+Alt+C = Compiz On.
	   Ctrl+Alt+H = Display Help Text.
	   Ctrl+Alt+X = Close App.	
	And no other key can interfere on its input scan.	*/

#include <stdlib.h>
#include <ncurses.h>
#include <string.h>

int main()
{
  initscr();
  raw();
  noecho();
  
  int length, width;
  char title[] = "Compiz/Metacity Switcher Alpha v0.0.5";
                    /*Change this as improvements are made*/
  
  int key; /*This integer ensures that both Ctrl+Alt are being pressed (First integer is 27)*/
  int ch;
    
  while (key != 26) {
    getmaxyx(stdscr, length, width);
    mvprintw (0, (width - strlen(title)) / 2, "%s", title);
    move (0, 0);
    key = getch();

    if (key == 27) {
      clear();
      mvprintw (0, (width - strlen(title)) / 2, "%s", title);
      ch = getch();

      if (ch == 10) {
	mvprintw (2, 0, "Metacity On");
	system("metacity --replace &");
      }
      if (ch == 3) {
	mvprintw (2, 0, "Compiz On");
	system("compiz --replace &");
      }    
      if (ch == 8) {
	mvprintw (2, 0, "Ctrl+Alt+M = Switch to Metacity.");
	mvprintw (3, 0, "Ctrl+Alt+C = Switch to Compiz.");
	mvprintw (4, 0, "Ctrl+Alt+H = Display Help.");
	mvprintw (5, 0, "Ctrl+Alt+X = Quit.");
      }
      if (ch == 24) {
	--key;
      }
    } else {
      ch = 27;
      key = 27;
      clear();
    }
    refresh();
  }
  
  endwin();
  return 0;
}

```

As I said, it is very alpha. Yet in a good condition to use on a daily basis (Just needs work on the interface). But for those who want to switch fast and effective, use Launchers for now.

To compile, use this
```
 gcc name.c -o name -lncurses 
```
Where name is the name that you want to give it, say, "compiz-switch" for example.

Regards
Iain

---

### Post by crazygopedder on 2008-03-13
Thanks guys.  I just made 2 launchers, that works great for me.  I'm surprised I didn't think of that lol.  And to to tinivole, that's awesome you're working on a program.  I wish you the best of luck, it would be a sweet addition to Ubuntu.

---

### Post by alan_cv86 on 2008-05-27
You saved my computer from reinstalling again. Thank you very much!

---

