---
title: "Where is the trash in Xubuntu?"
date: 2006-10-27
forum: General Help
---

### Post by bruenig on 2006-10-27
I have looked. In ubuntu ~/.Trash was pretty simple to find, but I can't find  the trash in xubuntu? Pretty simple I am sure but I am having some problems

---

### Post by DJ Scribblinni on 2006-10-27
Is there a trash can in Xubuntu?  I didn't think there was...

---

### Post by Choad on 2006-10-27
introduced in edgy

it can be got to through the file manager, i dont think it exists as a normal file?

---

### Post by bruenig on 2006-10-27
There must be some sort of file that I can delete that will empty the trash.

---

### Post by Choad on 2006-10-27
right click on trash> empty trash

or are you wanting to do some fancy pants scripting?

---

### Post by bruenig on 2006-10-27
> **Choad said:**
> right click on trash> empty trash

or are you wanting to do some fancy pants scripting?

Fancy pants scripting.

---

### Post by Choad on 2006-10-28
well, it took some searching

[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

the xfce4 trash was written in accordance to that... which *should mean* that "For every user a “home trash” directory MUST be available. Its name and location are $XDG_DATA_HOME/Trash ; $XDG_DATA_HOME is the base directory for user-specific data, as defined in the Desktop Base Directory Specification ."

which just leaves what the hell is $XDG_DATA_HOME/ in XFCE? there is a link to *that* specification but it didnt really tell me much

i would have thought it should be ~/Trash but its obviously not

---

### Post by bruenig on 2006-10-28
> **Choad said:**
> well, it took some searching

[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

the xfce4 trash was written in accordance to that... which *should mean* that "For every user a “home trash” directory MUST be available. Its name and location are $XDG_DATA_HOME/Trash ; $XDG_DATA_HOME is the base directory for user-specific data, as defined in the Desktop Base Directory Specification ."

which just leaves what the hell is $XDG_DATA_HOME/ in XFCE? there is a link to *that* specification but it didnt really tell me much

i would have thought it should be ~/Trash but its obviously not
Thanks for that but I still can't find it for whatever reason

---

### Post by kerry_s on 2006-10-28
/home/user/.local/share/Trash

---

### Post by bruenig on 2006-10-28
> **kerry_s said:**
> /home/user/.local/share/Trash

Wow one of the only ~/.* directories I didn't look in before giving up.

Thanks.

---

### Post by gbendotti on 2008-03-15
> **kerry_s said:**
> /home/user/.local/share/Trash
Thanks from me too, I deleted some root files, i know... that put them in my trash & i couldn't empty it until now. Cheers

---

