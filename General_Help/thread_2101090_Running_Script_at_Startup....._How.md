---
title: "Running Script at Startup..... How?"
date: 2013-01-03
forum: General Help
---

### Post by yusuo85 on 2013-01-03
I've made a script in order to reassign my space bar to my right alt key, seeing as my space bar is damaged. 
The script runs fine and does what I need it to do however I want this to be run at boot so I don't have to open terminal everytime I turn on the computer and run the script myself

I've tried running the script via crontab using
> @reboot /home/yusuo/Scripts/script.sh
But that doesn't do anything 

Here are the contents of the script
> sleep 8 && xmodmap -e 'keycode 108 = space'

Anyone have any idea how I can get this to run on startup.

Im using Ubuntu 12.10

---

### Post by ajgreeny on 2013-01-03
Just add the script to a folder in your home called **~/bin** and then point to it in startup-applications using just the script name.  By default ~/bin is included in the system $PATH but you can check that with command ```
echo $PATH
```so as long as the script is executable it will then run at session startup.

---

