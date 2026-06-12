---
title: "Help! My enter key has be reprogrammed!"
date: 2008-03-21
forum: General Help
---

### Post by FearBefore28 on 2008-03-21
Well i'm very new to linux, I just installed ubuntu yesterday and began figuring things out, things like the advanced desktop options available with compiz fusion. I was playing around with the paint fire on desktop options and I accidentally set return(enter) as the hotkey for painting fire, it then proceeded to lock up with fire painting activated so i couldn't even change the hotkey. I shut off my computer and turned it back on, relieved to learn I had regained control of things and switched the hotkey, now however, to my dismay, the computer doesn't seem to recognize the enter key as it used to. It won't make the cursor move down a line in the word procesor or in text boxes, it won't take me to the url i've just types or the google search i've just entered, and most frustrating of all is that it won't enter lines in the terminal. Can anyone help me restore my enter key's functionality?

---

### Post by TheLions on 2008-03-21
go to advanced desktop options, then open "Paint fire on the screen"  options. Go to "Actions" tab and doubleclick on "General" and "Initiate", then press the "Reset To Defaults" brush. Do the same for  "Clear":popcorn:

---

### Post by FearBefore28 on 2008-03-21
no luck V.V the problem isn't with the paint fire, I think it has to do with what the computer recognizes when i push the enter key, the enter key on the number pad works oddly enough

---

### Post by drs305 on 2008-03-21
Does this restore Enter?

```
xmodmap -e "keycode 36 = Return"
```

This would only affect this session, but it may provide temporary relief and give us clues as to where the problem lies.

---

### Post by ibuclaw on 2008-03-21
This is a small terminal app which prints the keycode of the key you input.

Save it to a file called "keycode.c"
and in the terminal type in (in the folder where the file is):

gcc keycode.c -o keycode

Then run the app using "./keycode"
And hit both Enter Keys.
To quit the program, Hit "Escape".

The number "10" should be being printed for both keys (27 for escape).

If not, something weird has happened to change it.
Perhaps resetting your Keyboard Map?

"System>Preferences>Keyboard"

Set it to, lets say Polish Keyboard, then switch it back to your original.

```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <stdlib.h>

int main()
{
	int ch;

	while (ch != 27) {
		ch = getch();
		printf("%d\n", ch);
	}

	return 0;
}

int getch()
{
	struct termios oldt, newt;
	int ch;
	tcgetattr( STDIN_FILENO, &oldt );
	newt = oldt;
	newt.c_lflag &= ~( ICANON | ECHO );
	tcsetattr( STDIN_FILENO, TCSANOW, &newt );
	ch = getchar();
	tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
	return ch;
}

```

---

### Post by FearBefore28 on 2008-03-21
@ drs305, nothing there ><

@ tinivole, wait wait slow down, I am very new to all this and only understand the basics of linux, as well as the terminal itslef >< and restting the keyboard map didn't work, I changed it to polish and back and nothing.

oh and if this helps at all, the enter key will move down a line in text boxes if i hold down the shift key and if i press it without the shift key the cursor just disappears for a second then comes back

---

### Post by FearBefore28 on 2008-03-21
just checked it and if i hold shift while pressing enter, it acts as it should, but if i just hit it it does nothing

---

### Post by drs305 on 2008-03-21
Now I'm curious, so if you will indulge me.
xev is a process that can return the value of a typed key. It opens a small box and in the terminal will return something like the following. This is what my Enter/Return key gives:

KeyRelease event, serial 31, synthetic NO, window 0x3a00001,
    root 0x1a5, subw 0x0, time 3552461312, (684,-240), root: (691,574),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

The line to be investigated would be the third one, the keycode value and what follows. What do you get for a keycode and the stuff in parentheses afterward  (e.g. keycode 36 (keysym 0xff0d, Return)?

To start xev:
```
xev
```

---

### Post by ibuclaw on 2008-03-21
Hmm... Something is messed up there.

Try creating a new user in ubuntu (or login to another user if already present) and test if the return key functions properly. I am thinking that if the issue is assumed to be compiz and you were root at the time (didn't have to enter a password to get to administrative functions) then the problem should only be with your user account.

If this is the case and all works. Migrate all your work to a new account and delete the faulty one.

This is the dummie way to fix this...

If it doesn't fix it. Try it on another Operating System, if you chose to dual-boot.

Hope this helps.
Regards
Iain

---

### Post by FearBefore28 on 2008-03-21
here's what i got when started xev and then hit the enter key

FocusOut event, serial 28, synthetic NO, window 0x3400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x3400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---

### Post by drs305 on 2008-03-21
FearBefore28,

Unfortunately I am not sufficiently proficient in linux to continue troubleshooting your problem. Hopefully someone will be able to read this thread and intrepret what's going on with your machine and provide the solution. 

Best of luck and sorry I wasn't able to help.

---

### Post by FearBefore28 on 2008-03-21
Changing users did the trick, its gonna be a pain to move everything over but the problem has been fixed, thanks to both drs305 and tinivole

---

### Post by ibuclaw on 2008-03-21
Just copy all visible (Lets leave all hidden folders and files alone, as something in one of your user config files caused the problem) files and folders across, should have no difficulty.

It's just setting it up the way it used to be that will probably be the grim of all this.

But in good time it will be it's old self again!

Your Welcome, and I'm glad that worked for you.

Iain

---

