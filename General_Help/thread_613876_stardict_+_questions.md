---
title: "stardict + questions"
date: 2007-11-15
forum: General Help
---

### Post by eneth80 on 2007-11-15
Hallo.
1)I have stardict installed and it is so great that i'd like to have another separate one in another language. I copied stardict's directory:
sudo cp -r  /usr/share/stardict  /usr/share/stardict2
and made a link
ln -s /usr/bin/stardict /usr/bin/stardict2 
now in /usr/bin stardict is green, stardict2 is light blue, and of course i cannot launch stardict2 from terminal. What did i do wrong?

2) how can i notice when people answer to this post? just make a search with my name?

3) I find very difficult to find the answer to my question in this forum. one guy proposed a method to create your own command. I d like to call "history | grep " with a simple "h". but i cannot find the thread.

After 2 years of ubuntu i still have these noob problems :(
thanks,
ale

---

### Post by nick_h on 2007-11-16
1. Don't do it this way.  You can install multiple dictionaries with stardict and if necessary put different languages in different dictionary groups.  You may need startdict 3.0.0 for groups (default for Gutsy).

2. In the User Control Panel under Edit Options set your Default Thread Subscription Mode.  You will then see when your thread is replied to in the User CP.

3. I don't quite understand what you mean.  Are you talking about bash functions and/or aliases?

---

### Post by eneth80 on 2007-11-17
Thanks for your answer! 
1) I cannot install stardict_3.0.1-1_i386.deb , i get : 
Error, dependency is not satisfiable libart-2.0-2
That library is already installed on my computer

2) SOLVED thanks, I did not know that

3)SOLVED  I have looked up what aliasses are and that was what i needed! For the sake of completeness:
sudo gedit /usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile
I added a few lines like: alias h='hystory | grep '     alias ls='ls -aF --color=always'       alias ..='cd ..'    , then
source /usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile

thanks a lot,
ale

---

### Post by nick_h on 2007-11-17
1. I have only used the one from the repositories myself.

3. Try adding an alias to your .bashrc file.
```
h='history | grep'
```

---

### Post by nick_h on 2007-11-17
I didn't read your last update before I posted.  I'm gald you solved number 3 on the list. :)
I have just compared libart between Feisty and Gutsy.  Feisty is version 2.3.17 but Gutsy is 2.3.19 - maybe startdict 3 needs 2.3.19 but it can't upgrade because the earlier version is installed.

---

### Post by eneth80 on 2007-11-18
Hi again
1)mmm, any other ideas?
2)SOLVED
3)SOLVED well, this morning I realized it was not solved: I put an alias in the file I mentioned above, which is just an example file, and loaded it with "source". Now I have copied it:
sudo cp /usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile ~/bash_profile
I also added an     source ~/.bashrc      to ~/bash_profile , It works!

thanks,
ale

---

