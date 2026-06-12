---
title: "No more alt+[left arrow] in Firefox 2.0??"
date: 2006-10-28
forum: General Help
---

### Post by wilberfan on 2006-10-28
Is it just me, or has anyone else noticed that you can no longer go "back" or "forward" by hitting alt + arrow keys?

I didn't realize how often I used that shortcut till today!  

Or is it an Edgy thing??  (I clean-installed today.)  Did something get turned-off, or...?

---

### Post by marcozs on 2006-10-28
works fine for me...

---

### Post by rfruth on 2006-10-28
works for me :)

---

### Post by wilberfan on 2006-10-28
Hmmmm......  What could have gotten turned off??   It doesn't work on my 32 *or* 64 bit box...   I'm using the 32-bit Firefox in both cases...

Firefox 2.0 under Windows XP is fine...

---

### Post by beerfan on 2006-10-28
> **wilberfan said:**
> Is it just me, or has anyone else noticed that you can no longer go "back" or "forward" by hitting alt + arrow keys?

I didn't realize how often I used that shortcut till today!  

Or is it an Edgy thing??  (I clean-installed today.)  Did something get turned-off, or...?

Works fine for me with Mozilla Firefox 2.0 in Dapper.

---

### Post by meng on 2006-10-28
I thought that alt-left arrow had stopped working, but I find that left_alt-left arrow still works, whiel right_alt-left arrow doesn't (it used to though). I wondered if this was a quirk of my notebook keyboard (i.e. not a standard 104/105-key keyboard) but changing keyboard layout/settings doesn't fix the problem.

---

### Post by garretwp on 2006-10-28
I have the same issue. I tried adjusting the keyboard layout with no luck. It is kind of annoying that I can not use it. I wish my buttons on my Logitech mouse would work to be able to move back and forth on the web.

- Garrett

---

### Post by wilberfan64 on 2006-10-28
> **meng said:**
> I thought that alt-left arrow had stopped working, but I find that left_alt-left arrow still works, while right_alt-left arrow doesn't (it used to though). I wondered if this was a quirk of my notebook keyboard (i.e. not a standard 104/105-key keyboard) but changing keyboard layout/settings doesn't fix the problem.

Ah HA!  You're right!!   The left-alt + left arrow DOES still work!  It's the RIGHT-alt + arrow key that doesn't...    

How odd...

---

### Post by sn0n on 2006-10-29
See here. 
System > Preferences > Keyboard. 

Change as so. And try again. 
This was rather annoying and did take me about 15 min to figure out..

---

### Post by wilberfan64 on 2006-10-29
> **sn0n said:**
> See here. 
System > Preferences > Keyboard. 

Change as so. And try again. 
This was rather annoying and did take me about 15 min to figure out..

Well, you got my hopes up.    Didn't work.  [-(

---

### Post by Krash1201 on 2006-11-01
I am confirming this problem on an IBM T42p, but the suggested keyboard preference change fixes the problem.  Thank goodness.

---

### Post by rich90usa on 2006-11-05
Seems something got added into the xorg.conf file keyboard section with Edgy. The edit to in the keyboard preference mentioned above fixes it by overriding the setting. However, for people not using gnome that preference pane isn't available(I use Xubuntu). In that case the only fix is to edit the xorg.conf file by hand.

```

sudo pico /etc/X11/xorg.conf

```

Find
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

```

and comment out the XkbOptions line to make it look like this:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
##      Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

```

Then just hit "Ctrl + O" and Enter to save the edit in Pico
Don't forget to restart X so that your using the new settings. Do that by restarting the computer or saving your work and hitting Ctrl+Alt+Backspace

