---
title: "Adding options to &quot;make&quot; globally and permanently"
date: 2006-11-08
forum: General Help
---

### Post by Skye on 2006-11-08
In an attempt to fix my wireless lockups, I recently switched to Gentoo to see if it would help.  I didn't like Gentoo's habit of taking literally days to set up a usable system, but I did like the way you can specialize compiler options.  After I came back to Edgy, I wanted to keep those optimizations I used in Gentoo, mainly because I like to stay on the bleeding edge, and hence I tend to do a lot of compiling.

Specifically, I want to find an easier way to maintain the CFLAGS, CXXFLAGS, and MAKEOPTS options I used in Gentoo.  I know you can pass make options to make directly by running **make <options>**, but I'm lazy and I don't want to type that every time.  I also would like to allow the CFLAGS and CXXFLAGS to be applied globally.

I attempted t do it by renaming **make** in /usr/bin, replacing it with a shell script that just called the old makefile with the options I want- but that doesn't work if there are options coming after make (such as *make install*, or *make xconfig*.)

So, has anyone else attempted this, or know how to do this?

---

### Post by bsussman on 2006-11-08
> **Skye said:**
> 

I attempted t do it by renaming **make** in /usr/bin, replacing it with a shell script 

Terrible idea - not standard.

1. You could alias it in your .bash_aliases

2. Since gentoo seems to do it, you might ask them how.

3. You could set up a shell variable in your .bashrc and reference it ( make $MYOPTS ...yadda ... yadda ).

4.  You could write a proper script, keep it in your own directory and make the options part of it.

I can probably think of a few more ways to do it,  if I need to :)

---

### Post by Skye on 2006-11-08
Thanks for the response!

I figured it was a pretty terrible idea, considering it effectively broke the compiler- I've since reversed it.

I'm liking the .bash_aliases idea, mainly because it wouldn't require me to attempt to write a shell script, which I have no confidence in.  After a little googling, I figured out the syntax to the file, and I created a new file called ".bash_aliases" in my home directory with the contents "alias maker= make -j3".  The thing is, it doesn't seem to do anything- running "maker" returns:

spitfire@Apollo:~$ maker
bash: maker: command not found

So, does Ubuntu implement the .bash_aliases file, and if so, how do you get the system to recognize the file?

---

### Post by bsussman on 2006-11-08
> **Skye said:**
> The thing is, it doesn't seem to do anything- running "maker" returns:


So, does Ubuntu implement the .bash_aliases file

Just like every other linux.

.bash_aliases is executed at login.

You can test it by sourcing in the terminal window:

```
bos@Dillon:~$ . ./.bash_aliases
bos@Dillon:~$
```

ending your current x session, starting another one or just restarting is your last test.

Then it is part of your environment whenever you open a terminal.

---

### Post by Skye on 2006-11-08
Got it.  Thanks!

---

### Post by lemix on 2006-11-08
how can i make an external tool for kate
that will pull up console output for a cxx
file using g++?

---

### Post by bsussman on 2006-11-09
> **lemix said:**
> how can i make an external tool for kate
that will pull up console output for a cxx
file using g++?
  The first step might be to open a thread with that question in the title.:-k

---

