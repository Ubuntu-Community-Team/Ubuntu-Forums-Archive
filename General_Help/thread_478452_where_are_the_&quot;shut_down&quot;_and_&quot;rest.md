---
title: "where are the &quot;shut down&quot; and &quot;restart&quot; buttons?"
date: 2007-06-19
forum: General Help
---

### Post by friendly2004 on 2007-06-19
hi!

i just wanted to shut down my notebook as i noticed that the "shut down" and "restart" buttons have disappeared.

i've no idea why that is because it was there yesterday and i hadn't made any changes before.

does anyone of you have a clue what the problem might have caused/ may be.


i'm looking forward to your posts.


cheers!
;)

---

### Post by energiya on 2007-06-19
Well I haven't used Gnome or KDE for a long time, but I can give you an alternative way... using the terminal
> 
sudo shutdown -h now

for shutdown, and
> 
sudo shutdown -r now

for restart.
"now" can be replaced with the time. See "man shutdown" for more.

This is to help you until you get this problem sorted...

---

### Post by friendly2004 on 2007-06-19
thanks but that's not solving my problem.

i want to have those buttons to click on ...

how can i restore them?

edit:

sorry, just remembered what i changed...in the synaptics package-management i removed all the entries of the "not installed (left configuration data)". after this my prob. occured. think it must relate to that.but which data was that?difficult one... don't know... maybe someone of you..?

i find this problem in connection with beryl/xgl and stuff. at least i haven't installed it. don't know. is that installed with feisty? hmm... wanna have those buttons...

---

### Post by defishguy on 2007-06-20
This thread appears to solve the problem you mention.

[Missing Buttons!]("http://ubuntuforums.org/showthread.php?p=2832369")

Best of Luck!

---

### Post by Sweet Mercury on 2007-06-20
> **friendly2004 said:**
> hi!

i just wanted to shut down my notebook as i noticed that the "shut down" and "restart" buttons have disappeared.

i've no idea why that is because it was there yesterday and i hadn't made any changes before.

does anyone of you have a clue what the problem might have caused/ may be.


i'm looking forward to your posts.


cheers!
;)

Which environment are you using?

If that doesn't mean anything to you, which "flavor" of Ubuntu are you using: Ubuntu, Kubuntu, Xubuntu, or something else?

---

### Post by friendly2004 on 2007-06-20
@defishguy: i will read and try that.

@sweet mercury: i'm on the gnome env.

---

### Post by Sweet Mercury on 2007-06-20
> **friendly2004 said:**
> @defishguy: i will read and try that.

@sweet mercury: i'm on the gnome env.

I think if the fix from **defishguy** is what you need, this problem is over my head.

I was just going to suggest adding them back to the GNOME panel. Is there a shutdown button on the panel itself, just no button in the exit menu?

---

### Post by friendly2004 on 2007-06-20
@defishguy: i can't find the startxgl.

in /usr/bin only exists a startx but no startxgl.

i don't even know if xgl is installed!!


@sweet mercury: well, there's the quit button (the red one with the power symbol) but in the menu that opens when clicking on it the 2 mentioned buttons are not there.

---

### Post by friendly2004 on 2007-06-20
done it!

on the first page of the link that defishguy posted was the hint!

"In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked."

that was the thing! it was, for some reason, unchecked.


but thanks to y'all for helping!!

---