[quote=http://www.gnome.org/learn/users-guide/latest/prefs-keyboard.html]
Third level choosers

    A third level key allows you to obtain a third character from a key, in the same way that pressing Shift with a key produces a different character to pressing the key alone.

    Use this group to select a key you want to act as a third level modifier key.

    Pressing the third-level key and Shift produces a fourth character from a key.

    The third and fourth level characters for your keyboard layout are shown in the Keyboard Indicator Layout View Window.
[/quote]

I'm guessing that firefox v.2 can't handle a third level right alt key thus it gets ignored. If someone did require a third level alt key, I would reccomend changing the line to:
```

Option		"XkbOptions"	"lv3:lalt_switch"

```
Making it the left alt that is third level and thus preserving that functionality if needed.


Does anybody know the best place to submit this suggestion to? Firefox for not supporting third level or Ubuntu for implementing this "feature"?

---

### Post by wilberfan64 on 2006-11-05
That's interesting...   The keyboard preference edit (via the menu) did NOT work for me--but the xorg.conf edit DID.

Not sure what that means, but I'm grateful to have my right-alt key back.  Thanks!

---

### Post by garretwp on 2006-11-05
Neither of these worked for me. 

- Garrett

---

### Post by rich90usa on 2006-11-06
> **garretwp said:**
> Neither of these worked for me. 

- Garrett

One thing I forgot to put in my post was to restart xorg(restart the whole computer or save what your working on and hit Ctrl-Alt-Backspace). That's about all I can think of.

---

### Post by garretwp on 2006-11-06
I have restarted the x server and rebooted the machine after modifying the xorg.conf file with the adjustments and still can not get it to work! :(

- Garrett

---

### Post by rich90usa on 2006-11-07
> **garretwp said:**
> I have restarted the x server and rebooted the machine after modifying the xorg.conf file with the adjustments and still can not get it to work! :(

And you probably have the standard American qwerty keyboard in the PS/2 too huh? Either way, the one thing I would do is dive into the documentation for the xorg keyboard settings and mess around. Unfortunatly I can't replicate your problem on mine.

Another thing to do would be to install an extension in firefox to remap the hotkeys. That was my original plan, however the only extension I found on the mozilla site didn't work properly in FF2.0 yet.

---

### Post by garretwp on 2006-11-07
This is what my xorg.conf looks like for my keyboard section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
#       Option          "XkbOptions"    "lv3:ralt_switch"
EndSection


- Garrett

---

### Post by rich90usa on 2006-11-08
> **garretwp said:**
> This is what my xorg.conf looks like for my keyboard section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
#       Option          "XkbOptions"    "lv3:ralt_switch"
EndSection


Try this:
```
Option		"XkbOptions"	"lv1:ralt_switch"
```

I tried it on mine and the alt-left worked so this might work for you by forcing lv1.

---

### Post by grumpymole on 2006-11-21
@rich90usa

Thanks!  Uncommenting the line, as per post #12, worked for me.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by xxJimboxx on 2006-11-22
> **wilberfan64 said:**
> Well, you got my hopes up.    Didn't work.  [-(

I had the same problem, and finally figured it out.  Go to System -> Preferences -> Keyboard ->Layout Options -> Alt/Win behavior.  Change it from "Default" to "Alt and Meta are on the Alt keys".  Hope this works for you.

---

### Post by mkoyle on 2007-01-19
Changing my keyboard layout fixed it form me.  The L3 thing can possibly stay the same.  Just going to System-->Preferences-->Keyboard-->Layouts  and changing the Keyboard Model to "Generic 104-key PC"  Haven't found the explanation for it yet, but this fixed it for me.  

I changed the XkbModel to PC104 (instead of PC105) line in my xorg.conf so it is correct for other users on my system.

--Matthew

---

### Post by o4tuna on 2007-02-03
[SIZE="7"][COLOR="Red"]THANK YOU![/COLOR][/SIZE]

Man that was irritating...

---

### Post by borkabrak on 2007-02-20
After much fiddling with all the ideas on here, including using xmodmap and altering my xorg.conf, I finally reached a solution that worked for me.

It turns out that all I really had to change was the Keyboard preferences, like so:

[SIZE="4"]1.) Go to System -> Preference -> Keyboard[/SIZE]

[SIZE="4"]2.) Activate the "Layout Options" tab.[/SIZE]

This will show you several expandable/collapsible sections you can play with.  Anything that has something active (checked) in it will be in **bold text** instead of normal text.

[SIZE="4"]3.) Uncheck everything you can.  [/SIZE]

