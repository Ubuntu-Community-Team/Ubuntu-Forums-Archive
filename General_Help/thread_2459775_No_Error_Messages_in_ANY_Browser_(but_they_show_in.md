---
title: "No Error Messages in ANY Browser (but they show in Windows 10)"
date: 2021-03-25
forum: General Help
---

### Post by Germbat on 2021-03-25
Hello all!

I'm hoping someone might know what's going on and could help me out. I'm trying to test out a PHP project on my laptop running Ubuntu 20.04, but I'm finding it difficult to fix issues in my code if all of my browsers are only displaying blank screens (see attached). When I copy the exact same project over to my Windows 10 desktop, I actually get error messages I can use to fix my code (see attached).

On Ubuntu, Firefox just shows a blank screen, while Chrome and Edge just give a general error about the page not working.

Is there a system setting I need to adjust in Ubuntu somewhere, since this doesn't seem to be a specific browser issue?


Thank you!


[ATTACH=CONFIG]288182[/ATTACH][ATTACH=CONFIG]288184[/ATTACH][ATTACH=CONFIG]288185[/ATTACH][ATTACH=CONFIG]288186[/ATTACH]

---

### Post by dragonfly41 on 2021-03-25
Do you have correct entries in /etc/hosts
127.0.0.1	localhost

---

### Post by Germbat on 2021-03-25
Yep, the entries are correct in /etc/hosts.

---

### Post by Germbat on 2021-03-25
Thanks for helping me out dragonfly41, I appreciate it :D

I did some more searching online and finally found someone who had the same issue:

[https://stackoverflow.com/questions/5050426/php-errors-not-being-displayed-in-the-browser-ubuntu-10-10](https://stackoverflow.com/questions/5050426/php-errors-not-being-displayed-in-the-browser-ubuntu-10-10)

It's a (very) old post, but it was still helpful.

I just had to find the "php.ini" file and change the "display_errors" to "On".

Now everything is working perfectly as needed, no need to switch back to Windows for this project!!

---

### Post by TheFu on 2021-03-25
Look at the apache/nginx/lighthttp log files.  There should be an access.log and an error.log which show what is hitting the web server.
If nothing it showing in those log files, run the configtest option. That should provide a line number for the first error.  The option for 
configtest depends on the specific web server used.

We seldom want images here. Please post text - copy/paste and wrap in code-tags. [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how. For people with bad eyesight, we can't real 2pt fonts on an 8K monitor. I'm exaggerating, but I still can't read that output.  Text, please.

I will admit to making some of my websites refuse to work with any Windows browser on purpose, but most people wouldn't want that.
As for authentication, I've always implemented that in the code using well-known modules for the language, not dependent on the bone
head web server trivial auth module.

---

