---
title: "Many warnings when using sudo gedit"
date: 2016-10-20
forum: General Help
---

### Post by tonma on 2016-10-20
I am opening gedit with sudo, to be able to save it in places I have no permissions to as a regular user, but I see many warning running in the opened terminal window while working in the gedit

The files seems to be OK, working as intended after I save them. But I wonder if those warnings may effect some things and cause problems I have yet to encounter?

---

### Post by mastablasta on 2016-10-20
DO NOT USE SUDO WITH gedit or any GUI app !!!!! this is the issue: [SIZE=2][http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[/SIZE]
gksu or gksudo was the right app to use, however they are both deprecated. 

use pkexec instead 

```
man pkexec
```

or read more here on the topic: [SIZE=2][http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)


edit: one more thing - gksudo will also throw out a bunch of warnings and such. there is nothing wrong with them
[/SIZE]

---

### Post by vasa1 on 2016-10-20
> **mastablasta said:**
> ...
edit: one more thing - gksudo will also throw out a bunch of warnings and such. there is nothing wrong with them

Opening gtk apps via the terminal could generate a lot of messages...
[Why are there so many console messages from GTK+ applications?]("http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications/422400#422400")

---

### Post by tonma on 2016-10-20
Thanks, is there a way to see if I caused any damage in those time I ran sudo gedit? And is it fix-able?

---

### Post by yetimon_64 on 2016-10-20
The main problem you are likely to run into is the file ~/.ICEauthority becoming owned by root. If that happens you can be blocked from logging into your users desktop. That file should be owned by your user name and have 0600 permissions. If you can currently log in to the desktop then it is highly likely you have been lucky so far.

If you don't want to install gksu (I do recommend you try the webupd8 links provided earlier and try using pkexec as gksu is deprecated) or if you continue to use sudo, ensure you use the "-H" switch with it. For example ...
```
sudo -H gedit
``` is safe to use. From man sudo ...
```
     -H, --set-home
                 Request that the security policy set the HOME environment variable to the home
                 directory specified by the target user's password database entry.  Depending on the
                 policy, this may be the default behavior.

``` Using this switch forces the root account to use its own home folder thus your home folder hidden files would be safe. You won't do damage every time you use sudo, but when damage does happen it can be drastic/scary for an inexperienced user. The faults it causes are relatively simple to fix from a tty terminal (eg. using "ctrl + alt + F1") and issuing a few commands to reset any files affected; though it is smarter to use either pkexec or if using sudo the "-H" switch with it to avoid the hassles in the first place. 

Regards, yeti.

**Edit:** you can click on the next thumbnail to see an example of the use of "sudo" and "sudo -H" on a graphical app (gnome-terminal). I use a custom prompt with colour coding of the user name on my installation, root user is supposed to always show in red. I issued the command "sudo gnome-terminal" in the first terminal and "sudo -H gnome-terminal" in the second (both on the left). 
In the resulting terminals on the right hand side I issue the command "echo $HOME" to demonstrate what the root terminal is using for the HOME environment variable. The root terminal on the top right is potentially dangerous to use, the root user is still showing in green and the HOME variable is showing as my normal users home folder. The bottom right terminal launched with "sudo -H" is perfectly safe to use, root is showing in red and the HOME variable is showing as /root (which is correct and safe). Cheers.
[ [IMG]https://dl.dropboxusercontent.com/u/30874719/UF/using-sudo-with-gnome-terminal_thm.png[/IMG]]("https://dl.dropboxusercontent.com/u/30874719/UF/using-sudo-with-gnome-terminal.png")

---

### Post by Impavidus on 2016-10-20
> **yetimon_64 said:**
> The main problem you are likely to run into is the file ~/.ICEauthority becoming owned by root.
Same story for ~/.Xauthority. It needs the same permissions and ownership as .ICEauthority.

---

### Post by Herman on 2016-10-20
Shouldn't the operating system be smart enough to know which are the graphical applications and seamlessly invoke rules when the root user is trying to run one of them to run it from the root account?

---

### Post by QIII on 2016-10-20
> **Herman said:**
> Shouldn't the operating system be smart enough to know which are the graphical applications and seamlessly invoke rules when the root user is trying to run one of them to run it from the root account?

So the OS should decide for the user what the user is trying to do?

---

### Post by Herman on 2016-10-20
That's what an operating system is for isn't it? Doing things for the user.

---

### Post by MartyBuntu on 2016-10-20
> **QIII said:**
> So the OS should decide for the user what the user is trying to do?

Sometimes, that can be helpful.

---

### Post by yetimon_64 on 2016-10-20
> **Impavidus said:**
> Same story for ~/.Xauthority. It needs the same permissions and ownership as .ICEauthority.

+1, yes, I was mainly remembering .ICEauthority as I got hit with that problem early on in in my Ubuntu journey (if I recall correctly, around the time of Jaunty) using straight sudo and graphical apps. 

I found it was a pretty easy fault to fix from a tty terminal at the time; a "sudo chmod 0600" and a "sudo chown <user>:<user>" command on the file from a tty prompt and I was able to get back in with no further problems. [B]

Edit:[/B] I am actually unsure now if I had to use sudo back then with those two commands when fixing the problem, I *_think_* I did, with the file being taken over by root, though not sure now if I did or didn't at the time. I haven't actually had to deal with the problem myself for about 6 or 7 years; I have either used gksu or sudo -H ever since then.

I will admit I near had a heart attack at the time with the desktop failing to load just after a fresh install though; google and these forums came through with a fix for me thankfully :).

@ OP, both of those files can be problematic if root changes ownership of them.

---

### Post by Herman on 2016-10-20
How many programs would be in the repositories for Ubuntu and it's derivatives and do we all know what each one does and whether or not it's a graphical program?
What about new users? Is there a list somewhere of text editors to warn them which ones are graphical and should they be expected to have it pasted on their wall behind their monitors?
How many tutorials are out there on the internet which could be telling users to use sudo for graphical applications?
Wouldn't it be easier to make the operating system adapt to the needs of its users rather than the other way around?

The operating system should have a built-in database where it can look up whether the program about to be run by sudo is graphical or not and automatically switch to gksudo without the user needing to worry about it.
Or, for a workaround, a deamon could run every so often in the background and fix the ownership of files like ~/.Xauthority or .ICEauthority in the users home directory.
How hard would it be?

---

### Post by Frogs Hair on 2016-10-20
This thread is drifting into a discussion rather than addressing the OP's concern about gtk warnings in the terminal. Please post accordingly.

---

### Post by Herman on 2016-10-21
> This thread is drifting into a discussion rather than addressing the  OP's concern about gtk warnings in the terminal. Please post  accordingly.
Okay, I am sorry, you are right I did get a little carried away. Sorry.
> I am opening gedit with sudo, to be able to save it in places I have no  permissions to as a regular user, but I see many warning running in the  opened terminal window while working in the gedit

The files seems to be OK, working as intended after I save them. But I  wonder if those warnings may effect some things and cause problems I  have yet to encounter?                 
I remember when aysiu wrote the web page here: [SIZE=2][http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) and before that I don't think many of us knew they needed to use gksudo. 
It caused quite a still here in Ubuntu Web Forums at the time. Before that I think most of us just used sudo for everything.[/SIZE]
I sometimes forget or don't bother to use gksudo myself and I have never really noticed  any serious problems and I have been using Ubuntu almost since it first  came out.
Maybe I have just been very lucky for all these years but I haven't really noticed any serious problems, (just my opinion).
I wouldn't bother re-installing or anything because of it. 
However, it would probably be best to do what the others said and use sudo when we're supposed to and gksudo when we're supposed to I guess. I wouldn't like to be accused of giving bad advice.
> Thanks, is there a way to see if I caused any damage in those time I ran sudo gedit? And is it fix-able?
Later I will make a fake user account in my own OS and try some experiments and see if I can detect the effects of wrong use of sudo using the ls -la command.
If I can detect changes in file ownership and permissions I will note then and then see if I can repair the damage with some chown commands.
It's quite possible that there will be an easy way to fix whatever problems inappropriate sudo can cause.
Unless somebody beats me to it I'll post back if I learn anything interesting.
Regards from Herman :)

