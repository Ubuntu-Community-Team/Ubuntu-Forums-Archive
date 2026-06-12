---
title: "Problems with VLC"
date: 2015-07-28
forum: General Help
---

### Post by kickflipsnnollies on 2015-07-28
Hi there. I'm having some problems running video off my external HDD. Running Lubuntu 14.04 on an old, awful laptop.

I really haven't had problems until today. IDK what exactly happened (I'm not a complete noob, but I know next to nothing about Linux besides the very basics really) but I started getting choppiness in all my my video files. They'll pixelate and then lose sound, or they'll pixelate for a scene (scenery change sometimes fixes it) then just go black and silent with the video timer (IDK what it's actually called, the bar that tells you where you are in the video) still running in time. I don't know where the error logs are or anything like that. I updated nothing.

So tell me what info you need, cause I'm sure this isn't enough, and how to find it and please help me with this problem. My computer is my only source of entertainment and I don't have money to get another and start over. Also, my screen is physically ruined so installing another distro or installing Lubuntu again fresh isn't really an option. It has to go through my VGA out to my TV or I can see nothing.

Sorry for the vagueness, and thanks in advance for any help.

---

### Post by kickflipsnnollies on 2015-07-28
Just happened again. It pixelated, then I got a popup saying:

```
 [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file (Input/output error).[/COLOR]
```

And then I closed the popup and my movie continued without sound for a few seconds until I got pissed off and closed it.

---

### Post by kickflipsnnollies on 2015-07-28
No ideas?

---

### Post by howefield on 2015-07-28
Have you looked to see if there is anything in Messages ?

VLC > Tools > Messages > set Verbosity Level to 2. Then play the video and you may get a clue in Messages.

Or start the video from the terminal, again looking for clues.

```
vlc /path/to/file/name_of_file
```

---

### Post by kickflipsnnollies on 2015-07-28
It kinda happens randomly, but I just set my messages to Verbosity level 2. I'll play some videos and see if I can get an error.

---

### Post by monkeybrain20122 on 2015-07-28
> **kickflipsnnollies said:**
> Just happened again. It pixelated, then I got a popup saying:

```
 [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file (Input/output error).[/COLOR]
```

And then I closed the popup and my movie continued without sound for a few seconds until I got pissed off and closed it.

Maybe problem with your external HD, either it is dying or the connection to your computer is loose?

Do you experience the same problem if you copy the file to your internal hd and play from there?

---

### Post by kickflipsnnollies on 2015-07-28
Yeah I do. I've also tried downloading directly to my internal drive, never touching the external. Same problem.

---

### Post by monkeybrain20122 on 2015-07-28
What is your graphic card? Are you using hardware decoding? Seeking never works well with vlc (sound gone if you drag the progress bar on for hd movies) Maybe delete the vlc config and start again (the folder to be deleted is  ~/.config/vlc, open the file manager, press ctrl+h to show hidden file, go to .config and delete the subfolder vlc)

---

