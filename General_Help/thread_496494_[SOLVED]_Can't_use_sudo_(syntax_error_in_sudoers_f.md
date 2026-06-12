---
title: "[SOLVED] Can't use sudo (syntax error in sudoers file)"
date: 2007-07-09
forum: General Help
---

### Post by Espreon on 2007-07-09
Big problem I can't use sudo! This is what I get when I use any command with sudo in it:

spanek@spanek-laptop:~$ sudo
>>> sudoers file: syntax error, line 20 <<<
sudo: parse error in /etc/sudoers near line 20

---

### Post by smoker on 2007-07-09
hi, have you checked the file, sudoers?

here is a copy of mine, sudo works fine with me,

---

### Post by Espreon on 2007-07-09
No, but I would like to know what can cause this? Also how do I open the file, I tried opening it with gedit but no avail.
And please give me another solution rather than reinstall (maybe I will since I broke Wine-Doors).

---

### Post by aysiu on 2007-07-09
This link should help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Espreon on 2007-07-10
Did not help at all. A solution would be nice. Also did you even read my post?

---

### Post by aysiu on 2007-07-10
Did you read mine?

Yes, I read your post. There's a syntax error in your /etc/sudoers file.

The link I gave you not only tells you how to edit the /etc/sudoers file if it's corrupted--it also gives you exactly what your /etc/sudoers file should look like after you edit it.

"Did not help at all" doesn't help at all. Can you explain what you did, where you got an error, and what the exact error was?

---

### Post by Espreon on 2007-07-10
When I entered the command visudo, I don't know how 2 save changes or anything.

---

### Post by aysiu on 2007-07-10
Can you try **Control-X, Y**, and **Enter** to save?

---

### Post by Espreon on 2007-07-10
Well there is something different than the example on the link, the difference is that there is a truecrypt line in it, which I believe allows TrueCrypt to be useable, but I will put your knowledge to use later.
As for the enter button I think I tried that in the file but just gave me a very annoying beeping noise. Oh and BTW is there any way to disable this infernal beeping?!?

---

### Post by Kodfish on 2007-07-11
what error does it give after beeping? does it give an error?

---

### Post by Espreon on 2007-07-11
It is no error I believe, just the terminal beeping there are also blue ~ characters after the truecrypt line, when I try to go beneath them it beeps! Oh the horror!

---

### Post by Kodfish on 2007-07-11
hmmmm... does su still work? try: ```

su
visudo

```

---

### Post by aysiu on 2007-07-11
I'm not sure what you mean about a truecrypt line. I'm using Feisty right now, and this is what my /etc/sudoers file looks like: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` Perhaps a TrueCrypt line gets in there if you install TrueCrypt?

I've attached screenshots of the save process after you've made changes to the file.

---

### Post by Espreon on 2007-07-11
No su does not work. When I enter my password it gives me this:

spanek@spanek-laptop:~$ su
Password: 
su: Authentication failure
Sorry.
spanek@spanek-laptop:~$ su vidsudo
Unknown id: vidsudo
spanek@spanek-laptop:~$

Also I have TrueCrypt and Forcefield installed.

In addition all I entered was visudo

Do I hafta enter nano /etc/sudoers ? Or nano visudo?

Also Where did you get that terminal backround? It is pretty sweet if you ask me.

---

### Post by aysiu on 2007-07-11
Okay, here's the problem. You have to boot into recovery mode to make these changes.

As long as your /etc/sudoers file is screwed up, you won't be able to *su* or *sudo* from regular mode.

Refer back to the link I posted earlier on how to boot into recovery mode.

---

### Post by Espreon on 2007-07-11
Thanks for the link, I got it solved, apparently all I needed to do was make a space between something.

Now about that terminal backround, how do I get it?

---

### Post by aysiu on 2007-07-11
It's actually just the regular Ubuntu background with the terminal transparent so you can see it.

In the terminal, go to Edit > Profiles > Edit > Effects > Transparent Background

---

