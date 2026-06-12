---
title: "old distro left-overs help"
date: 2007-01-20
forum: General Help
---

### Post by tsanoff on 2007-01-20
Hey guys I have a wierd addiction of installing every linux distro i run across. I wanted to try the new slackware, but soon got disappointed and switched back to Ubuntu. In slackware by default you get a My Computer and Home links on your desktop. I have 3 partitions (root, home, and usr/local). I mount my home partition with every linux distribution i install without formating it, before hand i delete most of my .**** files, i just keep the ones that would remember my themes when i come back to ubuntu or any other gnome running distro. After i came back to ubuntu i found, i had a My computer  and Home links left over from the previous distro installation. The thing is i want to remove them but can't. I tried to do it with sudo through the terminal, but when i do "ls" it shows that there are no existing files in my Desktop folder. Then i tried to "sudo nautilus" i went back to my home/username/desktop folder, and the items are not there either. BUT THEY ARE STILL ON MY DESKTOP!!! AND I CAN"T MAKE THEM GO AWAY!!!. If you are getting any ideas coming to mind, let me know. Any help, or direction to be pointed to would be greatly appreciated. (I think it should be one of those hidden .**** files, but i dont want to delete them all, because i have nicely customised my interface and i dont wanna ruin it.)

Thanks for you time,

AlexGT

---

### Post by tsanoff on 2007-01-20
LoL I feel like a complete r-tard for having to post my own solution to my own problem. I was buzzing around through the configuration, an settings and found a very easy solution, i am posting it so others can see it if they run into the same silly problem.

1. hit alt-F2
2. type "gconf-editor" // without the quotes of course
3. Hit apps->nautilus
4. change the appropriate settings.

Have fun.

---

