---
title: "Scipts won't run without full path"
date: 2007-11-27
forum: General Help
---

### Post by 0/0 on 2007-11-27
I am working on setting up 2 Ubuntu Server boxes with DRBD/Heartbeat + Samba. Everything loads if I run it manually, but won't from the Heartbeat resource scripts. **I don't think this is a Heartbeat issue!** It has something to do with the path to the executable scripts.

Basically, if I try to run the Heartbeat resource scripts manually from within the directory they won't run. I.e., cd into the dir and type the script name gives an error ("samba start" = "command not found"). If I type the whole path along with the script name it starts ("/etc/ha.d/resource.d/samba start" = successful). This happens with pretty much anything in the /etc/ha.d/resource.d directory. The haresources file assumes some things, like path and some options (start, stop, restart, etc), so the scripts really need to run without the path specified, as near as I can figure.

I am sure that this has to do with a link, a path variable of some sort, or something similiarly simple that I should know, but I don't. Though I love 'nix in theory, I just don't have enough day-to-day experience with it to know what is going on here.

Thanks for your help.

---

### Post by Tenken on 2007-11-28
That is normal for scripts, instead of typing the full path while in the directory you can type ./scipt. The ./ signifies "this directory"

```
cd /etc/ha.d/resource.d
./sambastart
```

---

### Post by neilengineer on 2007-11-28
How about you changing the script with the full path like :

change "samba start"
to "/etc/ha.d/resource.d/samba start"

---

### Post by 0/0 on 2007-11-28
>That is normal for scripts, instead of typing the full path
>while in the directory you can type ./scipt. 

Crap. Now I feel stupid. :-) I think I remember this from a shell scripting class from *many* moons ago.

So I guess the question is, what do I need to do to the haresource file to get heartbeat to launch them?

---

