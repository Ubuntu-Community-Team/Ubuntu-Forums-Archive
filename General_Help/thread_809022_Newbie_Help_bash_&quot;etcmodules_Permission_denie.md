---
title: "Newbie Help: bash: &quot;/etc/modules: Permission denied&quot;"
date: 2008-05-27
forum: General Help
---

### Post by shaggy1054 on 2008-05-27
Hey all, 

I've been having wireless issues, and since I have the atheros chipset, I was hoping to use Madwifi to solve them. I followed the steps in this thread: 

[http://ubuntuforums.org/showthread.php?t=705386](http://ubuntuforums.org/showthread.php?t=705386)

(Paris Heng's post)

and everything worked perfectly, until I reached the last step, consisting of:

echo "Add ath_pci to the /etc/modules"
CODE=ath_pci
echo $CODE >> /etc/modules 

when I type the last part in, I get 

bash: /etc/modules: Permission denied


now, I've tried typing su <username> and then my password beforehand... that didn't help. I've tried putting sudo in front of the echo thing, and that didn't work either. What am I doing wrong here?

---

### Post by kesman on 2008-05-27
Maybe you should try to understand what the commands to instead of just copy/pasteing them. Have you checked if somehow your wireless could be enabled from system -> administration -> hardware drivers?

It shouldn't give you permission errors if you type:
```

sudo echo $CODE >> /etc/modules

```
then it promts for your password which you must type even though it isn't shown.

---

### Post by shaggy1054 on 2008-05-27
Yeah, sorry about the whole not understanding thing. One of the things that attracted to me about linux was that even though it was very complicated (from a former windows user's perspective), there was an awesome community that would help, and that most fixes could be solved by copy/pasting stuff into the command line. So, I'm still trying to figure everything out, but for now I need my wireless working better.

In any case, I tried what you pasted, even though as I mentioned I had already tried it before. It doesn't prompt me for a password, it just says permission denied. That's pretty much where I'm stuck, and I'm trying to figure out why it won't let me do this. Possible explanations?

In case anyone else wants to try, this is the copy/paste from the terminal: 

nate@caracol:~$ echo "Add ath_pci to the /etc/modules"
Add ath_pci to the /etc/modules
nate@caracol:~$ CODE=ath_pci
nate@caracol:~$ sudo echo $CODE >> /etc/modules 
bash: /etc/modules: Permission denied
nate@caracol:~$

---

### Post by mali2297 on 2008-05-27
Make it
```

sudo -i
echo "ath_pci" >> /etc/modules
exit

```

If you want some kind of explanation of why it does not work to put sudo in front of the echo line, see [here]("https://help.ubuntu.com/community/RootSudo#head-a1a6136e349bca8bd739ef01ebe7a02c65007bd6") about redirecting output.

---

### Post by shaggy1054 on 2008-05-27
Thanks for the help, it seems to have worked, even if I can't understand that linked explanation as to why. One question, though. From what I understand, the command I was trying to run was copying something to the /etc/modules folder... which doesn't exist insofar as I can see. What gives?

---

### Post by mali2297 on 2008-05-27
> **shaggy1054 said:**
> Thanks for the help, it seems to have worked, even if I can't understand that linked explanation as to why. One question, though. From what I understand, the command I was trying to run was copying something to the /etc/modules folder... which doesn't exist insofar as I can see. What gives?

The command is supposed to append the line
```

ath_pci

```
to the end of the file /etc/modules. Didn't it work?

Check with the command
```

cat /etc/modules

```
in the terminal. It should show you the content of the file, if it exists.

(Of course, a more newbie-friendly solution would have been to open the file in an editor, e.g. *gksudo gedit /etc/modules*.)

---

### Post by shaggy1054 on 2008-05-27
Yeah, worked perfectly - my wireless connection now automatically loads "ath_pci" as the driver, which I imagine is the point of the whole operation, right? I thought it was a directory or something and looked for it to no avail, but if it's a file I guess that makes sense. Your suggested check showed it appended successfully, so we're all good there. Only problem now is that the latest set of downloads I got from the ubuntu update thing caused my wireless performance to go to **** (literally; before updates, fine, after, slow as hell and very unreliable in terms of locations in my house that formerly worked). That's another problem for another thread, though, and before I do anything there I'm going to make sure it's not a router problem or something. 

In any case, thanks guys. Solved!

---

### Post by ezramorris on 2008-05-31
> **shaggy1054 said:**
> Thanks for the help, it seems to have worked, even if I can't understand that linked explanation as to why.

Root is the superuser/administarator/user_that_can_do_anything.

Basically, putting sudo at the start of the line in question just made the program "echo" run as root and not the saving to /etc/modules, which was where it was really needed.

Running sudo -i logs you in as root, meaning every command typed is run as root (including saving the text to a file).

Hope this helps.

---

