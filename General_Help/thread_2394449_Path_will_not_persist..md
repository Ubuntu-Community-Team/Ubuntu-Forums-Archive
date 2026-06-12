---
title: "Path will not persist."
date: 2018-06-16
forum: General Help
---

### Post by LinuxAlexs on 2018-06-16
Hello I run this:

```
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools

source ~/.profile

echo $PATH
```

Returns:

*/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-8-oracle/bin:/usr/lib/jvm/java-8-oracle/db/bin:/usr/lib/jvm/java-8-oracle/jre/bin:/home/alex/Android/Sdk/tools:/home/alex/Android/Sdk/tools/bin:/home/alex/Android/Sdk/platform-tools*

Next time I reboot the settings are lost and I have to do it again.
How can I make this persist, I thought source ~/.profile would do it.

Thanks...

---

### Post by TheFu on 2018-06-16
No. You need to put the changes into the startup file that your shell uses.  ~/.profile is used by Bourne shell and descendants.  Usually for bash, you'd want to put it into the ~/.bashrc.

You don't need to "source" the file except immediately after modifying it.  If you logout and login, a new session will be created and the updates will be inherited.

Which files are included in the startup process is different based on the shell AND if you've modified any already included files.

For example, I use a ~/.bash_aliases file for .... aliases.   It won't be used, unless one of the startup files "sources" it.  My ~/.bashrc does this.   **source ~/.bash_aliases**   For compatibility a . (period) can be used instead of saying "source" ... 
**. ~/.bash_aliases**
is the same.

The manpage for your shell should have a startup section that explains this.   Which shell you are using is part of the password entry.   On most home Linux systems, that data is stored in the /etc/passwd file. In most businesses or places that use LDAP, you'll want to check the password entry using **getent passwd** .

I'm not certain I explained it in a way that you'll understand.  If it isn't clear  enough, ask.

Oh ... and referencing HOME or ~/ might not work on all systems for non-interactive uses.

---

### Post by LinuxAlexs on 2018-06-16
Thanks, so I rebooted and ran this

```
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools

**source ~/.bashrc**

echo $PATH
```

Returns:

*/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-8-oracle/bin:/usr/lib/jvm/java-8-oracle/db/bin:/usr/lib/jvm/java-8-oracle/jre/bin:/home/alex/Android/Sdk/tools:/home/alex/Android/Sdk/tools/bin:/home/alex/Android/Sdk/platform-tools*

Same issue after rebooting.
Sorry if I'm misunderstanding

---

### Post by LinuxAlexs on 2018-06-16
Ah nevermind I see I have to:
gedit ~/.bashrc

.. and paste it at the end. Thanks!

```
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

---

### Post by TheFu on 2018-06-16
Yes, you have to put the commands into a file that gets run at login.  No need to reboot. Rebooting is a Windows thing and seldom needed on Unix systems.  In fact, when you understand this stuff better, you won't even need to logout/login.

Also, you might want to test the PATH to see if those things are already in it, since the code above might get called more than once, adding those settings again and again and again.   But you should be careful using $HOME ... since it might not work on all platforms for non-interactive logins.

---

### Post by LinuxAlexs on 2018-06-17
Many thanks.

---

