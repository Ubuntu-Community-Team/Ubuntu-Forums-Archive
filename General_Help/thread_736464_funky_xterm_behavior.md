---
title: "funky xterm behavior"
date: 2008-03-26
forum: General Help
---

### Post by queuedvariable on 2008-03-26
So, I've freshly installed ubuntu 7.10.   I'm running e16.7, and any xterms I start work perfectly well except for the final row- where output gets garbled.  Only the top line of pixels of the cursor rez's, and in interactive & n/curses apps, deleting (or ^h'ing) over typed characters does not result in the characters being derez'd (erased), just moves the cursor over them.  The character is logically removed, but newly typed characters print straight over them.

This is a rather bizarre behavior I've not seen before.  Anyone ever seen this?

---

### Post by ibuclaw on 2008-03-26
Could you copy and paste the output in the forum?

Just incase the "garble" as you describe might mean something to someone.
ie: **^[[19** to some people means the F8 key.

And as for ncurses apps.
Not too sure whats going on there.
Perhaps pasting the source of the app you are using may prove to be a bug in the application.

Here's one of my old old apps from when I first began to learn C with ncurses.
```

#include <ncurses.h>
#include <string.h>

int moveleft(int x, int y); int moveright(int x, int y);
int moveup(int x, int y); int movedown(int x, int y);

int row, col;
int pointer = 0; int line[80];
int x = 0, y = 0;

int main()
{
	char intro_one[] = "===========================================================";
	char intro_two[] = "Welcome to TXED. A simple screen editor to jot down ideas.";
	int input, tab;
	char backspace = '\b';

	initscr();
	start_color();
        getmaxyx(stdscr, row, col);
        mvprintw(x, (col - strlen(intro_one)) / 2, "%s\n", intro_one); ++x;
        mvprintw(x, (col - strlen(intro_two)) / 2, "%s\n", intro_two); ++x;
        mvprintw(x, (col - strlen(intro_one)) / 2, "%s\n", intro_one); ++x;
	refresh();
	raw();
	noecho();
	keypad(stdscr, TRUE);

	while (input != 27) {
	getmaxyx(stdscr, row, col);
	input = getch();
		switch (input) {
			case 9  : tab = (y / 8); y = (++tab * 8);
				  move(x, y); break;
			case 10 : if (x < (row - 1))
				  {y = 0; move(++x, y);} break;
			case 27 : clear(); break;
			case 32 : printw(" "); ++y; break;
			case 258 : x = movedown(x, y); break;
			case 259 : x = moveup(x, y); break;
			case 260 : y = moveleft(x, y); break;
			case 261 : y = moveright(x, y); break;
			case 262 : y = 0; move(x, y); break;
			case 263 : printw("%c %c", backspace, backspace);
				   if (y > 0){--y;} break;
/*FunctionKeys*/	case 265 : break; case 266 : break;
			case 267 : break; case 268 : break;
			case 269 : break; case 270 : break;
			case 271 : break; case 272 : break;
			case 273 : break; case 274 : break;
/*Are Not Used Yet*/	case 275 : break; 
			case 276 : input = 27; clear(); break; /*Since Esc is Sluggish*/
			case 330 : printw(" "); ++y; break;
			case 331 : tab = (y / 8); y = (--tab * 8);
				   if (y < 0) {y = 0;} move(x, y); break;
			case 338 : if (x < (row - 1)) {x = x + 5;} if (x > (row - 1)) {x = (row - 1);}
				   move(x, y); break;
			case 339 : if (x > 3) {x = x - 5;} if (x <= 3) {x = 3;}
				   move(x, y); break;
			case 360 : y = (col - 1); move(x, y); break;
			default : if (y < (col - 1)) {printw("%c", input); ++y;}
				  else{y = 0; ++x; if (x > (row - 1)) {y = (col - 1); --x;}
				  move(x, y); printw("%c", input); ++y;}
				  break;

		}
		if (y > (col - 1)) {y = 0; ++x; if (x > (row - 1)) {y = (col - 1); --x; --y;}}
		move(x, y);
		refresh();
	}
	endwin();
	return 0;
}

int moveleft(int x, int y)
{
	if (y >= 1) {mvprintw(x, --y, "");}
	return y;
}

int moveright(int x, int y)
{
	if (y < (col - 1)) {mvprintw(x, ++y, "");}
	return y;
}

int moveup(int x, int y)
{
	if (x > 3) {mvprintw(--x, y, "");}
	return x;
}

int movedown(int x, int y)
{
	if (x < (row - 1)) {mvprintw(++x, y, "");}
	return x;
}

```

It's simply a program that prints user input on the screen.
it doesn't have any form of text formatting, so characters are overwritten on the screen.
If you have the same problem that characters aren't being over written properly with this, I'll have a look into it.

Regards
Iain

---

### Post by queuedvariable on 2008-03-26
It's not garbled in the sense of printing out encodings of keypresses.   It's garbled in the sense of printing one character over another when you delete.   It shows up mostly in interactive apps or curses-invoking things.

For example, when I was using apt to install scrot to take this screenshot:
[IMG]http://staff.washington.edu/lynx/xterm1.jpg[/IMG]

Or when I'm running tf, a visual mode application:
[IMG]http://staff.washington.edu/lynx/xterm2.jpg[/IMG]
(the bottom couple lines have the issue- it doesn't appear with this application, in this terminal, with all the same options, same version of ubuntu, on another machine)

It's weird.

---

### Post by ibuclaw on 2008-03-26
Ah, OK, I get you now.

What version of Ubuntu or Linux do you have?
```
 lsb_release -rd 
```

What version of ncurses do you have?
```
 apt-cache policy ncurses-base 
```

And lastly you said you were using e16.
Have you tried another window manager on the same system such as gnome or e17?

Does this happen in the virtual terminal?

Regards
Iain

---

### Post by queuedvariable on 2008-03-26
I'm running 7.10.   The behavior doesn't occur in gnome, and I don't have e17 so I'm not sure about it.   


ncurses-base:
  Installed: 5.6+20070716-1ubuntu3
  Candidate: 5.6+20070716-1ubuntu3
  Version table:
 *** 5.6+20070716-1ubuntu3 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status

---

### Post by ibuclaw on 2008-03-26
Well, I have the exact same version or ncurses as you. And, like you said, the issue doesn't occur in gnome.

It may be an error specific to e16.

If you prefer the enlightenment look.
Perhaps you should give OpenGEU a try. (previously Geubuntu until they were told to change their name)

They use the exact same repositories as Ubuntu (7.10), with the exception of their own added bespoke repo that has E17 with a few modifications and a mixture of gnome utilities integrated to try and keep the Enlightenment window manager as beta as possible, siince it is still in alpha stages.

I have tried it myself on LiveCD, and it is a very good piece of work. Considering an artist made it.
[http://opengeu.intilinux.com/Home.html]("http://opengeu.intilinux.com/Home.html")

You won't be disappointed.

Regards
Iain

---

### Post by queuedvariable on 2008-03-26
That actually looks kind of cool, thanks.

The really odd thing is, this is one of 3 boxes running basically exactly this configuration, and it's the only one with this problem.     Oh well.    I'll probably try e17 first.

Thanks again,

-qv

---

