---
title: "Fiest Brings up error on login!"
date: 2007-06-13
forum: General Help
---

### Post by Rhyn W on 2007-06-13
Hi I Booted my Feisty Fawn up this morning,

Horror I've done something to it .It gave me this error

User's $HOME/dmrc file is being ignored. This prevents 
the default session and language from being saved.
File should be owned by user and have 644 
permissions. Users $HOME directory must be owned
by user and not writable by other users.

With an Ok Symbol on the bottom right.

Anyone know what to do?

I did try and installl a game off the net called airattack.
I Extracted it to a sub folder in my home directory, the game couldn't launch for some or other reason.
and now I get this today.

Anybody know what to do? 
I haven't clicked the OK button yet.

---

### Post by jd65pl on 2007-06-13
Boot in recovery mode. Check the permissions on your home directory with
```
 ls -l /home 
```
Change the permissions as appropriate with chmod.

---

### Post by Rhyn W on 2007-06-13
Chmod: missing operand

Try Chmod --help
for more info

---

### Post by jd65pl on 2007-06-13
Do you know what permissions you want to set? You need to include them in chmod you can't just type it without any instruction!

Do ```
man chmod
```

Or search the forums / google to find more about chmod.

If you need more help working it out post back.

Thanks

J

---

### Post by Rhyn W on 2007-06-13
No I don't know anything about permissions,
I'm the user only user. Its my Pc and its ideally meant to just be for home use. Play games cruise the Net and be stable...

rhyn (the only user)

I rebooted after viewing chmod --help
and then logged in again. 
The same error appeared so I know its not a BAD DREAM.
So permissions should allow me to do anything and eveything I want to. Although maybe thats why I have this problem that I do now.

---

### Post by jd65pl on 2007-06-13
can you post the output from

```
ls -lR /home
```

---

### Post by Rhyn W on 2007-06-13
Total 4
rwxrwxrwx 23 rhyn rhyn rhyn 4096 Jun 13 11:48 rhyn

---

### Post by jd65pl on 2007-06-13
do
```
chmod 755 /home/rhyn
```

---

### Post by Rhyn W on 2007-06-13
Nothing happened

---

### Post by jd65pl on 2007-06-13
do
```
chmod 644 /home/rhyn/dmrc
```

then check if the error occurs

---

### Post by Rhyn W on 2007-06-13
Chmod: missing operand after '644./home/rhyn.dmrc'
try 'chmod --help' for more info

---

### Post by jd65pl on 2007-06-13
Did you copy and paste the command I posted, I think you may have mistyped it.

---

### Post by Rhyn W on 2007-06-13
I'm using another machine to post to you. so I'm typing what I see here in there. no way to C&P.
I'll retype and see what hapens

---

### Post by Rhyn W on 2007-06-13
Chmod: cannott access '/home.rhyn/dmrc'/: No such file or directory

---

### Post by jd65pl on 2007-06-13
It should read
/home/rhyn/dmrc

NOT

/home.rhyn/dmrc'/

---

### Post by Rhyn W on 2007-06-13
Hi Thats was typo on my part here in the forum.
It did read the way you say it should on my machine. appologies.

Um I've had to give this a rest now, Is there anything you can recommend me to do next. 
I'll give it a bash later on. And post back to you tomorrow.

I really appreciate the help.

Kind Regards

Rhyn W

---

### Post by jd65pl on 2007-06-13
Check [this thread]("http://ubuntuforums.org/showthread.php?t=91455&page=3"),

---

### Post by Rhyn W on 2007-06-13
Thank You, Jd 
Will check it out. later

Kind Regards

Rhyn

---

