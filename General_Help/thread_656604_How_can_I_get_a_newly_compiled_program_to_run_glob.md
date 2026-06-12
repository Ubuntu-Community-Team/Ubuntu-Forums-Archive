---
title: "How can I get a newly compiled program to run globally"
date: 2008-01-02
forum: General Help
---

### Post by jeeves on 2008-01-02
I have just [successfully compiled a couple of multimedia utilities. ]("http://ubuntuforums.org/showpost.php?p=4060634&postcount=2")I can run them by cd'ing into the directories I compiled them in and running something like:```
./ProgramName
```

It would be handy to be able to call these program in shell without having to specify where they reside and using "./" to tell them to run.  Does anyone know how to set this up?

---

### Post by p_quarles on 2008-01-02
Did you try running this?:
```
sudo make install
```
(inside the build directory, of course)

---

### Post by CrucifiedEgo on 2008-01-02
If for some reason the make install fails (though any app worth it's salt should have an install), the correct place for compiled programs and scripts (anything not installed by apt) is /usr/local/bin :)  I've seen some systems where that's not in the default path, so check it by doing ```
echo $PATH
``` at a terminal, and look for /usr/local/bin

---

### Post by jeeves on 2008-01-02
Thanks. I tried running **sudo make install** but got the following message:

**make: Nothing to be done for `install'.**

Then I tried checking the path by running echo $PATH and got back:
[B]
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games[/B]

so "/usr/local/bin" is in that list, but I am not sure what to do with that information.

---

### Post by p_quarles on 2008-01-02
CrucifiedEgo was suggesting that you place a copy of the executable file in /usr/local/bin, and see if that works. It may not, depending on whether the executable looks for any configuration files in its own directory. 

Personally, my solution would be to make an alias:
```
gedit .bashrc
```and add a line such as this:
```
alias programname='/path/to/file/programname'
```

---

