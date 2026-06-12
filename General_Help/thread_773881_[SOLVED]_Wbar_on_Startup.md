---
title: "[SOLVED] Wbar on Startup"
date: 2008-04-29
forum: General Help
---

### Post by lostlinuxkiwi on 2008-04-29
Can someone please tell me how to get wbar to run on startup in xfce. there is no way to simply add it to the autostarted applications. Ive tried to write a script but since i don't know anything about scripting yet I don't even know if its right. Also I don't know how to run that script on startup anyway. Please its driving me mad.

my script is 

#!/bin/bash

exec wbar -above-desk -bpress

---

### Post by k-i-m on 2008-05-14
Somebody please help, I have the same problem..

---

### Post by prshah on 2008-05-14
> **lostlinuxkiwi said:**
> 
#!/bin/bash
exec wbar -above-desk -bpress

> 
Try edit the **~/.config/autostart/wbar.desktop** file manually.
The line Exec should say ( at least ):
Exec=wbar -above-desk **-pos bottom**


Did it help?

---

### Post by lostlinuxkiwi on 2008-05-19
ok i solved this a couple of weeks ago. 

the script was fine but i needed to chmod it

so i ran "chmod +x wbar.sh"

wbar.sh was the name of the script by the way.

now i can just add the script to autostarted applications in xfce or the startup programs in gnome.

[http://www.linux.com/feature/128982](http://www.linux.com/feature/128982)

thats the site that help me. 

cheers

---

### Post by rojodojo on 2009-01-26
Hi there, when I input 'chmod +x wbar.sh' into the terminal, I get the message 'chmod: cannot access `wbar.sh': No such file or directory.' I cannot find this wbar.sh file with a locate command nor do I know what that file does.
Could you give a more novice walkthru of what you did to get wbar to autostart?

---

### Post by bashphoenux on 2009-10-22
let me consolidate all the posts into what you have to do ---
first open terminal
type

```
 

cd ~/.config/autostart/
vi wbar.desktop
```then paste the code
```

Exec=wbar -above-desk -pos bottom
```save and exit
then type 
```
chmod +x wbar.desktop
```and now restart, it should work as you expected !! :)

---