Notice that under the section "Third level choosers", you *can't* uncheck everything.  Something must remain active.  All you have to do is make sure that all the options having to do with Alt keys are unchecked, specifically the one that says "Press Right Alt key to choose 3rd level".

I also noticed that if you have checked "Press Right Ctrl to choose 3rd level", than the right control key no longer works as normal.  

Since you do have to have something checked, I went with:

[SIZE="4"]4.) Activate the option: "Press Menu key to choose 3rd level"[/SIZE]

I suppose one day I'll figure out what 3rd level is and why I might want it.  (The help button was less than helpful).

To reiterate, that one menu "System->Preferences->Keyboard" was *all* I had to mess with -- my xorg.conf has the "lvl3:ralt_switch" *un*commented.  My list of startup scripts does *not* contain any form of "xmodmap".  Neither does my .zshenv or .zshrc (which are the same thing as .bashrc and .bash_profile, for most of you).

I hope this helps somebody.  Good luck, guys.

Oh.. and can someone explain what's going on with the "3rd level" stuff in the first place, and why the machine insists I have to have it?

Thanks,

-borkabrak

---

### Post by P235 on 2007-02-24
Is there a similar gui solution for Kubuntu users?

---

### Post by russianbandit on 2007-02-27
> **borkabrak said:**
> After much fiddling with all the ideas on here, including using xmodmap and altering my xorg.conf, I finally reached a solution that worked for me.

It turns out that all I really had to change was the Keyboard preferences, like so:

[SIZE="4"]1.) Go to System -> Preference -> Keyboard[/SIZE]

[SIZE="4"]2.) Activate the "Layout Options" tab.[/SIZE]

This will show you several expandable/collapsible sections you can play with.  Anything that has something active (checked) in it will be in **bold text** instead of normal text.

[SIZE="4"]3.) Uncheck everything you can.  [/SIZE]

Notice that under the section "Third level choosers", you *can't* uncheck everything.  Something must remain active.  All you have to do is make sure that all the options having to do with Alt keys are unchecked, specifically the one that says "Press Right Alt key to choose 3rd level".

I also noticed that if you have checked "Press Right Ctrl to choose 3rd level", than the right control key no longer works as normal.  

Since you do have to have something checked, I went with:

[SIZE="4"]4.) Activate the option: "Press Menu key to choose 3rd level"[/SIZE]

I suppose one day I'll figure out what 3rd level is and why I might want it.  (The help button was less than helpful).

To reiterate, that one menu "System->Preferences->Keyboard" was *all* I had to mess with -- my xorg.conf has the "lvl3:ralt_switch" *un*commented.  My list of startup scripts does *not* contain any form of "xmodmap".  Neither does my .zshenv or .zshrc (which are the same thing as .bashrc and .bash_profile, for most of you).

I hope this helps somebody.  Good luck, guys.

Oh.. and can someone explain what's going on with the "3rd level" stuff in the first place, and why the machine insists I have to have it?

Thanks,

-borkabrak

This helped me out. Thanks a bunch.

---

### Post by robin. on 2007-03-01
> **wilberfan64 said:**
> Ah HA!  You're right!!   The left-alt + left arrow DOES still work!  It's the RIGHT-alt + arrow key that doesn't...    

How odd...

How is CTRL + F4 (close present tab) working out for you?

Along with the (left)ALT-Left Arrow not working, I'm not getting the (left)CTRL + F4 to close my tabs either.

It may be helpful to note that I do not have a (right)CTRL key as I'm typing on a laptop with Xubuntu, 6.06 installed.

---

### Post by CodeNosher on 2007-04-22
Yes!!  I thought for sure it was my laptop.  I had sent it in to get fixed three times over a different issue and they ended up sending me a 'new' replacement.  I was beginning to think this was a busted keyboard.  Thanks for the post.

---

