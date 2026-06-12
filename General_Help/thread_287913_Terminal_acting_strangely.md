---
title: "Terminal acting strangely"
date: 2006-10-29
forum: General Help
---

### Post by BucketOfZen on 2006-10-29
I upgraded to Edgy on Friday, and most of it I like, but yesterday I unwittingly did something to make the terminal act very strangely. (I haven't a clue what I did though)

I was used to getting "nat@ubuntu:" but now I only see "#". Another thing is usually, when I want to re-do a command, I press up to see the last command I did, but when I do this I get "^[[A" instead.

Is this something to do with .bashrc?

---

### Post by jhofmann on 2006-10-29
Yes, it is related to .bashrc.  The '#' prompt almost always means you are now logged in as root.  Try typing exit to see get back to a regular user.  You may edit .bashrc and .bash_profile as both user root and as yourself.  They are different and are in their respective home directories.  I think the .bashrc file is preconfigured for the prompt you mentioned and history is enabled, but I don't know about root.

Try typing exit, and see if things aren't fixed.

---

### Post by BucketOfZen on 2006-10-29
I did exit, nothing happened, did it again and the terminal closed. I tried again, su'd into my normal user account, which just replaces # with $.

I've replaced my .bashrc file with [this one]("http://uzix.org/bashrc.html"), but no change.

---

### Post by jeblinux on 2006-11-02
The terminal you are using is not BASH. It is simply sh from BSD. That is why you get the arrow keys creating weird characters and no history. this is a historic interpreter from the old AT&T days.

Type 'bash' to switch to the bash command line interpreter. Look at the file '/etc/shells' to see all the different available shells on your system. You will be surprised (probably) how many different ones there are. Just type

$ cat /etc/shells

and they will all be listed.

You can change you default shell by using the 'chsh' command. If you don't change your default shell then you will keep coming back to 'sh' every time you login and you will have to type 'bash' to get the bash interpreter again. Just type

$ chsh

and it will ask for your password (probably) and then ask you for the complete path to the shell of your choice. A default is shown in square brackets. If you just press Enter this will become your new default shell. So if you see

Password: 
Changing the login shell for jeblinux
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]: 

The just press enter to get BASH.

---

### Post by BucketOfZen on 2006-11-03
Yeah, I worked that out. I messed it up on my first attempt, as I messed around with the symlinks in /bin. Bad idea...

I fixed that, then re-installed bash and it worked fine.

Thanks anyway though, I'll do that if it happens again.

---

