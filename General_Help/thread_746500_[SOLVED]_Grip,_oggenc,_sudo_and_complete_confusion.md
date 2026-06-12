---
title: "[SOLVED] Grip, oggenc, sudo and complete confusion"
date: 2008-04-05
forum: General Help
---

### Post by PaulGrahamRaven on 2008-04-05
OK, so I'm trying to use Grip to rip CDs to ogg format. I have vorbis-tools installed, no problems.

Now, if I just run Grip normally, I get the message "Invalid coder executable [...] ensure it specifies full path to the encoder executable".

That path is set to usr/bin/oggenc, and a look in my file system shows it right there where it belongs. But it belongs to root.

"Ah, OK," I thought, "if i run Grip as gksudo, it can use the oggenc binary." And I was quite right, it can; so I set it to output the encoded files into my home directories.

But, of course, the directories and files it outputs are also owned by root, meaning I can't do anything with them ...

So, I know I've made a logical error somewhere along the line, but none of the threads I've found here have shown me what I've done wrong (though they helped me get as far as I did). Can someone explain to a n00b what he's doing wrong?

[Running Gutsy 7.10 i386 with all the current updates and so on; please ask for any other pertinent info, as I'm a bit lost. This is all the more embarrassing when you consider I was brought up on command-line MSDOS ... helloooooo, learning curve!  :( ]

---

### Post by logos34 on 2008-04-05
> **PaulGrahamRaven said:**
> That path is set to usr/bin/oggenc

Should be **[COLOR="Red"]/[/COLOR]**usr/bin/oggenc.  But I assume you just made a typo.

You might try copying oggenc to /usr/local/bin, and use that path. Might work, never know. (I have to do that for another app)

Permissions should look like this:
[COLOR="Red"]-rwxr-xr-x[/COLOR] 1 root root 67232 2008-03-21 05:37 /usr/bin/oggenc

---

### Post by PaulGrahamRaven on 2008-04-05
> **logos34 said:**
> Should be **[COLOR="Red"]/[/COLOR]**usr/bin/oggenc.  But I assume you just made a typo.

I'd love to tell you that your assumption was correct; in truth, you pointed out my error - I'd been skipping that leading slash. Many thanks - I may feel a fool, but that's the only way to learn, I guess! :D

---

### Post by logos34 on 2008-04-05
no prob, glad to help.  The important thing is that it's fixed.  

Now you can enjoy superior ogg audio fidelity!

---

