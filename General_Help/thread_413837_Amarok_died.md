---
title: "Amarok died"
date: 2007-04-19
forum: General Help
---

### Post by darksong on 2007-04-19
Hi all - another little problem =)

I just installed amarok, it installed i opened it for the first time, It crashed. I tried to re-open it but it does not reopen - even after reinstall through apt-get and synaptic ;S

any suggestions?

---

### Post by goldaryn on 2007-04-20
What happens when you run try to run it in a shell? This would provide more information..

g.

---

### Post by xfile087 on 2007-04-20
> **darksong said:**
> Hi all - another little problem =)

I just installed amarok, it installed i opened it for the first time, It crashed. I tried to re-open it but it does not reopen - even after reinstall through apt-get and synaptic ;S

any suggestions?

Not quite the same I don't think but I installed it myself last night and everytime I tried to play a song it would crash on me. I had to froce quit. Have you rebooted since it last crashed? When I force quit mine it still left loads of processes behind and wouldn't open again until I rebooted.

---

### Post by ashz on 2007-04-20
yeah my kept crashing when ever i tried to play a song on it last night because the mp3 thing was not installed yet!! (new install of feisty)

if u goto usr/lib/amarok then click on install-mp3

hopefully then it wont crash on u, u will have to put in ur password because it is a script thats uses synaptic!!

---

### Post by goldaryn on 2007-04-20
> **ashz said:**
> 
if u goto usr/lib/amarok then click on install-mp3

Well, I've not heard of that script.

The last time I used ubuntu (herd 4) the codec wizard did a nice guided install of the right codec when you opened an mp3 file in totem. (Or double-clicked in Nautilus, out of the box)

What I used to do (in ye olden days, to avoid messing about with gstreamer) is "sudo apt-get install amarok-xine libxine-extracodecs".. but I don't recommend this. Don't think it's necessary now.

g.

---

### Post by ashz on 2007-04-20
normally amarok would do it automatically but i found it crashed before it ran the script, so thats why i gave instructions to run it manually.

---

### Post by xfile087 on 2007-04-20
> **ashz said:**
> yeah my kept crashing when ever i tried to play a song on it last night because the mp3 thing was not installed yet!! (new install of feisty)

if u goto usr/lib/amarok then click on install-mp3

hopefully then it wont crash on u, u will have to put in ur password because it is a script thats uses synaptic!!

Perfect! No crash now! Too bad it couldn't just let me know instead of crashing...

---

### Post by ashz on 2007-04-20
glad to have helped!

---

