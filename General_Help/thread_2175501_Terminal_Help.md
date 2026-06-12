---
title: "Terminal Help"
date: 2013-09-19
forum: General Help
---

### Post by xExekut3x on 2013-09-19
For some reason, my Terminal isn't working properly. Whenever I open it, there is just the cursor. My user name and hostname are not there. I can type, but no commands work. The only way to get it to work is to press "ctrl-c", then everything works fine. The terminal works fine when pressing "ctrl + alt + F1," and I can return to the desktop with "ctrl + alt + F7."

I think the problem started after I installed another terminal emulator out of the Software Center. I think it was the "Terminator." I've uninstalled it, didn't help. I uninstalled "Terminal" and re-installed, didn't help.

This is after a fresh install and after fully updating.

Anybody ever experience this problem and know how to fix it? I've already got my desktop customized the way I want it and it's a pain to get my wifi NIC driver installed so I'd rather not have to re-install Ubuntu.

---

### Post by papibe on 2013-09-19
Hi xExekut3x.

Did you edit your bash config files?

Could you post the result of these commands?
```
diff ~/.bashrc /etc/skel/.bashrc 

diff ~/.profile /etc/skel/.profile
```
Regards.

---

### Post by xExekut3x on 2013-09-19
I did, yes. I installed Ruby on Rails. Here are those outputs:

> 115,118d114
< 
< PATH=$PATH:$HOME/.rvm/bin # Add RVM to PATH for scripting
< source ~/.profile
< [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"


> 23d22
< [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"


---

### Post by xExekut3x on 2013-09-19
I commented out the things I added, but left in what RVM added. It's working right, now. Thanks.

---

### Post by papibe on 2013-09-19
Thanks.

Try reverting back to the original files, and see what happens.

First backup what you have:
```
mv  ~/.bashrc  ~/.bashrc.old

mv  ~/.profile  ~/.profile.old

mv  ~/.bash_logout  ~/.bash_logout.old
```
Then copy the files from skel to your home directory
```
cp -v /etc/skel/.[bp]* ~/
```
Now open a terminal and see how it goes.

Let us know how it went.
Regards.

---

