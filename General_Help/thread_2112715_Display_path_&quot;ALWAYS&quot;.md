---
title: "Display path &quot;ALWAYS&quot;"
date: 2013-02-05
forum: General Help
---

### Post by bigbankclub on 2013-02-05
Is there a way to display the path all the time? Meaning - command pwd in Terminal displays:

```
/home/ubuntu/Desktop
```I want the Terminal to display:

```
 ubuntu@ubuntu-VirtualBox:~/home/ubuntu/Desktop$
```instead of:

```
 ubuntu@ubuntu-VirtualBox:~/Desktop$
```

Sure you can press command "pwd" - but I want it there all the time. Any suggestions?):P

---

### Post by Cheesemill on 2013-02-05
All of the settings for your prompt are held in the PS1 environmental variable which lives in your ~/.bashrc file.

Look for the line that begins 'PS1 ='  and then replace the \w (near the end of the line) with `pwd`.

For example, before...
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\][COLOR=Red]\w[/COLOR]\[\033[00m\]\$ '
```and after...
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\][COLOR=Red]`pwd`[/COLOR]\[\033[00m\]\$ '
```

---

### Post by omeomi on 2013-02-05
You should check whether you are using the color prompt or not because the above mentioned line is for the colored version, the non-colored version is found approx. 2 lines down (they are both contained in an IF-statement).

For more info on customizing the Bash prompt: [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

---

### Post by sudodus on 2013-02-05
It does by default. ~ means /home/your-user-id

You can see that if you change directory to for example /etc

```
sudodus@April-2008-precise:**[COLOR=SeaGreen]~[/COLOR]**$ cd /etc
sudodus@April-2008-precise:**[COLOR=SeaGreen]/etc[/COLOR]**$
```

---

### Post by Habitual on 2013-02-05
```
\w
```

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

