---
title: "TERM=xterm-256color with gnome-terminal"
date: 2007-08-29
forum: General Help
---

### Post by Micah Elliott on 2007-08-29
I'm running an ssh session in a gnome-terminal from one up-to-date Feisty machine to another. I have set "export TERM=xterm-256color" everywhere.  In my local gnome-terminals I don't see any problems with basic tools like man or less.  

But in the ssh'd terminal various tools (man, less, etc) are giving me messages like "WARNING: terminal is not fully functional".  (But ssh might be a red herring; read on...)

And even locally (not ssh'd) mutt is very upset, refusing to start when using xterm-256color.  I presently use a 'alias mutt="TERM=xterm mutt"' alias to get around this one.  And vim just won't syntax-highlight.

I'd like to solve the problem generally instead of collecting alias hacks.  Maybe I'd be best off exporting TERM=xterm (in .bashrc) and then aliasing hi-color-capable tools with aliases like 'alias elinks="TERM=xterm-256color elinks"'.  Still, it seems like there should be a better solution.

I haven't tweaked any terminfo/termcap AFAIK.  Anyone else seen this problem?  Is it just not safe to generally use TERM=xterm-256color ??

I don't *remember* seeing this problem with Edgy.

---

