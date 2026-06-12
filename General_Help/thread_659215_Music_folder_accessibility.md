---
title: "Music folder accessibility"
date: 2008-01-05
forum: General Help
---

### Post by groovomata on 2008-01-05
Hey All,
I have two users on my gutsy box. I have a lot of music in my home/erik/Music that I would like to make available to home/karina/Music. I'd like to set things up so that both users can use rhythmbox (for instance) to listen to music from the folder and also see, search and import files to that folder as well.
Happy New Year!
Erik.

---

### Post by Seti on 2008-01-05
```
 chmod -R 755 /home/erik/Music
```

unless you want karina write access to ~/Music, in which case, 

```
chmod -R 775 /home/erik/Music
```

Don't forget to read the man page for chmod to see how this works

---

### Post by groovomata on 2008-01-05
Cool, thanks. I figured out that I can simply point rhythmbox to home/erik/Music from the other user's folder and it'll play the music no problem. However I was thinking that perhaps it would be better for bother users to actually share that folder. 
I'll check out the man pages on that. 
Thanks,
Erik.

---

### Post by ~LoKe on 2008-01-05
How about a symbolic link?
```
sudo ln -s /home/erik/Music /home/karina/Music
```

So when Karina tries to play music from her own Music folder, it'll be playing the contents of Erik's music folder.  Not sure if this is exactly what you're after.

---

### Post by groovomata on 2008-01-05
Thanks for that! I think that's what I'm after...
Erik.

---

### Post by ~LoKe on 2008-01-05
> **groovomata said:**
> Thanks for that! I think that's what I'm after...
Erik.

Great, let us know how it works out.

---

