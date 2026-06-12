---
title: "Configuring Network Devices"
date: 2007-07-17
forum: General Help
---

### Post by kf4tqj on 2007-07-17
I'm running 6.06 on a Compaq Presario. The modem is a 
Zoom, serial port type. It used to dial up while booting when it got to Configuring Network Devices but has stopped doing that. I'm having to go to System / Administration / Networking or Networking tools to tell it to dial.
    I could use some help getting this setting back the way it was, and any speculation on how I might have screwed it up.
Thanks,
Woody / KF4TQJ

---

### Post by Bartender on 2007-07-18
This help any?
[http://ubuntuforums.org/showthread.php?t=476448&highlight=dial+at+boot](http://ubuntuforums.org/showthread.php?t=476448&highlight=dial+at+boot)

---

### Post by kf4tqj on 2007-07-18
That got me into the right area, but...I can't figure out how to edit that page. The cursor stays at the top left corner no mater what I do. I tried copying the whole thing to Gedit and edited it there but I couldn't cut the original. Then I went to Ect / Network and tried to edit it there but it said I didn't have permission.
How do I edit the page I get after running the sudo command  in the terminal?
Thanks,
Woody / KF4TQJ

---

### Post by Bartender on 2007-07-19
k4 -
"nano" is a stripped-down file editor.  Some folks prefer it, but I imagine most of those people are very familiar with command line work.

Try the same command, but instead of 
```
sudo nano /etc/network/interfaces
```

type
```
sudo gedit /etc/network/interfaces
```

You should be able to click the "Save" icon to save the changes.  You can save the changes in nano but it's text-based and I don't remember the "save" command right off the top of my head.

---

### Post by kf4tqj on 2007-07-31
One of the recent updates seems to have fixed the problem. After about 2 months of not dialing while loading, it's back to doing it right.
Appreciate all the responses.
Woody / KF4TQJ

---

