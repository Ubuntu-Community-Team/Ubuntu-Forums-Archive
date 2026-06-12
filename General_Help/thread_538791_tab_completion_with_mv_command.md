---
title: "tab completion with mv command"
date: 2007-08-30
forum: General Help
---

### Post by Seti on 2007-08-30
Hey gang, I searched around but couldn't really find the answer to this, there is something that I try to do and it doesn't seem to work, although its never been a problem on other distros.
Lets say I have a file located in my home dir, /home/seti and want to move it to a data storage partiton.

```
mv file /media/backup
```

Like many of you probably are, I'm addicted to [TAB] completion. For some reason, it doesn't seem to work (is it turned off somehow) for the mv command with reference to some directories.

any ideas? 
thanks

---

### Post by Seti on 2007-08-30
to do this I had to edit /etc/bash.bashrc
and uncomment:

#if [ -f /etc/bash_completion ]; then
#   . /etc/bash_completion
#fi


yeha!

---

### Post by fvu on 2007-08-31
If you're addicted to TAB completion, you might also want to try [[FONT="Courier New"]cdots.sh[/FONT]]("http://www.fvue.nl/wiki/Bash_cd_alias:_cdots").  It creates 
seven functions/aliases: 2-8 dots which allow you to move 1-7 directories up
and an optional directory back again - dir - **with TAB-completion**:

```
.. **[dir]** = cd ../**[dir]**
... **[dir]** = cd ../../**[dir]**
.... **[dir]** = cd ../../../**[dir]**
..... **[dir]** = cd ../../../../**[dir]**
...... **[dir]** = cd ../../../../../**[dir]**
....... **[dir]** = cd ../../../../../../**[dir]**
........ **[dir]** = cd ../../../../../../../**[dir]**
```

Example usage:

```
$/usr/local/share> ... sh<TAB><ENTER>
$/usr/share>
```

For download and more information, see: [http://www.fvue.nl/wiki/Bash_cd_alias:_cdots]("http://www.fvue.nl/wiki/Bash_cd_alias:_cdots")

Freddy Vulto
[http://fvue.nl](http://fvue.nl)

---

