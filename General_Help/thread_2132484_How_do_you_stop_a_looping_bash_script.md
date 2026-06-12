---
title: "How do you stop a looping bash script?"
date: 2013-04-05
forum: General Help
---

### Post by Heeter on 2013-04-05
Hi all,

I was trying a bash script that I found on Github through terminal. At first, it was a funny little bash script, but now I can't stop it. Every time I open my terminal, the bash script starts up. I kill it by pressing "Ctl+C". but it is just a temporary stop. It restarts every time I open a new terminal.

How can I kill this bash script permanently? 

[Here is the Github link for that bash script]("https://github.com/keroserene/rickrollrc") in case someone needs to know which one.

Thanks

Heeter

---

### Post by lvlint67 on 2013-04-05
Has the script planted itself in your ~/.bashrc or ~/.bash_profile?

...edit after reading script....
It definitely looks to have added itself to your .bashrc

---

### Post by Habitual on 2013-04-05
restore your .bashrc from backup.

words like "inject" with variables like "AND_HURT_YOU" should be a BIG **[COLOR="#FF0000"]RED[/COLOR]** FLAG.

---

### Post by Lars Noodén on 2013-04-05
> **lvlint67 said:**
> Has the script planted itself in your ~/.bashrc or ~/.bash_profile?

...edit after reading script....
It definitely looks to have added itself to your .bashrc

If you don't have a backup, you can get a copy of the default .bashrc from /etc/skel

```

cp /etc/skel/.bashrc ~/.bashrc

```

---

### Post by Cheesemill on 2013-04-05
You can also edit the file by hitting ALT+F2 and running the command...
```
gedit ~/.bashrc
```

If you're not sure which line(s) need deleting the just post the contents of the file here a we can take a look.

---

### Post by Heeter on 2013-04-07
Awesome, Thanks guys for  all your guys's help.

I opened up my bash file, and removed the offending line, and now I have my terminal back.

Thanks again all!


Heeter

---

