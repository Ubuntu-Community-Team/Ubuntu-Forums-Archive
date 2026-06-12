---
title: "My Desktop is gone"
date: 2007-11-24
forum: General Help
---

### Post by Kinkybuu on 2007-11-24
I seem to have misplaced my desktop; if u wanna call it that. heres the story...

I was playing around with some of the User Options and i suppose i unclicked something there and now i have no way of accessing my desktop. I can get to a log in screen, put in my user name and password, Ubuntu accepts it and then it begins to log in but then just stops and shows an orange background with a curser in the middle. i cant right click, go anywhere, or anything. ive lost all powers(i suppose). i can get to terminal via Ctrl+Alt+F1 and thats it. I dont want to reinstall the OS; thats my last resort, so im seeing if anyone here as hear anything or knows a way i can fix this. any help would be awesome, thanx in advance :-)

---

### Post by Sef on 2007-11-24
From the terminal:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

