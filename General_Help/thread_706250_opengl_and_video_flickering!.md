---
title: "opengl and video flickering!?"
date: 2008-02-24
forum: General Help
---

### Post by el_ricardo on 2008-02-24
hi all, I've just got an ATI radeon 2900 XT. I've just finished installing the drivers, which was a mission in the first place, and now i've been hit with flickering in all opengl apps, and videos while compiz is running. I've googled around, and fixed the video issue, and from what i can gather the opengl is pretty unfixable for the time being.

I was just wondering if there was any news on the issue, like whether there's some beta ati drivers i could try, or a new workaround?

I'm very annoyed because one of my expectations of this card was that i'd be able to play 3d games without having to close down compiz!

also, what is the release cycle for the proprietary ATI drivers?

---

### Post by tors on 2008-02-24
Release cycle seems to be once a month.

Version
8.01 = Jan
8.02 = Feb
8.03 =

---

### Post by danwood76 on 2008-02-24
This is a well known problem with the ati drivers and compiz.
Its rumoured to be repaired in the next couple of ati releases but im not holding my breath.

I can run video without flickering and with compiz running by using VLC and setting the video output module to be 'X11 Video Output' I dont really play many 3d games on linux so I cant help you in that respect.
I have an x1950 Pro by the way.

---

### Post by stinkinrich88 on 2008-03-03
thanks, worked for me. I'd love more info on this though, and something to sort it in other applications. Also, anyone experiencing problems with mipmaps in compiz? safe

---

### Post by pro003 on 2008-03-08
i have the same problem since i started using compiz and ati driver jan 2008 release and i can't watch video at all beacuse it flickers to much so guess i have to disable compiz and then watch some movie or tv show... as far 3d games are concerned there is an issue too when i try to play some 3d game it pop up the error message that this video card doesn not support 3d acceleration and my graphic card in use is ATI HD2600 Pro.

So, am still kinda looking for solution. Am installing the vlc player so i could try to do something about this issue, if any news I'll let you know first..

---

### Post by stinkinrich88 on 2008-03-08
> **pro003 said:**
> i have the same problem since i started using compiz and ati driver jan 2008 release and i can't watch video at all beacuse it flickers to much so guess i have to disable compiz and then watch some movie or tv show... as far 3d games are concerned there is an issue too when i try to play some 3d game it pop up the error message that this video card doesn not support 3d acceleration and my graphic card in use is ATI HD2600 Pro.

So, am still kinda looking for solution. Am installing the vlc player so i could try to do something about this issue, if any news I'll let you know first..

Yeah just change the video output in VLC to X11. Open preferences -> output modules -> select "advance options" checkbox -> select X11 from dropdown list.

Also, I just did a clean install of Hardy alpha 6. No flickering at all now, not in totem, not in default vlc, nowhere. Still no mipmaps though...

---

### Post by pro003 on 2008-03-08
I just did that. Can you tell me what should I do then? I mean what should I type in section X11 display? And should I check Alternate Full screen Method?

Thanks.

MSN: [email]pro003@hotmail.com[/email]

---

### Post by stinkinrich88 on 2008-03-08
that's all you need to do. You don't need to type anything, just literally:

open vlc -> settings -> preferences -> video -> output modules -> check "advanced options" -> select "X11 video output" from the dropdown next to "video output module"

that should sort you video flickering in VLC. As for your games, I don't have a clue. For any other opengl apps (like totem) I also don't have a clue, however, a clean install of hardy alpha 6 seemed to sort most opengl apps (only tried totem & vlc). 

good luck!

---

### Post by pro003 on 2008-03-08
thanks man... didn't solve the problem but keep in mind that i run guttsy 7.10

thanks anyway & good luck2u2

---

