---
title: "How to type em dash on Linux?"
date: 2007-04-30
forum: General Help
---

### Post by Aleksandersen on 2007-04-30
Hi,

How do I type [em dash](http://www.fileformat.info/info/unicode/char/2014/index.htm) on KUbuntu 7.02 Linux? On Mac OS 10.4 I enter Alt + -. However this shortcut does not work in KUbuntu.

---

### Post by TheWizzard on 2007-04-30
> **Aleksandersen said:**
> Hi,

How do I type em dash on KUbuntu 7.02 Linux? On Mac OS 10.4 I enter Alt + -. However this shortcut does not work in KUbuntu.

what kind of dash do you mean?

---

### Post by Aleksandersen on 2007-04-30
EM DASH

[http://www.fileformat.info/info/unicode/char/2014/index.htm](http://www.fileformat.info/info/unicode/char/2014/index.htm)

---

### Post by TheWizzard on 2007-04-30
> **Aleksandersen said:**
> EM DASH

[http://www.fileformat.info/info/unicode/char/2014/index.htm](http://www.fileformat.info/info/unicode/char/2014/index.htm)

ok, that one—sorry i'm not a native speaker.

in open office a double dash (--) is automatically replaced.

---

### Post by Aleksandersen on 2007-04-30
Well, I want to use em dash in Konqueror, Opera, KMail, and other applications as well... No keyboard shortcut?

---

### Post by TheWizzard on 2007-04-30
yes, i found it! you have to set your compose key. 

go to 'system settings' -> regional and language -> keyboard layout
select tab 'xkb options'
go to 'compose key position' select 'right alt is compose' and 'apply'

now if you hold the right alt key and pres - 3 times, you have your em dash. &#8212; 

i'm not sure if this works in gtk based apps.

---

### Post by Aleksandersen on 2007-04-30
:popcorn: Thank you!!!

Saved me eight keys to get a em dash! :D

Alt Gr + - - -  = &#8212;

---

### Post by TheWizzard on 2007-04-30
glad i could help. 
cheers

---

### Post by Aleksandersen on 2007-04-30
It works everywhere except in my browser (Opera 9.20, built on Qt).

---

### Post by Jamie Jackson on 2007-06-21
> **TheWizzard said:**
> yes, i found it! you have to set your compose key. 

go to 'system settings' -> regional and language -> keyboard layout
select tab 'xkb options'
go to 'compose key position' select 'right alt is compose' and 'apply'

now if you hold the right alt key and pres - 3 times, you have your em dash. — 

i'm not sure if this works in gtk based apps.

Hmm, I could use the Gnome secret for doing this. Anybody know?

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-06-28
System >> Preferences >> Keyboard >> Layout Options >> Compose key position >> (Check) Right Alt is Compose

&#8212; :)

Okay, so now I can type an em dash. How about an e*n*dash, or some other character? Where do I find other mappings like this?

For instance, in Windows, I could type Alt-0150 to get an en dash. So in Ubuntu, say I know the UTF value is 2013. Is there a keystroke combo that will allow me to enter the UTF value directly?

On the plus side, I'm getting more familiar with Ubuntu's Character Map application, so I can go there in the meantime.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-06-28
I think I'm content now.

If I want an en dash, and I know the UTF value (2013):

[LIST]
[*]ctrl-shift-u (a character will appear that looks like _u_)
[*]2013 (at this point it'll display _u2013_)
[*]enter (hit enter key)
[/LIST]

That leaves you with a – 

Woohoo, another closed issue for me. :)

---

### Post by SmileyChris on 2007-11-14
> **Jamie Jackson said:**
> I think I'm content now.

If I want an en dash, and I know the UTF value (2013):

...

That leaves you with a – 

Woohoo, another closed issue for me. :)
Even easier:

R-alt (compose key) + '--.'

(found [here]("http://www.hermit.org/Linux/ComposeKeys.html"))

---

### Post by Foster Grant on 2008-02-26
> **Jamie Jackson said:**
> System >> Preferences >> Keyboard >> Layout Options >> Compose key position >> (Check) Right Alt is Compose

— :)

Okay, so now I can type an em dash. How about an e*n*dash, or some other character? Where do I find other mappings like this?

For instance, in Windows, I could type Alt-0150 to get an en dash. So in Ubuntu, say I know the UTF value is 2013. Is there a keystroke combo that will allow me to enter the UTF value directly?

On the plus side, I'm getting more familiar with Ubuntu's Character Map application, so I can go there in the meantime.

Thanks,
Jamie

Thank you, sir. This answered a question I've had for some time. 8)

(Posted only so the guy who found the answer could have my thanks noted in his user profile. :) )

---

### Post by stinkinrich88 on 2008-06-17
This isn't working for me... I'm a gnome user with Hardy (UK layout)

---

### Post by Jamie Jackson on 2008-06-18
> **stinkinrich88 said:**
> This isn't working for me... I'm a gnome user with Hardy (UK layout)

Which one are you trying, mine from post 12 or SmileyChris's from 13? I think mine is fairly clear, but it took me a few tries with SmileyChris's:

First, check to make sure your compose key is the right Alt key (see post 11), then:
Type the following:
[LIST=1]
[*][FONT="Courier New"][SIZE="7"][COLOR="Red"]<R-Alt>[/COLOR][/SIZE][/FONT] (The right "Alt" key)
[*][FONT="Courier New"][COLOR="Red"][SIZE="7"]--[/SIZE][/COLOR][/FONT] (the hyphen key, next to the zed; type it twice)
[*][FONT="Courier New"][COLOR="Red"][SIZE="7"].[/SIZE][/COLOR][/FONT] (the dot/period character, next to the question mark)
[/LIST]

The en-dash will only appear after hitting the dot key.

Hope this helps.

Thanks,
Jamie

---

### Post by stinkinrich88 on 2008-06-18
hmmmm, nope, still nothing. Here is exactly what I do:

I did this previously: 

menu->system->preferences->keyboard->Layout(tab)->layout options->compose key position (expand)-> ensure "Right alt is compose" is the only box ticked. 

Then I open gedit, hold down my right alt key (the one with "Alt Gr" printed on the key), type two hyphens (using either the hyphen above my P key or the minus sign on the numpad), press the full-stop key (period) then release the alt key. 

All that happens is --. appears, just as if I hadn't been holding the alt key.

---

### Post by stinkinrich88 on 2008-06-20
...reckon I should report a bug or post a new question?

---

