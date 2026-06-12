---
title: "TRying to install Browser Google Chrome I get error about a missing dependency"
date: 2015-10-01
forum: General Help
---

### Post by webwiller on 2015-10-01
ERROR!
I'm very basic.....tried ubuntu years ago, but cause of proprietary sw I was obliged to abandon ...so now I'm baby-like... :)

---

### Post by NathanRodriguez on 2015-10-01
How did you tried to install Chrome?

---

### Post by slickymaster on 2015-10-01
google-chrome-stable is available on a 3rd Party Repository: Google Chrome (For Stable). All you have to do is to open your terminal and run the following:```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

---

### Post by webwiller on 2015-10-01
ERROR: "libappindicator" dependency is missing.

And I don't get any further explanation nor infos.

I'm very basic to ubuntu but I can copy/paste code to terminal! yeah!!!! ;)
Ty in advance!
w.

---

### Post by webwiller on 2015-10-01
[ATTACH=CONFIG]264771[/ATTACH]





tried this also.... :(

---

### Post by howefield on 2015-10-01
Duplicate threads merged, one is sufficient.

---

### Post by webwiller on 2015-10-01
> **howefield said:**
> Duplicate threads merged, one is sufficient.

Thx....
Sry for that

---

### Post by webwiller on 2015-10-01
> **slickymaster said:**
> google-chrome-stable is available on a 3rd Party Repository: Google Chrome (For Stable). All you have to do is to open your terminal and run the following:```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

Ty very much!

---

### Post by QDR06VV9 on 2015-10-01
> [COLOR=#000000]*Last edited by webwiller; 24 Minutes Ago at *[/COLOR][COLOR=#3E3E3E]*12:12 PM*[/COLOR][COLOR=#000000]*. *[/COLOR][COLOR=#000000]***Reason:***[/COLOR][COLOR=#000000]* where the hell do I mark it as solved?!?! ;)*[/COLOR]
Like this [**[COLOR=Red]_solved_[/COLOR]**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by webwiller on 2015-10-01
Which is the best way to post a picture here? A PC one or a web one like flickr

---

### Post by howefield on 2015-10-01
> **webwiller said:**
> Which is the best way to post a picture here? A PC one or a web one like flickr

Use the paper clip icon in the posting window to attach your image to the post.

---

