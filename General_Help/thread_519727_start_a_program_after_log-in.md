---
title: "start a program after log-in"
date: 2007-08-07
forum: General Help
---

### Post by muddymind on 2007-08-07
Hi!

I have a workstation with dynamic guest accounts (taken from an AD) and I would like to launch a simple program at each log-in with root permission... Is that possible? How can I do it?

[]

---

### Post by muddymind on 2007-08-07
anyone? :(

---

### Post by Majorix on 2007-08-07
You could go ahead and edit /etc/rc.local . You shouldn't include sudo.

Like
```
firestarter
```

and NOT
```
sudo firestarter
```

---

### Post by muddymind on 2007-08-08
Many Thanks :)

EDIT: It didn't work...

my /etc/rc.local looks like this:

```
java -jar "/usr/local/proxylauncher.jar"

exit 0
```

But when I login it shows nothing :S help plz...

---

### Post by muddymind on 2007-08-08
~~bump~~

---

### Post by muddymind on 2007-08-08
help plz... :(

---

### Post by mcduck on 2007-08-08
To start something after log-in, just go to System/Preferences/Sessions and add the command to the list of startup programs.

---

### Post by muddymind on 2007-08-08
> **mcduck said:**
> To start something after log-in, just go to System/Preferences/Sessions and add the command to the list of startup programs.

And if that user don't have administrator privileges will it run with administrator privileges?

[]

ps- I'm having problems launching java programs... they don't work if I try to make
```
gksu java -jar "bla/bla.jar"
```

Why is that?

---

### Post by nichipet on 2007-08-08
> **muddymind said:**
> 
ps- I'm having problems launching java programs... they don't work if I try to make
```
gksu java -jar "bla/bla.jar"
```

Why is that?

Is this from a program or script that starts on login?

If so, I think it may be waiting for a password from the user. You may only be able to do this through a shell script which insecurely contains the user's password. Even then, the script may need to be customized for each user.

If this is when you login and then enter the terminal and try it, can you give us the output?

---

### Post by muddymind on 2007-08-08
> **nichipet said:**
> Is this from a program or script that starts on login?

If so, I think it may be waiting for a password from the user. You may only be able to do this through a shell script which insecurely contains the user's password. Even then, the script may need to be customized for each user.

If this is when you login and then enter the terminal and try it, can you give us the output?

thanks for the tip ;)

I found a workaround to the gksu problem:

```
gksu "java -jar "bla/bla.jar""
```

I wanted to launch it (without gksu "") in /etc/rc.local or in /usr/share/xsessions/gnome.desktop but it doesn't work... why is that? I need to launch it there to have administrative privileges :S

---

### Post by muddymind on 2007-08-08
I found that nothing that I put in /etc/rc.local works :S Does anyone have a clue why that happens?

---

### Post by nichipet on 2007-08-08
Let me see if I understand. You want a program to launch with administrative privileges for every user when they log in, whether they are allowed to administer the system or not, correct?

If that were possible, someone could write a malicious script that uses administrator privileges (especially if it can be done where users do not need to enter their passwords for the program/script), put it into /etc/rc.local and it will run every time anyone on the system logs in. That would be a serious security flaw, which is probably why it is either impossible or at least very difficult to set up.

---

### Post by muddymind on 2007-08-08
But U need administrative privileges to write in rc.local... I don't think It would be a flaw... All You need to do is to be careful of what you launch from there and to make sure that nothing that is launched there can't be overwritten by anything else... anyway, how can I make it work?

[]

---

### Post by nichipet on 2007-08-08
As far as running the program on login goes, anacron may do what you want. I'm not sure if it runs a set period of time after the computer turns on or after login. If it's login, it should fit the bill. You'll still have the administrator privileges problem, though.

Here is a page from RedHat's manual on how to use anacron: [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-autotasks-anacron.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-autotasks-anacron.html)

---

### Post by muddymind on 2007-08-08
hum... anacron seems interesting but it doesn't solve my needs...

In /etc.rc.local there's the following text:

```
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

```

could someone explain to me what are they refering to execution bits?

[]

---

### Post by nichipet on 2007-08-08
Permissions. Try:

```
sudo chmod u+x /etc/rc.local
```

---

### Post by muddymind on 2007-08-09
well... i managed to let the domain users to execute just 1 sudo comand by ading the following line to /etc/sudoers :
```
%domain\ users ALL = NOPASSWD: /usr/bin/java -jar /bla/bla.jar
```

but now it gives me this error when I try to launch it:
```
teste@linux-ws:~$ sudo /usr/bin/java -jar /bla/bla.jar 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:91)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at java.awt.Toolkit.getEventQueue(Toolkit.java:1678)
        at java.awt.EventQueue.invokeLater(EventQueue.java:954)
        at proxylauncher.Mainwindow.main(Mainwindow.java:198)
```

This only happens if the user is underprivileged :(

How can I solve this problem?

[]

---

