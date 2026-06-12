---
title: "Ubuntu stays in black screen after boot selection"
date: 2006-12-25
forum: General Help
---

### Post by Cows on 2006-12-25
Well yesterday I read the tutorials to install beryl on your Edgy Ubuntu. I followed this guide:

[http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)

After I installed it , it was working fine and everything. I also think that it is a problem with the xorg.conf file. Anyways back to the post, It was working fine and everything. I turned it of f to go to sleep and when I wake up to boot Ubuntu, I relieze that after i select Ubuntu in the boot screen it displays Ubuntu loading, the bar loads and then it stays black.

Im very new with Linux so I have limited knowledge of the way Linux works. I tried the only thing i know how to do and that is to create a new xorg.conf file , but I do not know how to rename a file or to move it.

I start Ubuntu in recovery mode and I type 'Xorg -configure' , that makes a new xorg.conf.new file in your /root/ folder. Then I tried to X -configure /root/xorg.conf.new but that didn't work. It gave me a error message about my radeon card after it tried to boot using the .new xorg file. I don't know why but my radeon card was working very good before I installed the beryl and it was also working good after, I think it was the xorg.conf file. Anyways any help would be appreciated. Thanks :).

---

### Post by Cows on 2006-12-25
ok I managed to get it to work by starting it in recovery mode and then I changed directory to /etc/X11/. After that I 'mv xorg.conf~ xorg.conf' and that restored my old 1, but know how do I get beryl to work without messing up my xorg.conf?

EDIT: I just tried to start beryl-manager with my default xorg.conf and it works. Why the tutorial says to edit your xorg.conf?

---

### Post by Vox754 on 2006-12-25
Not really my business, I haven't tried beryl, but you should really practice more with Linux before going to install something that messes up your system.
Basic commands and stuff.

---

### Post by Cows on 2006-12-25
That is true, but look , I just fixed it all by myself and im new to linux. Sometimes you just got to take risks =]. Trial and error is a very good way to learn.

---

