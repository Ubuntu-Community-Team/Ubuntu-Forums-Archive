---
title: "script to start modem??"
date: 2008-02-14
forum: General Help
---

### Post by smurphs on 2008-02-14
Hi, can anyone help with a simple script?

Sometimes my modem disconnects from the internet, and to reconnect I have to type: 

sudo pppd call speedtouch 

in a terminal to get it going again. 

How can I create a shortcut to do this for me? Is it possible to bypass the need to enter my password? I need it to be as simple as poss. for my wife!!

Many thanks,

Dylan

---

### Post by amingv on 2008-02-14
You don't need a script, an alias should do nicely.

type in the console:

```
cp ~/.bashrc .bashrc.backup
gedit ~/.bashrc
```

go to the end of that file and add this:

```
###Re-stablish internet connection
alias connect='sudo pppd call speedtouch'
```

In the above you can change "connect" for whatever you want. When you reopen your terminal, just by keying the word you specified you should be able to run this command. Notice this will only work under your session.

As for automating the password, I don't know a secure way to do that.

---

### Post by hyperair on 2008-02-14
Run this command:
```
sudo visudo
```

Then at the bottom of the file, add this line:
```

<username> ALL = NOPASSWD: /usr/sbin/pppd

```

This authenticates your user (without a password) to run sudo /usr/sbin/pppd without the need for keying in a password. Not very secure, but not exactly very insecure either. 

Since you want it as simple as possible, you should just create a launcher that contains this command "sudo pppd call speedtouch" or something of that sort in your panel. Then just tell her to click it.

---

### Post by smurphs on 2008-02-14
Thanks guys, the alias is a neat trick, but my wife really needs a button!!

I've resolved the password problem thanks to the advice given, but am having problems with my launcher.

I've created a launcher and put 'sudo pppd call speedtouch' in the command box, and have changed the type to 'application in terminal'. Unfortunately it doesn't seem to do anything - a terminal flicks up and disappears almost instantly, and it doesn't connect. 

Any ideas?

---

### Post by hyperair on 2008-02-14
Why don't you see if manually doing "sudo pppd call speedtouch" really works. =\

---

### Post by smurphs on 2008-02-14
Thanks - sorted it now. The problem was that if you try to reconnect too quickly you get 

Plugin pppoatm.so loaded.

But with the launcher it didn't pause to display the message, so it seemed as if nothing was happening.

cheers,

dylan.

---

### Post by directcharitycontribution on 2008-02-15
thanks. fed up with typing password, and was using terminal to call as well.

 i also considered over complicated scripting  to then discover using application launcher. now have a number of commands on the dropdown. the alias is nice idea. 

anybody know how to remove commands from app launcher dropdown?

@OP you should mark this [SOLVED]!

---

### Post by hyperair on 2008-02-15
App launcher drop down? What do you mean? Perhaps a screenshot can clarify your question.

---

### Post by directcharitycontribution on 2008-02-16
or internet search

---

