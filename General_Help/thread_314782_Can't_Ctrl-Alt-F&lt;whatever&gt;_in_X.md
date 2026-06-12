---
title: "Can't Ctrl-Alt-F&lt;whatever&gt; in X"
date: 2006-12-08
forum: General Help
---

### Post by authortitle on 2006-12-08
Whilst trying to fix some login problems, I've found with Ubuntu on my laptop that Ctrl-Alt-F<whatever> to get to a console doesn't work from the gdm login screen, and sometimes doesn't work once logged in either.

It simply doesn't respond - to get to a console I have to either Ctrl-Alt-Bksp and then hammer Ctrl-Alt-F1 for about 20 secs - X flashes up then it goes back to the console, or login to failsafe terminal and sudo /etc/init.d/gdm stop and then Ctrl-Alt-Bksp.

Any clues how I can get this functionality back?!

Cheers
Tom

(I should add, to anyone who notices I've posted two other random problems on this forum and is thinking "why not just reinstall":

I've been through many distros over the years and pretty much everyone has got messed up to the point where I had to reinstall - this doesn't surprise me as it is the nature of a open, totally configurable system such as Linux, especially when combined with someone who likes to mess with stuff like me :)

However, reinstalling over and over doesn't teach me any new problem solving skills - I'd rather learn how to diagnose such problems and get them fixed. I don't really use this machine for anything significant so time isn't a factor. Cheers!)

---

### Post by bapoumba on 2006-12-08
Hi, are you using xgl ? There are several threads dealing with this issue.

---

### Post by authortitle on 2006-12-09
Not intentionally... but I was playin around trying to get Beryl installed (even though my gfx card will in no way handle it!) so I'll double check that. I'll have a look for other threads.

Thanks!

---

### Post by authortitle on 2006-12-19
You were right pamouba, thanks. I just removed XGL from xorg.conf for now but I'll find a proper resolution to it one day!

---

