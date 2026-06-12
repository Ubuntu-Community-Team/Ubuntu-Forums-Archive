---
title: "VT320 Terminal Emulation"
date: 2006-11-23
forum: General Help
---

### Post by LineOf7s on 2006-11-23
I've resisted 'til now, but Google's doing my head in. ](*,)  I'm happy to use any terminal emulation proggy that'll do the job (gnome-terminal, xterm, eterm - whatever), but this is all I need:

[LIST=1]
[*]VT320 terminal emulation
[*]A 'full-screen' terminal (ie doesn't sit in the top-left corner with 9pt fonts when maximised)
[*]The ability to remap the keys (through any method).  I need to use the top row of the numeric keypad as PF1 - PF4.  This is essential.
[/LIST]

If I can manage this, I can commission a dozen computers running Ubuntu to replace a bunch of old 'dumb' terminals.  The alternative is for head office to install Microsoft thin clients - and I'd rather go with Ubuntu, obviously.

Pretty please?!  :-D

---

### Post by LineOf7s on 2006-11-23
Help me Obi-Wan.  You're my only hope!


I'll settle for a guide on how to remap keys.

---

### Post by po0f on 2006-11-24
LineOf7s,

I googled it and got [BTERM](http://www.bbbs.net/) as a possible vt320 terminal emulator (hint: scroll to the bottom of the page).  They have a Linux port, but it looks like the web site hasn't been updated in a while.

As for remapping keys, try [xmodmap](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html).

---

### Post by LineOf7s on 2006-11-24
Thankyou po0f.  BTerm is one of my conquests already - sadly, it wasn't up to the task (and unfortunately I can't remember exactly why - but I know it wasn't).

I've heard mention of xmodmap and thought I'd moved on from it, but I can't remember it and the webpage looks unfamiliar so I'll give it a good going-over.

Thankyou.  Fingers crossed.

---

### Post by po0f on 2006-11-24
LineOf7s,

Does [C-Kermit](http://www.columbia.edu/kermit/index.html) fit the bill?  From what I skimmed over on the web site, it looks like it does vt320 emulation.  As I understand it, Kermit isn't free (as in speech) though, but it is in the [multiverse repos](http://packages.ubuntu.com/edgy/comm/ckermit).

---

### Post by LineOf7s on 2006-11-24
Well C-Kermit's one I haven't tripped over before.  I'll check it out right away.  There's also PowerTerm Interconnect that works 'out of the box', but it's $US85 and would be a hard sell when I'm trying to spruik the benefits of a free (as in speech and beer) OS.

Especially since there are a million billion terminal emulation programs available for Linux, and most of them do exactly what I'm looking for **except for the four keys at the top of the numeric keypad acting like the PF1 - PF4 keys**.  I've found a page that tells me exactly how to remap the keys for Xterm [http://www.jmknoble.net/old-stuff/xterm-keys.html]("http://www.jmknoble.net/old-stuff/xterm-keys.html") but I can neither bend Xterm to my will nor adapt the instructions to any other terminal proggie (gnome-terminal for example).

It's just frustrating knowing the answer's out there somewhere - sooo close - but I can't find it.  And it seems to be one of the few things the general Linux guru just hasn't needed to do before.

But back to C-Kermit.  I do appreciate your help, po0f.  :D

---

### Post by po0f on 2006-11-24
LineOf7s,

What functions do those keys serve?  I can't seem to figure out what they do.  I'm currently browsing [vt100.net](http://vt100.net/) looking for an answer, if you haven't stumbled across this site yet.

---

### Post by LineOf7s on 2006-11-25
We're all familiar with function keys on a PC keyboard:  F1 - F12.  VT320 (and later) terminals have these as well (up to F24 in fact), but they also have **P**F1 - **P**F4.  These keys - when run on a PC keyboard through an emulator - are typically the Num Lock, /, * and - keys running along the top of the numeric keypad.  

As with function keys, they're application-specific in their actual use - it just so happens that on the system used at work they perform vital functions that aren't replicated elsewhere.  Any terminal emulation program in Linux that doesn't have these keys mapped properly means I can use it - which means I can't use Linux.

I know they **can** be remapped - xterm remapped using the information on the link I provided works a treat - but I've just got to work out how to remap them for a terminal emulation program more suitable than xterm.

Of course, the other possibility is to get xterm to work full-screen...

PS:  I haven't checked out C-Kermit yet because I'm having issues with connecting to the work VPN thru Linux - I won't bore you with that here though.  ASAP C-Kermit will be checked out.

---

### Post by po0f on 2006-11-25
LineOf7s,

If you can post the escape sequences these keys should emit (don't know terminal emulation lingo), I can probably hack together something that will work with rxvt-unicode (the emulator I use).

[EDIT]

In the link you posted, I saw remaps for KP_add, KP_subtract, KP_decimal, and KP_enter, which are the right-most keys on the keypad (not counting the decimal).  Are these correct?  You said the top 4 keys are what you are interested in remapping.

---

### Post by mcduck on 2006-11-25
> **LineOf7s said:**
> 
Of course, the other possibility is to get xterm to work full-screen...

That should be possible. I just press ctrl-alt-enter to make Gnome-terminal fullscreen with no panels or window borders visible (fullscreen, not maximized), and I just tried and it works just fine with xterm too. Actually it works with about every program... You should be able to create a shortcut for making apps fullscreen in System/Preferences/Keyboard Shortcuts.

---

### Post by LineOf7s on 2006-11-25
> In the link you posted,
A thousand apologies. :(  I went to that link to point out to you the exact bit I meant... and it turned out not to be the link I thought it was.  I was actually thinking of **this** link - and here you'll see references (in the first and third examples) to Num Lock, Divide, Multiply and Subtract - the top four keys of the numeric keypad.

[http://dickey.his.com/xterm/xterm.faq.html#how2_fkeys]("http://dickey.his.com/xterm/xterm.faq.html#how2_fkeys")

Now while this seems comprehensive and seems to answer my question most thoroughly, I haven't worked out how to adapt it for use by anything but xterm.

Of course, with mcduck's advice, I may not need to - I'm about to reboot into Ubuntu and see what happens when I full-screen Xterm.  Thankyou for the tip - I didn't know about that key combo.

---

### Post by LineOf7s on 2006-11-26
> I just press ctrl-alt-enter to make Gnome-terminal fullscreen...and I just tried and it works just fine with xterm too.  Actually it works with about every program...

Really?  I just tried this out on Edgy and not only does it not work in Gnome-terminal or xterm, but I'm yet to find **any** application it works in.  Could there be something else installed that provides this functionality?  Are you running Dapper perhaps and it's missing from Edgy?

Google shows me a patch I can compile into xterm to get it to go fullscreen, but I'm yet to find something as straightforward as what you've described, sadly.

---

### Post by po0f on 2006-11-26
LineOf7s,

To make gnome-terminal "full-screen" (there's still a menu bar at the top), hit F11.

Is it the initial size of the terminal window that is bothering you?  Or does it actually have to be fullscreen?  You can add the following entry to ~/.Xdefaults to increase xterm's window size:
```
[FONT="Courier New"]XTerm*geometry: 120x50[/FONT]
```
Geometry is in columns by rows format.  You'll have to close the current xterm window and open a new one for the new setting to take effect.

---

### Post by LineOf7s on 2006-11-26
Alrighty - a moment of inspiration caused me to check the Keyboard Shortcuts preference.  'Toggle Fullscreen' was disabled.  It's now enabled as CTRL-ALT-Enter.

Trouble is, all it does is make the window fill the screen, but the 'terminal' itself is still snuggled up in the top left corner with its teensy 12-point font (or whatever).  Whilst I appreciate this is normal behaviour, my ultimate goal is to have the font be big enough (even if it's manually set if need be) to fill the screen so that to all intents and purposes the computer seems to have no other function but to act as the terminal it's emulating.  No windows, no desktops etc etc

I realise the longer this drags on the more whiny I'm sounding, and I'm really trying to make it work, but it's amazing me that it's so difficult to find what I want unless I buy an $US85 commercial application.

---

### Post by LineOf7s on 2006-11-26
Finally got around to checking out ckermit (and gkermit, the GPL version).  Sadly, no.  From the help files:

> SET TERMINAL TYPE ...
  This command is not available because this version of Kermit does not
  include a terminal emulator.  Instead, it is a "semitransparent pipe"
  (or a totally transparent one, if you configure it that way) to the
  computer or service you have made a connection to.  **Your** console,
  workstation window, or the **terminal emulator** or terminal from which you
  are running Kermit **provides the emulation**.


*bold added to emphasise what I'm looking for.  :)

---

### Post by stylishpants on 2006-11-27
> **LineOf7s said:**
> Trouble is, all it does is make the window fill the screen, but the 'terminal' itself is still snuggled up in the top left corner with its teensy 12-point font (or whatever).  Whilst I appreciate this is normal behaviour, my ultimate goal is to have the font be big enough (even if it's manually set if need be) to fill the screen so that to all intents and purposes the computer seems to have no other function but to act as the terminal it's emulating.  No windows, no desktops etc etc


Konsole and gnome-terminal are both very good at providing the look that you want.  It is very simple to change the default font size if you change the font options through the menus of these programs.

Both also provide keyboard shortcuts for resizing your fonts.  In gnome-terminal, Ctrl-Shift-+ makes the font bigger, Ctrl-Minus makes the font smaller.

To have a totally clean look in gnome terminal, you have to turn off the scroll bar (Edit->Current Profile->Scrolling) and the menu bar (View->Show Menubar).

---

### Post by LineOf7s on 2006-11-28
Thankyou guys for all your help thus far.  With your guidance, and a metric crapload of bashing my head against a wall ](*,)  I have thus far achieved the following:
[LIST]
[*]Remap the keys to what I need them to do (via xkeycaps).  YAY! This was a showstopper.
[*]Start gnome-terminal automatically (by adding an entry to the Startup Programs tab in Sessions)
[*]Used the --geometry parameter to almost fill the screen using the chosen font
[*]Have gnome-terminal start with the profile I want by default.
[/LIST]

I could probably 'get by' with this, but since it's going to be used by computer illiterates (no offence to them), I want to make it as transparent and robust as possible.  With that in mind, does anyone have any tips how to:

[LIST]
[*]Get gnome-terminal to start 'full-screen' (ie, what it does when you perform the keyboard shortcut to make it go full-screen).  If it can do it 'manually', surely there's a script or something I can write that'll to it automatically?
[*]Somehow password protect it so that you need a password (root or otherwise) to close the application (this could be tough).
[/LIST]

If I could get either of those happening (listed in order of preference), I could sleep easy knowing it was set up the best it can be (for now).  I humbly await a response.

---

### Post by LineOf7s on 2006-12-03
For those, perhaps years from now, searching this forum for an answer to the eternal question of how to get gnome-terminal to start full-screen and finding that the man pages for it mention nothing, a random running of *gnome-terminal --help* mentions the *--full-screen* option.  In my particular application it seems to be happening a little intermittantly (sometimes not actually opening full-screen but some full-screen/windowed hybrid), but it seems to be stable at the moment, and when it works, it works great!

---

