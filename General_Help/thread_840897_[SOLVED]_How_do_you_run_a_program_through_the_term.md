---
title: "[SOLVED] How do you run a program through the terminal"
date: 2008-06-25
forum: General Help
---

### Post by chad2408m on 2008-06-25
This is more specific than the title.  When you click on a program (executable text), and it gives you the options:

run in terminal   display   cancel   run 

I click run, and everything works okay, however, how do you launch executable text through the terminal (the command).  I need to know so I can make a Link to that application, and for the command i need to know how to run it as a program as default or something like that.

Oh, and I am runnung Ubuntu 8.04

---

### Post by cdtech on 2008-06-25
Depends on the program actually. Some it's just a matter of calling it with:
```
./program-name (within the directory of the program itself).
```

If we knew the program that would be an advantage.

---

### Post by chad2408m on 2008-06-25
okay, but im sorta new at this and dont really understand.  its an executable text string that does this:

LD_LIBRARY_PATH=".:${LD_LIBRARY_PATH}" ./phun.bin $@

can someone maybe give an example or something that would tell me the code?

directory: /home/chad/Games/Phun
and the file type is 'plain text'.
How i got it to work before was go to properties, and the permissions, and check the box that said 'allow to run as program'

-------------------------------------

okay, I got it to work doing what you told me, but it took 2 lines of code (one to change directories, the other to launch the program).  Is there anyway (when using the 'make launcher' thing that you can type in the command box to tell it to launch one piece of code on one line, let it do its job, and then launch another string of code as if it were on a second line?

---

### Post by drs305 on 2008-06-25
> **chad2408m said:**
> 

okay, I got it to work doing what you told me, but it took 2 lines of code (one to change directories, the other to launch the program).  Is there anyway (when using the 'make launcher' thing that you can type in the command box to tell it to launch one piece of code on one line, let it do its job, and then launch another string of code as if it were on a second line?

You can join the commands by putting a **&&** between them.

For example, with will run both:
```
cd /home && gimp &
```
The '&' symbol at the end allows the window to stay open and run other commands while the previous command remains active.

Another example:
```
cd /home && ls
```

---

### Post by chad2408m on 2008-06-25
thanks, i think it might work, but one problem:

Details: 
Failed to execute child process 
"cd" (No such file or directory)

it claims theres no directory even though i checked it twice and even copied/pasted the folder, and it put in the path!  any more suggestions?

------------------------------
To be more desriptive, heres what i put in the 'command' line of the launcher:
cd /home/chad/Games/Phun && ./phun &

---

### Post by cdtech on 2008-06-25
> For example, with will run both:
Code:

cd /home && gimp &

That could read "~/directory-to-program"

That will change to your "~" home directory.

---

### Post by drs305 on 2008-06-25
Sorry, 'cd' may be alias I made a long time ago when I switched from windows. I don't even remember doing it. ADDED: Nope the alias I added was cdd to change to Desktop. cd should work.

Here's another example:
```
ls /home && nautilus &
```

---

### Post by chad2408m on 2008-06-25
I still keeps complaining about there not being a file or directory, and I know for a fact its there.  Im not a pro, so im probably doing something wrong.  Heres absolutely everything I can tell you about this:

---------------------------------------------------------------------------
Directory: /home/chad/Games/Phun
File: phun, which is an executable text which has this command on it:
               LD_LIBRARY_PATH=".:${LD_LIBRARY_PATH}" ./phun.bin $@
It calls phun.bin, which is in the same directory.
---------------------------------------------------------------------------

and heres what I put for my 'launcher'.
1) cd /home/chad/Games/Phun && ./phun &
2) cd ~/Games/Phun && ./phun &
(I made 2)

and heres the error I get:

There was an error launching the application.

Details: 
Failed to execute child process 
"cd" (No such file or directory)

---

### Post by chad2408m on 2008-06-25
A New Breakthrough!

when I used the ls command instead of cd, no error.  However, no program was launched either.

---

### Post by chad2408m on 2008-06-25
Problem solved, I just edited the file itself and put cd (directory) && before everything else.  it works great.

---

