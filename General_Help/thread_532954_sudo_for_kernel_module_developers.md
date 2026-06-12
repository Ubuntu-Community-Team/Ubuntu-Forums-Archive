---
title: "sudo for kernel module developers"
date: 2007-08-23
forum: General Help
---

### Post by ensis2k on 2007-08-23
Hello,

my problem is as follows:

2 Users:
usr1, usr2

usr1 has all the passwords
usr2 is not allowed to have them

usr2 needs special /etc/sudoers/ entries that allow him to:
- (un)load kernel modules
- make and execute a program as root

As a test, so he can run his compiled program, I tried to add the following line at the bottom of 'sudoers':
usr2 ALL=NOPASSWD:/home/usr2/app

but it didn't work. What is wrong?

---

### Post by ddrichardson on 2007-08-24
Sudoers works with groups (specify %) or users, the colon is not needed: for example to add, say apt-get then add a line to /etc/sudoers:```
%installers ALL=(root) /usr/bin/aptitude, /usr/bin/apt-get
```

Then add the user to the installers group.

In this case you will need to ad insmod and make. It is risky to allow this though because it gives him the ability to do a make install, potentially messing up everything. make doesn't require sudo so the best thing is to just add the module programs and get him to run his compiled programs as sudo.

---

### Post by ensis2k on 2007-09-03
Works fine. But the problem is that i need more then just insmod. 

There is also an application which has to run with su-privileges. Every user has his own version in his repository.
So right now whenever i add a new user i also have to add the line:

%installers ALL=(root) /home/axel/repos/start.sh, /home/axel/repos/kernapp
%installers ALL=(root) /home/tom/repos/start.sh, /home/tom/repos/kernapp
%installers ALL=(root) /home/tom/jane/start.sh, /home/jane/repos/kernapp

Okay, i can copy the start script into another directory and remove it from the repository since it changes seldom but what about 'kernap'. It has to run with super user privileges and is different for every repository.


Thank you very much.

---

### Post by ddrichardson on 2007-09-03
There is the setuid bit but this is highly discouraged as a possible security risk.

I have to ask why these are so different, are they entirely different projects or are they a distributed project - if so using subversion/git/cvs of even rcs would be the way forward.

If not then, I don't know if this works but its worth a try, can you specify a relative path rather than an absolute? i.e.```
 %installers ALL=(root) ~/repos/start.sh, ~/repos/kernapp
```If sudoers doesn't accept the relative pathname then it should accept the $HOME variable set in .bashrc in the users directory, hence:```
 %installers ALL=(root) '$HOME'/repos/start.sh, '$HOME'/repos/kernapp
```

Like I say though these are purely suggestions, because I'm not sure at what point sudoers is actually read - I assume it's after sudo is called, but maybe at login.

---

