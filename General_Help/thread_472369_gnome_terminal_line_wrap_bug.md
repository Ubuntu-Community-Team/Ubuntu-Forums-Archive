---
title: "gnome terminal line wrap bug"
date: 2007-06-13
forum: General Help
---

### Post by goneskiing on 2007-06-13
Is there a setting or workaround for the word wrapping that happens in gnome terminal - it looks like it's wrapping at about 75 characters - problem is that the wrap overwrites the beginning of the line - serious bug!

---

### Post by quantumcheese on 2007-08-29
*bump*

I have this problem, too, but I had assumed that I'd cuased it by tweaking .inputrc .
Moreover, when I go "up" into my shell history to a long command (one that was wrapped), every character I edit causes all of the text to ascend one line on my terminal (see screenshot - cursor ends in upper-left).

This problem afflicts all of my terminals -- xterm, aterm, eterm, gnome-terminal.

---

### Post by FuturePilot on 2007-08-29
Could you explain how to reproduce this? I cannot reproduce this.

---

### Post by quantumcheese on 2007-08-29
Here are the contents of my .inputrc; if you want anything else, let me know, but I don't know what else it would be.

```

set bell-style none
"\e[1~": beginning-of-line
"\e[4~": end-of-line
#"\e[5~": beginning-of-history
#"\e[6~": end-of-history
"\e[5~": history-search-backward
"\e[6~": history-search-forward
"\e[3~": delete-char
"\e[2~": quoted-insert
"\e[3C": forward-word
"\e[2D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

```

---

### Post by justincwatt on 2007-10-09
You are not alone. This affects me in a pretty vanilla, untweaked Ubuntu install. I usually experience it writing out long SQL queries in the mysql command line client. The only quick fix I've found: resize the width of your window and the clobbered text will reappear. But I'd like a real solution...

---

### Post by memorygap on 2007-11-18
i was having this same problem but thankfully i had only changed one thing in my .bashrc so i knew where to look. the problem is some non-printable characters in your customized bash prompt are being counted towards the line lengths by the shell and hence messing up wrapping among other things.
the solution is to enclose all non-printing parts of your bash prompt with \[ and \].
here's more info: [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/nonprintingchars.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/nonprintingchars.html)

SOLVED :)

---

### Post by quantumcheese on 2007-11-18
Thank you, memorygap!

---

