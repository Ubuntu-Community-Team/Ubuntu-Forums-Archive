---
title: "Grey boot screen at edgy.HELP a newbie get rid M$"
date: 2006-10-28
forum: General Help
---

### Post by DrSasaroli68 on 2006-10-28
Ok, i am a complete newbie at the linux world, but i am REALLY eager to say goodbye to windows once and for all. I am really excited with ubuntu, but i have this problem, so i need your help.

I installed Dapper 6.06 and everything worked fine.While it booted it showed a colored logo and beneath it it showed a terminal-like screen which showed the processes i think.
I tried to install automatix2 by using the instructions and searching the forums with no luck.I had an error message like package automatix2 can not be found.The funny thing is that with the instructions i COULD install perfectly well the automatix2 version for edgy 6.10, which didnt of course work because it was for another edition.So i decided to upgrade to Edgy.
**And the problem is that now i get while booting a cheesy grey screen, in which no processes are shown under the logo and the progress bar looks like it is a bit "stuck"**. the systum otherwise works fine.Has anyone got any ideas why the cheesy screen in which the proccesses are not shown? HELP please!!!

---

### Post by Choad on 2006-10-28
thats just how it's done in edgy

the package i think is ubuntu-artwork-usplash

im not sure how you down-grade packages, but you can probably downgrade it to the breezy one somehow. i would like to do the same really, i prefer the old one too. the gradiants in the xubuntu one really suck with low colour depth

---

### Post by almalaci on 2006-10-28
I have the same problem. It's not just that it doesn't look good, it would be quite helpful to see what's going on at startup. I don't think it was meant to be like that in edgy.

---

### Post by Choad on 2006-10-28
> **almalaci said:**
> I have the same problem. It's not just that it doesn't look good, it would be quite helpful to see what's going on at startup. I don't think it was meant to be like that in edgy.
yer it is. people complained about the "scary text" that you dont see in XP/osX

---

### Post by Muntted on 2006-11-01
Im getting the same thing and its definently not the way the edgy boot screen is supposed to look.

It
1. has no colour in it
2. the right hand side of the loading bar has a grey fill already even though that area had not been loaded yet if you get my drift.

I have just moved from 32 bit edgy to 64 bit edgy.

---

### Post by frizzl on 2006-11-04
choad, it isnt supposed to be like that

the screen is all monotone and the logo is partially corrupted

the screen is corrupted in a way, the loading bar is grey and doesnt load in a chronololical order and you can see stuff moving around 'in it'

there are no words either...

---

### Post by pgatrick on 2006-11-04
I'm having the same problem with 64 bit edgy.. Doesn't really matter I guess, but it's very annoying, and it's nice to see what's going on as it boots.

---

### Post by LenzM on 2006-11-04
I'm not sure about the color problems, but the to get the text back you have to edit /boot/grub/menu.lst

Look for this block of text
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```
and remove 'quiet' from the last line.

Now run
```

sudo update-grub

```

---

