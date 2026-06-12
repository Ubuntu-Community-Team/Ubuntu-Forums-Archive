---
title: "terminal command queue"
date: 2008-04-29
forum: General Help
---

### Post by bayonetblaha on 2008-04-29
this is a situation I run into frequently. Let's say I have an apt-get command running that is going to take a long time and I want to leave my computer, but I have just thought of something else I want to install as well. Is there a way to command linux to install package_c when it is done installing package_a and package_b?

---

### Post by Anduu on 2008-04-30
Gah nevermind I just got the actual gist of your question....best bet I think would be to ctrl-c to stop what you were doing and then add whatever other packages you want.

---

### Post by bingoUV on 2008-04-30
> **Anduu said:**
> All you have to do to install multiple packages is list the packages on the same line separated with spaces.

```
sudo apt-get install package-a package-b package-c etc...
```

 In general, semi-colon separated commands should do the trick. Semi colon ends a command, and you can start another after a semi colon. Try  ```
 cd ~/Documents/ ; ls 
```

---

### Post by sdennie on 2008-04-30
In this particular case, you could hit Ctrl-Z in the terminal and then, in the same terminal, type:

```

bg
wait `pgrep apt-get` ; sudo apt-get install blah

```

I didn't actually try that but, I believe it will work.

---

### Post by olejorgen on 2008-04-30
Hm.. maybe you people should *read* the question. No offence :) (not you vor)
```

$ sudo apt-get install <long list>
<ctrl + z>
[<number>]+ Stopped sudo apt-get install <long list>

```
Method 1:
```

$ fg; sudo apt-get install <other packages>

```
Method 2:
```

$ ps
# ...
<pid> <something> <something> sudo apt-get install <long list>
$ bg
$ wait <pid>; sudo apt-get install <other list>

```
You probably want to do this in a root shell though, since sudo will time out while <long list> is installed

---

### Post by sdennie on 2008-04-30
Actually, yes, as olejorgen said, it's entirely likely that sudo will timeout on a long apt-get so, you may not be able to do what you want easily.  You could write a script to wait for a pid as sudo and then execute a command but, that seems dangerous and I wouldn't recommend it.

---

### Post by Anduu on 2008-04-30
> **olejorgen said:**
> Hm.. maybe you people should *read* the question. No offence :) (not you vor)
```

$ sudo apt-get install <long list>
<ctrl + z>
[<number>]+ Stopped sudo apt-get install <long list>

```
Method 1:
```

$ fg; sudo apt-get install <other packages>

```
Method 2:
```

$ ps
# ...
<pid> <something> <something> sudo apt-get install <long list>
$ bg
$ wait <pid>; sudo apt-get install <other list>

```
You probably want to do this in a root shell though, since sudo will time out while <long list> is installed

Hey it is late and I'm sleepy but at least I caught it :p

Anyway thats very useful info there...had no idea you could do that.I'll have to file that away in my notes in case I need it.Thanks :KS

---

### Post by olejorgen on 2008-04-30
> **vor said:**
> Actually, yes, as olejorgen said, it's entirely likely that sudo will timeout on a long apt-get so, you may not be able to do what you want easily.  You could write a script to wait for a pid as sudo and then execute a command but, that seems dangerous and I wouldn't recommend it.
Why whould that be so dangerous? Just make sure the script is owned by root and is non-writable. At least for home use I'd say it's perfectly safe. (not that I'm a security guru ^^)

---

### Post by sdennie on 2008-04-30
> **olejorgen said:**
> Why whould that be so dangerous? Just make sure the script is owned by root and is non-writable. At least for home use I'd say it's perfectly safe. (not that I'm a security guru ^^)

Off the top of my head, I can think of no reason why it's dangerous.  However, it tickles my Spider-Sense and, for me, when it comes to security, that's a good enough reason to not do something.  ;)

---

