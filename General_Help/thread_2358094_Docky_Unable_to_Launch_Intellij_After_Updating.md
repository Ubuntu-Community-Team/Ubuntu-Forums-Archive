---
title: "Docky Unable to Launch Intellij After Updating"
date: 2017-04-09
forum: General Help
---

### Post by j4102 on 2017-04-09
I recently updated intellij to 2017.1 but when I try to launch it from Docky it doesn't work. It works perfectly fine on my unity launcher and if I click the super key and then launch it in that window it will work but it won't launch on Docky. It also shows the wrong version of Intellij (it shows 2016.3 with an old project name) when I hover over it and when I hover over it using my unity launcher it just displays "Intellij Community Edition". Here are the pictures showing both of them.

[ATTACH=CONFIG]274492[/ATTACH]

This first picture shows intellij being launched on the unity launcher perfectly with the correct name when I hover over it 

[ATTACH=CONFIG]274493[/ATTACH]
The second picture shows Intellij launched however this was launched using the super key and launching it from that window (I don't know what's it called sorry). As you can see the name is also wrong when I hover over it - it displays something like "/projects/bukkit/stuff/ - De.cmd Intellij 2016.3". This project doesn't even exist anymore as well which I find quite odd.

---

### Post by howefield on 2017-04-10
So, remove from Docky, then put it back ?

Sorry for the oh so simple suggestion but you haven't said whether you tried it or not.

---

### Post by j4102 on 2017-04-10
Okay, yeah I tried that first 2 times with 'sudo apt-get remove docky' and then I also used right after that 'sudo apt-get autoremove' to remove all the config files but everytime I would install it back it would still reappear with the same exact launcher that I had before. I also tried purge too with remove which did not help. 

I honestly thought that those commands would remove the configuration files.. until I tried to manually delete the configuration files by typing in 'docky' in the search nautillus bar. That's when I was able to delete all the docky folders and when I installed it back and clicked on intellij it worked. 

So TLDR - Your solution worked but I had to manually delete the files when I thought that purge and autoremove would work. Thanks!

---

### Post by howefield on 2017-04-11
Cool, I actually meant just removing the offending icon from docky and replacing it with the correct one, but glad you managed to suss it, feel free to mark the thread as solved to aid others. :)

---

### Post by j4102 on 2017-04-13
I did do that, I used the same exact icon on the unity launcher and docky but somehow docky managed to show up with an icon with a totally diferent name.. and sorry for the late replies, I'm not getting notifications from these posts for some reason.

---

