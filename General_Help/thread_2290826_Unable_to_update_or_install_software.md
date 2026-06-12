---
title: "Unable to update or install software"
date: 2015-08-15
forum: General Help
---

### Post by ray_silva on 2015-08-15
OK, maybe I should be posting a totally new thread, but here is my problem: I think I have completely messed up my 14.04 LTS install. Everything was working great until recently. I tried to install Emby server for Kodi and actually have never gotten it to work. I started noticing that my updates stopped working. I'd get a message that my installer package was broken. Nothing would update. I can't even install any software from the Ubuntu Software Center. The Ubuntu message suggested I disable third party repositories, which I did. It also said then to run apt-get -f, which I did. That gave me a message that libsdl2 needed to be installed because it was a kodi-bin dependency. I said yes, but got an error and it did not install. I wish there were something like Windows' "system restore" so I could go back to where I was before all this. There may be software that would have helped had I installed it before, but I didn't. So now I'm stuck. I don't have a clue how to fix mu system installer package. Will I have to start completely from scratch and blow out everything, re-partition and re-install Ubuntu? Can anybody help me on this? I'm totally frustrated.

---

### Post by PaulW2U on 2015-08-15
Post moved to its own thread.

---

### Post by v3.xx on 2015-08-15
Yep, should of started your own thread :)

Please run
```
sudo apt-get update && sudo apt-get upgrade
```
and post the results using code tags.

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by PaulW2U on 2015-08-15
ray_silva, as you already have a thread in progress at [http://ubuntuforums.org/showthread.php?t=2287577](http://ubuntuforums.org/showthread.php?t=2287577) will close this one.

---

