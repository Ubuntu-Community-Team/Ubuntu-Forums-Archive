---
title: "Disable Turning Screen Off While Watching Video"
date: 2012-10-16
forum: General Help
---

### Post by Shadius on 2012-10-16
Hello everybody! :)

So I'm watching videos online and whether I'm in full screen mode or not Ubuntu will turn off my screen when it is inactive for 10 minutes, but it's not really inactive because I'm watching videos and not moving the mouse or doing anything else. How can I stop Ubuntu from turning off the screen when I'm watching videos?

---

### Post by kcxzero on 2012-10-16
Good question, this is something I've been trying to do for years. I never found a way to do this through power manager. As it does not matter if a video is running, full screen or not. In the past I just always disabled the screensaver etc. before I'd start watching a video.

However, I found this: [http://askubuntu.com/questions/144621/how-do-i-stop-the-screensaver-from-turning-on-when-watching-videos](http://askubuntu.com/questions/144621/how-do-i-stop-the-screensaver-from-turning-on-when-watching-videos) Using Caffeine you're able to assign what programs should disable the screensaver. That is the best solution I found so far.

Hope my post helps, although I'm also very interested to hear from anyone who knows of a solution without using an application.

---

### Post by Shadius on 2012-10-16
> **kcxzero said:**
> Good question, this is something I've been trying to do for years. I never found a way to do this through power manager. As it does not matter if a video is running, full screen or not. In the past I just always disabled the screensaver etc. before I'd start watching a video.

However, I found this: [http://askubuntu.com/questions/144621/how-do-i-stop-the-screensaver-from-turning-on-when-watching-videos](http://askubuntu.com/questions/144621/how-do-i-stop-the-screensaver-from-turning-on-when-watching-videos) Using Caffeine you're able to assign what programs should disable the screensaver. That is the best solution I found so far.

Hope my post helps, although I'm also very interested to hear from anyone who knows of a solution without using an application.

Yeah, I found that post too. I guess there's no other way, currently, of doing what we'd both like. =/ I thought there would be a solution rather than using another application or changing the screensaver settings everytime.

---

### Post by kcxzero on 2012-10-16
Yeah. I've been looking for a solution on and off since 10.04. But I never posted or asked anyone, just browsed to see if there were already answers. So hopefully this post attracts anyone who knows how to (if possible).

---

### Post by wojox on 2012-10-16
Toggle between true and false in the terminal (Ctrl+Alt+T):
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

---

### Post by pqwoerituytrueiwoq on 2012-10-16
i made a script for this, it was intended for xscreensaver
only tested on xubuntu
[http://ubuntuforums.org/showpost.php?p=12291285&postcount=9](http://ubuntuforums.org/showpost.php?p=12291285&postcount=9)
you may need to comment out this line for ubuntu since it uses no screensaver
```
xscreensaver-command -deactivate > /dev/null
```
or replace it with (xdotool is not installed by default)
```
xdotool key shift
```

---

