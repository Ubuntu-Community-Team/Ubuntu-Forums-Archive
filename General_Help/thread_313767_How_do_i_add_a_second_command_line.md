---
title: "How do i add a second command line?"
date: 2006-12-06
forum: General Help
---

### Post by thecynicality on 2006-12-06
When i play one of my games, the sound doesn't work unless i run the line:
```
sudo killall artsd
```
in the terminal.

Well im tired of doing this, is there any way i can add that command to the command line for the program?

---

### Post by taurus on 2006-12-06
You can try something like

```
<first command> && <second command>
```

---

### Post by thecynicality on 2006-12-06
I can't get it to work, the game won't load. I tried:
```

<"sudo killall artsd"> && </usr/local/games/enemy-territory/tc-elite>
```
and

<"killall artsd"> && </usr/local/games/enemy-territory/tc-elite>

and i tried them without the quotes. Any ideas?

---

### Post by thecynicality on 2006-12-06
and i tried without the "<>"

---

### Post by taurus on 2006-12-06
```
sudo killall artsd  &&  /usr/local/games/enemy-territory/tc-elite
```

---

### Post by CatKiller on 2006-12-06
You don't need the <> around the commands.

If you do need the sudo (I don't know that you do) you might want to use gksudo or kdesu (depending on whether you're using Gnome or KDE) so that you actually get the password prompt. Otherwise your command will appear to silently fail.

Oh and I suspect that if artsd has already stopped running, the first part might fail, meaning the second won't run. The && means do the second if the first was successful, I think. You could try just one &, which I think would mean do the second after the first, regardless.

---

### Post by thecynicality on 2006-12-06
Yeah i tried that, didn't work but i got it to work without the sudo, thanks!

---

