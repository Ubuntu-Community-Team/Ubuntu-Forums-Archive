---
title: "elusive disapearing file"
date: 2006-12-12
forum: General Help
---

### Post by martijn hoekstra on 2006-12-12
I have a file that won't delete because it doesn't exist. It's in my trash folder. I don't know what to say so ill show it:
```

$ sudo rm -r .Trash/*
rm: cannot remove `.Trash/Program Files/PokerStars/Gx/fplogo.bmp': No such file or directory
$ cd .Trash/Program\ Files/PokerStars/Gx/
/.Trash/Program Files/PokerStars/Gx$ ls -la
total 0
drwxr-xr-x 2 martijn martijn 80 2006-12-08 01:41 .
drwxr-xr-x 3 martijn martijn 72 2006-12-08 01:41 ..
?--------- ? ?       ?        ?                ? fplogo.bmp
/.Trash/Program Files/PokerStars/Gx$ rm fplogo.bmp 
rm: cannot remove `fplogo.bmp': No such file or directory
/.Trash/Program Files/PokerStars/Gx$ 

```

I have no idea what's happening. It's a reiserfs partition.

does anyone have any ideas?

---

