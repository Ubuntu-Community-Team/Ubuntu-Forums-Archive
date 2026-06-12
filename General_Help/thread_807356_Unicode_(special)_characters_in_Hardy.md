---
title: "Unicode (special) characters in Hardy"
date: 2008-05-25
forum: General Help
---

### Post by frogitts on 2008-05-25
I know there's a few other threads about this, but none of them seem to have been made after Hardy got in the works, and I can get any posted solutions to work. Here's what I've tried, all in OpenOffice Writer, most in the terminal and firefox as well:

Ctrl+Shift+0222
Ctrl+Shift+0222 on the numpad
Ctrl+Shift+U+0222, on and off the numpad
Ctrl+Shift,U, 0,2,2,2 - on and off the numpad (hold down Ctrl+Shift, then type U0222, then let off Ctrl+Shift)
Ctrl+Shift+222, on and off
Ctrl+Shift+U222, on and off
Alt+0222, same
Alt+U0222, same

in each case, as soon as I type the "0" (zero), it changes my Greek text to a Latin font. As soon as I type a 2 on the numpad, it highlights one line beneath. So what is the right key combination? How can I type a Unicode character in Hardy?

---

### Post by tacutu on 2008-05-25
a round-about solution is to go to applications-accessories-character map and select your symbols from there... not very fast though...

another way I can think of is to have scim set up and use the "raw code" input method.

---

### Post by frogitts on 2008-05-26
Yeah, the long inconvenient roundabout is not what I'm looking for, that's easy to find. The SCIM method sounds interesting though, I'll give it a shot. 

Am I to understand then, though, that Ubuntu has no built-in support for typing unicode characters? Because if not, that is a very basic thing that needs to happen, and definitely helps accessibility for those of us who don't want to deal with the details but just have a function. I know that I was fine with doing Alt+0223 for an ß for years in a certain other operating system before I found a workaround that let me use Ctrl+Shift+s. Of course, this time the problem is typing a small superscript t-shaped thing used in critical editions of the Greek text of the Christian New Testament, and I'd love to be able to just type Alt+0222 (or 00df, whatever it happens to be) or something similar to insert it. 

But I will give the SCIM solution a try when I get back to my computer.

---

### Post by engine on 2008-06-26
Don't know where I found the information, but I have a note on my office wall:
[LIST=1][*]press and hold down Shift and Ctrl together
[*]type in u, followed by the four-character unicode value for the character
[*]release Shift and Ctrl[/LIST]

Here's a fraction (00bd) to show it in action: ½

Doesn't work in Open Office, which has its own 'insert symbol'

hth

---

### Post by simosx on 2008-08-30
Just to add here that Ctrl+Shift+u works when you use the default "input method" in Ubuntu, which is called "GTK+ Input Method".

You are not using the default input method if either

1. you have enabled SCIM, and SCIM is active.
2. you have set the GTK_IM_MODULE variable to something like "xim"
3. you use KDE (QT-based applications)

---

