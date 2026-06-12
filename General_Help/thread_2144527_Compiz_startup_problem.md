---
title: "Compiz startup problem"
date: 2013-05-12
forum: General Help
---

### Post by dzontra on 2013-05-12
Hi guys,
I'm running Voyager Linux 13.04 and I have problem with compiz startup. 

I have installed compiz with emerald, and then I added compiz to startup session.  
At first it run normally and started with system startup.

But problem raised at one point where compiz is not starting with the system anymore. 

If i run in terminal after system is started:
```
compiz --replace
```
,the compiz starts and is working normally. 

I might have changed something in ccsm that is causing this behaviour. 
But running compiz manually without problems after the system is started confuses me very much. 

I also had this same behavior when running latest Sabayon MATE.

Is there any clue on what is going on here and how can I fix or work around this problem? 

Thanks in front.

---

### Post by ajgreeny on 2013-05-12
I don't run compiz any more, so I may be wrong about this but I seem to remember that I used your command **compiz --replace** in my startup applications list in Ubuntu 10.04 at one time, but that was now a while ago, but I also seem to recall that just the command **compiz** also worked for me.

Try both in your Xubuntu 13.04 and see if it gets you anywhere

---

### Post by dzontra on 2013-05-12
I had it right there in xfce's 'startup application' , called 'session and startup'. 

And at start it did work nice, and booted with compiz working. 
But later it got kind of corrupted for unknown reason, which is strange.

I have tried both with "compiz --replace" and "fusion-icon" already with no luck.
I have also just tried the "compiz" command yuo suggested and it runs compiz on startup same as with "compiz --replace".

I have to note that when unchecking "compiz --replace" from start up list, the xfwm fires up as default WM and everything else works right.
When having compiz option checked , I get broken compiz on startup and no running WM. 

I might as well get used to xfce's native WM. 

Appreciate your help though :) 

Regards

---

