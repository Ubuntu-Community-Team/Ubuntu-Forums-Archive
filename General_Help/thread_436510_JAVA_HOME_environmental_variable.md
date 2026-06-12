---
title: "JAVA_HOME environmental variable"
date: 2007-05-07
forum: General Help
---

### Post by qzak on 2007-05-07
I have Java installed correctly. 

I have set the JAVA_HOME environmental variable using
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00/

And this works but Everytime I close the terminal window and open a new one it forgets about the JAVA_HOME variable and gives me the following error: Perhaps JAVA_HOME does not point to the JDK.

How can I set this variable so that it will remember where to find JAVA_HOME?

---

### Post by taurus on 2007-05-07
Try adding that line

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00
```
to your ~/.bashrc.

```
gedit ~/.bashrc
```
Then, either run

```
source ~/.bashrc
```
or log out and back in again.

---

### Post by qzak on 2007-05-07
thanks a million, that worked but do I have to do this for every evironmental variable I want to setup?

---

### Post by taurus on 2007-05-07
Nope as long as you use /bin/bash shell.

---

### Post by qzak on 2007-05-07
I know how to change the type of shell I use in Ubuntu, but dont know much about the difference between the shells. Do you sugest using a shell other than bash?

---

### Post by adam-mada on 2007-05-10
So, I've got big throuble... I followed those up-said stept and instead of running this code: source ~/.bashrc  , I've written it the bashrc code and restarted the computer. Now, i have no terminal signup, so I cannot run any command in it. Pleace tell me what can i do! It was my fault, I know that but I was in a rush and now I have no ideea how to set it back as long as i can't run any command in the Gnome terminal.

---

### Post by taurus on 2007-05-10
> **adam-mada said:**
> So, I've got big throuble... I followed those up-said stept and instead of running this code: source ~/.bashrc  , I've written it the bashrc code and restarted the computer. Now, i have no terminal signup, so I cannot run any command in it. Pleace tell me what can i do! It was my fault, I know that but I was in a rush and now I have no ideea how to set it back as long as i can't run any command in the Gnome terminal.

Not sure what you mean you have written it to bashrc?  Do you mean you have created a ~/bashrc with that line about setting java environment?

---

### Post by adam-mada on 2007-05-13
Yes, I've opened bashrc and i've written a new line with this command: "source ~/.bashrc". so, starting from taht time, I can not use the Gnome Terminal. What should I do? how can I open the bashrc to delete that line?

---

### Post by taurus on 2007-05-13
Yes, remove that line.  And by the way, there shouldn't be bashrc in your $HOME directory.  There are .bashrc, .bash_profile, .bash_history, etc.

---

### Post by adam-mada on 2007-05-14
I don't know how to open bashrc since my terminal is not working.  Where can I find that bashrc file and how can I remove that line from it?

---

