---
title: "A folder under my home directory is gone."
date: 2018-11-21
forum: General Help
---

### Post by luar7olye on 2018-11-21
Hello there, just as the title, a folder of mine under my home directory is just GONE.

Here's what I did yesterday:
-removed several default folders(like Music, Videos, examples.desktop)
-some novice customizing of vim(like python.vim, installing colortheme, installing linuxbrew, ...)
-opened python simplehttpserver at localhost:8080
-used some REST api and requested json
-and rebooted to windows(through grub) after all of those finished

And that's it.
I moved all my projects file to a single folder(~/Projects) and just that folder is totally gone, other folders are just fine.
I tried to find files that I remember using terminal, and I can't reach any of them.

Anyone please give me some help? Thanks.

---

### Post by Bashing-om on 2018-11-21
luar7olye; Ouch 

See what you can see.
change your directory :
```

cd /

```
what shows now for terminal commands:
```

ls -al /home/
ls -al /home/<username_here>/

```
IE: ls -al /home/sysop/ ; where my username is sysop.


[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by HermanAB on 2018-11-21
Chances are that you folder has a different name or is now owned by root, so you can't find or see it.
```
$ sudo find / -name filename
```

---

