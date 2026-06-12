---
title: "Making Conky show my music played through Amarok"
date: 2008-05-06
forum: General Help
---

### Post by Eax.exe on 2008-05-06
**EDIT!**
Never mind :) I solved it 5 minutes after I posted.

I just had to rename "amarok.sh" to "amarok".


Hello :)

I'm trying to make Conky show what music is currently being played in Amarok.
But I won't :(
I shows up as it should, but it doesn't show what is currently playing.

This is the code inserted .conkyrc:

```

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}

```

The amarok.sh isn't used anywhere? Oo Should it be named "amarok" instead?
And how do I make a folder with the  ~ infront? 

Thank in advance :D

---