---

### Post by mastablasta on 2016-10-21
> **Herman said:**
> Shouldn't the operating system be smart enough to know which are the graphical applications and seamlessly invoke rules when the root user is trying to run one of them to run it from the root account?

this debate as well as what to use going forward was in another thread. i originally wanted to seek that one out, but couldn't remember the exact title. i just remembered the pkexec option to be a good one.

for 2017 it is planned what you mentioned. GUI apps should work with pkexec then.

note that kdesudo is still available in Kubuntu (and KDE distros). not sure if it is the same thing as gksudo.

as for the messages they are really often spewn out when running GUI apps from terminal (as indicated).

---

### Post by Herman on 2016-10-25
I found an old hard drive lying around and made a clean install in it for experimenting with.

The quickest and easiest way I have found so far to check file ownerships in your entire /home/username directory is to use the 'tree' command.
```
sudo apt-get install tree
```
The following command will list files up to 3 levels deep in your /home/username directory, 
The 'tree'command will show the ownership of each file, (username or root).
```
tree -L 3 -u -a
```
change the 3 to 4 or 5 or 6 if you want to do deeper.
Use a smaller number for looking shallower and having less output.

If you want the output to go straight to a plain text file for your record keeping you can do something like this,
```
tree -L 6 -u -a > 2016_10_26_home_user_file_ownership_list
```
A person could do that in a new installation and then keep it for future comparisons.
You can use the search function on gedit to look for each instance of the word 'root' if you want. (Or grep).

If you're in a hurry and you don't want such a large list only want to quickly see which files are owned by root:
```
tree -L 6 -u -a | grep 'root'
```
There's no guarantee that all files owned by root will be harmful. That would need to be assessed on a case by case basis.

---