### Post by arpanaut on 2013-05-12
You might try the commands found in this link:
[http://ubuntuforums.org/showthread.php?t=2137975&p=12614224&viewfull=1#post12614224](http://ubuntuforums.org/showthread.php?t=2137975&p=12614224&viewfull=1#post12614224)

---

### Post by pqwoerituytrueiwoq on 2013-05-12
This works flawlessly on 12.10 and 13.04 for launching compiz at login, though compiz is a bit buggy
```
echo -e '#!/bin/bash\nif [ ! -f ~/.Compiz ];then\n\texit\nfi\necho "-------------New-Session-------------" > /tmp/compizLog\nx=0;\nif [ 0`pidof compiz` -eq 0 ];then\n\twhile [ 0`pidof xfwm4` -eq 0 ];do\n\t\tif [ $x -gt 300 ];then\n\t\t\tbreak\n\t\tfi\n\t\tsleep 0.02\n\t\tx=$(($x+1))\n\t\techo "I know you are going to start xfwm4..." >> /tmp/compizLog\n\tdone\nelse\n\techo "----Compiz was already running!----" >> /tmp/compizLog\nfi\ncompiz --replace >> /tmp/compizLog\nstate="$?"\necho "Compiz exited status code: $state" >> /tmp/compizLog\nwhile [[ ! $state -eq 0 || -z "$first" ]];do\n\tsleep 2\n\tif [ $state -eq 0 ];then\n\t\techo "---------Crash--Assumed------------" >> /tmp/compizLog\n\telse\n\t\techo "---------Crash-Detected------------" >> /tmp/compizLog\n\tfi\n\tcompiz --replace >> /tmp/compizLog\n\tstate="$?"\n\tfirst="$state"\n\techo "Compiz exited status code: $state" >> /tmp/compizLog\ndone\necho "-------------End-Session-------------" >> /tmp/compizLog\nif [ 0`pidof compiz``pidof xfwm4` -eq 0 ];then\n\txfwm4 --daemon\nfi\nexit' | sudo tee /usr/local/bin/Compiz
sudo chmod +x /usr/local/bin/Compiz
sudo sed -i "s/    xfce4-session/    Compiz \&\n    xfce4-session/" /etc/xdg/xfce4/xinitrc
touch ~/.Compiz
```
you may want to edit [FONT=courier new]/usr/local/bin/Compiz[/FONT] for emerald, not sure if you need to run a command to launch it

I quit using compiz, you may get some use out of my work

---

### Post by dzontra on 2013-05-14
> **pqwoerituytrueiwoq said:**
> This works flawlessly on 12.10 and 13.04 for launching compiz at login, though compiz is a bit buggy
```
echo -e '#!/bin/bash\necho "-------------New-Session-------------" > /tmp/compizLog\nx=0;\nif [ 0`pidof compiz` -eq 0 ];then\n\twhile [ 0`pidof xfwm4` -eq 0 ];do\n\t\tif [ $x -gt 300 ];then\n\t\t\tbreak\n\t\tfi\n\t\tsleep 0.02\n\t\tx=$(($x+1))\n\t\techo "I know you are going to start xfwm4..." >> /tmp/compizLog\n\tdone\nelse\n\techo "----Compiz was already running!----" >> /tmp/compizLog\nfi\ncompiz --replace &>> /tmp/compizLog\nstate="$?"\necho "Compiz exited status code: $state" >> /tmp/compizLog\nwhile [ ! $state -eq 0 ];do\n\tsleep 2\n\techo "---------Crash-Detected------------" >> /tmp/compizLog\n\tcompiz --replace &>> /tmp/compizLog\n\tstate="$?"\n\techo "Compiz exited status code: $state" >> /tmp/compizLog\ndone\necho "-------------End-Session-------------" >> /tmp/compizLog\nif [ 0`pidof compiz``pidof xfwm4` -eq 0 ];then\n\txfwm4 --daemon\nfi\nexit\n' | sudo tee /usr/local/bin/Compiz
sudo sed -i "s/    xfce4-session/    Compiz \&\n    xfce4-session/" /etc/xdg/xfce4/xinitrc
touch ~/.Compiz
```
you may want to edit [FONT=courier new]/usr/local/bin/Compiz[/FONT] for emerald, not sure if you need to run a command to launch it

I quit using compiz, you may get some use out of my work

I have seamlessly entered your code into my terminal and I have no Improvements.
so I created a simple script on my desktop running "compiz -- replace" so I start it manualy.

Thanks for your help. 
When I find out the problemi will update the post.

---

### Post by pqwoerituytrueiwoq on 2013-05-14
[s]when you login to a xubuntu session it should start with compiz running
can you post the content of [FONT=Courier New]/tmp/compizLog[/FONT]
[/s]
Oh i know what i did wrong, this will make it work
```
sudo chmox +x /usr/local/bin/Compiz
```
i forgot to make the script executable

---

### Post by dzontra on 2013-05-15
It apperas that I have found a solution, It's so simple that it did not cross my mind. 
One side effect I had was when I choose i.e. Scale Addons and reenter the Compiz Settings Manager the settings get deleted and appears like all "older" settings are reseted. 

I googled it for a bit and found a solution: 

> dconf reset -f /org/compiz/


And after I rebooted once aggain with Compiz --replace enabled from startup applications , 
it worked like a charm ! :D  

Apparently that compiz is sensitive on which plugins get initiated before or after others.

Thank you guys for helping me and big thanks to [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") for the script :) 
bthw, how can I mark this as [SOLVED] ?

---

### Post by pqwoerituytrueiwoq on 2013-05-16
[duplicate, please delete]

---

### Post by pqwoerituytrueiwoq on 2013-05-16
instructions cause i am not typing them again: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
If you done have a [FONT=courier new]~/.Compiz[/FONT] file the script will not replace xfwm4, this is useful for the guest account that does not have compiz configured, also when compiz goes to crap and you cant do anything you can disable compiz start by removing that empty file
Opps i posted a old copy of that script, i updated the 1st line of that code box (it starts with echo)
to update that script just rerun the 1st line, don't rerun the third line, that would be bad

---

