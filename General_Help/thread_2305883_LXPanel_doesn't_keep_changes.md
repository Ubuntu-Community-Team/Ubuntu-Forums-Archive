---
title: "LXPanel doesn't keep changes"
date: 2015-12-10
forum: General Help
---

### Post by paul_red2 on 2015-12-10
Hi

Firstly, I am not an expert Linux user (I've always used it but never went beyond the GUI)

I installed Lubuntu on an old netbook. Everything went fine until I decided to edit the icons on the LXPanel (I guess it's called like that).
When I loaded the weather widget / icon (or whatever you call it) the menu and all its icons disappeared (!)
After restarting, the problem persisted (no menu, just the desktop with its icons).

After searching online, I saw this was a common problem (and to be frank, I'm thinking of trying another OS)
Anyway I don't remember what exactly I did. I only remember moving the panel files from a location to another. I guess it was to restore the default configuration and make it appear. It looked like the problem was solved because the menu did appear. But it doesn't keep the changes. When I restart the computer, the icons return to the default position.

It look like I have deleted (and I might have done it cause I tried everything to make it reappear) the file where LXPanel writes to memorize the changes. I also had problems with Firefox that also restarted always with the default options, but after a few times, it started to store and keep the changes.

So my question now is: where can I look for the config file that LXPanel uses to store the chages? Or maybe (since I had the problem od Firefox also not keeping the changes) maybe the issue is bigger and I need to reinstall. Maybe the ssd drive of this old eeepc netbook is starting to have physical problems. I don't know. What do you think?

Thank you all.

---

### Post by paul_red2 on 2015-12-12
bump

---

### Post by Rex Bouwense on 2015-12-12
You can try ```
lxpanelctl restart
```

---

### Post by paul_red2 on 2015-12-26
I'm writing this just in case someone else has the same issue.

I had another computer running the same OS (Lubuntu) as the one I had issues with.
So I knew LxPanel folders had always inside a folder named "panels" and a file named "config"
The problem was (since I have no idea how linux is structured) this Lxpanel folder was in different locations.
To find out which was the one I needed, I made a change in the panel and then I saw that the files in the folder located in:
/home/[USER]/.config/lxpanel/Lubuntu changed the edited date. So I copied these files (folder "panels" + file "config") to the same location on computer I had issues and the panel worked as before.

Thank you all for your help
Bye!

---

