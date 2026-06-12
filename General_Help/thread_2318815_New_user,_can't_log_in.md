---
title: "New user, can't log in"
date: 2016-03-29
forum: General Help
---

### Post by jdkcarlson on 2016-03-29
I have an Acer R471-T3 trying to run Trusty Tahr, but I can't log in anymore. I think it has something to do with xconf, which I was trying to change to fix a different problem using advice I found on the Ubuntu stackexchange. It didn't exist before, but I tried to create it with vi in order to fix a separate problem. There are still some swap files from these attempts living in /tmp but I've moved those files that I tried to create.

To clarify, I *can* login through the terminal, but the GUI won't let me. My username appears and the window where one types in the password appears, with the noise that the system makes when you're trying to do something you shouldn't. If I type in the wrong password, it tells me I've done so via red text and sends me back to this window. If I type in the correct password, though, it makes the noise again, but gives me no text warning, and bounces me back to this window. This means, to me, that the password hasn't changed, but something else is going wrong. 

If I Ctrl+Alt+F1, login goes fine. Doing "sudo startx" after this sends me to my desktop, but without any of the menus to the side. I should mention that earlier, misinterpreting some advice for yet another problem (which I can explain later if needed but may be transient or irrelevant), I did "sudo startx" from within the GUI, and it sent me to this menuless desktop. I have not gotten back to the regular GUI with my full abilities since.

At a friend's prompting, I tried the following

```
cd /home/USERNAME 
mv .Xauthority .Xauthority.old 
touch .Xauthority 
chown USERNAME: USERNAME .Xauthority

```

but without success.

As you might be able to tell, I am a new user with sharply limited technical ability and intuition, so many thanks in advance for your patience.

---

### Post by Bashing-om on 2016-03-29
jdkcarlson; Hoooo Boy ....

Bad Bad bad :
> 
If I Ctrl+Alt+F1, login goes fine. Doing "sudo startx" after this sends me to my desktop,

running 'sudo' for anything on your /home causes "root' to take over ownership rights and "YOU" have none .

So we now have at least 2 issues ..
1) ownership and permission issues with your /home
2) /etc/X11/xorg.conf  file miss-directing the graphic's driver.
The ownership issue is the 1st priority:
what returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home/
ls -al /home/<USERNAME _here>

```

'startx' has limited applications in today's environments .. most likely does not apply in your use case .
What DeskTop are you running ? If lightdm is a factor, need to also examine:
```

ls -al /var/run/lightdm/root/

```

Once "you" have access restored to your /home we look at the graphic's driver issue.

[INDENT][INDENT][INDENT]there is that way that seems right
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdkcarlson on 2016-03-30
I'm typing this on a tablet since my old laptop won't start up. I'll write NAME for my username and DATE for the time

First command yields 

-rw------- 1 root root 149

Second

-rw------- 1 NAME NAME 11308

Third

```
drwxr-xr-x  3 root root 4096 DATE .
drwxr-xr-x 23 root root 4096 DATE ..
drwxr-xr-x 27 NAME NAME 4096 DATE NAME
-rw-r--r--  1 NAME NAME 0 DATE .Xauthority

```

Fourth gives a big list. The only ones that have "root root" instead of NAME NAME are 

..
.dbus
.gvfs
.Xauthority

I do have lightdm. The last line of code you provide gives

```

drwx------ 2 root root DATE .
drwx--x--x 3 root root DATE ..
-rw------- 1 root root DATE :0

```

Thanks!

---

### Post by Bashing-om on 2016-03-30
jdkcarlson; Welll ...

Let's see how far we get ;

Put the access rights back to "you" :
```

sudo chown <USERNAME>:<USERNAME> .ICEauthority
sudo chown <USERNAME>:<USERNAME> .Xauthority

```

Now can you boot to the GUI ?

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2016-03-30
Got GUI access back! 

What else should I try to change?

... I have a new problem. I'll post it somewhere else I guess. Basically I see the loading dots . .. ... and the screen goes black without turning off and stays that way.

---

### Post by Bashing-om on 2016-03-30
jdkcarlson; Hummm ...

Graphic's driver ?? From the grub boot menu, what results when selecting a recovery kernel ?

Then we consider RE-installing the graphic's driver.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdkcarlson on 2016-04-21
Hi, the reason I haven't responded is that this particular problem seems to have gone away without any explanation (and I have so many other new-user problems still). I've since used a recovery kernel for at least one other problem, so I know it is a good option to keep in mind. 

Thank you so much for your help!

---

### Post by Bashing-om on 2016-04-21
jdkcarlson; Ho Kay !

Glad things have worked out in this respect. As the original query is no longer of relevance :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

These new issues, as you need guidance, open a new thread to address any.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2016-04-21
Will do!

---

