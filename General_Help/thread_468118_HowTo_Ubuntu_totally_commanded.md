---
title: "HowTo: Ubuntu totally commanded ?"
date: 2007-06-08
forum: General Help
---

### Post by nqsonk9 on 2007-06-08
Hi Guys, I've just had my very first coffee cup of Ubuntu :popcorn:.

I'm really fond of controlling my Ubuntu totally by keyboard, by Run and Terminal commands, i means. So i'm looking for a way to learn the command for each action I do, each application I run. (access command to the synaptic manager, the system monitor ... like that).

Can you guys pls help me out of this, thks :D

---

### Post by EndPerform on 2007-06-08
Instead of Synaptic, you'd use aptitude (or apt-get).  Here are some examples of how to use aptitude:

Install a package named foo:
```
sudo aptitude install foo
```

Update the repository software list:
```
sudo aptitude update
```

Update currently installed packages:
```
sudo aptitude upgrade
```

Hope that helps some :)

---

### Post by Thomar on 2007-06-08
You can set up lots of keyboard commands in Ubuntu.

Go to System>Preferences>Keyboard Shortcuts, and you'll find a huge list of shortcuts you can set.  I've set Show the panel menu to the Windows key, as a simple example.  Be careful, I'm not sure how to reset defaults on this list, just try commands before you change what their keys are.

---

### Post by nqsonk9 on 2007-06-08
Thanks
I've install Beryl on my machine and it works pretty cool, it provides some more shortcut and command that impress me. 

But that's not just enough. I'm looking for a way to get the commands for every action I do. 

:pI've found a good way to do that: add laucher of that application to panel, then property it you will get the command that work fine for both Run and Terminal services :):p

But how about some system command? For example, how can I open the logout box by my keybroad? (shortcut key form Ubuntu preference just not works for me :'(

---

