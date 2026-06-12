---
title: "[SOLVED] Problems with updates and installs."
date: 2008-06-25
forum: General Help
---

### Post by Lexam on 2008-06-25
Hi everyone. So I am downloading and installing some fun new software. Like Tux Guitar etc. Nothing extreme all in Add-remove. And then I get this message. 

[B]Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing perl-modules (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.[/B]

Now Add-remove, sudo apt-get, synaptics or my update manage won't work. I know they are all tied together and once I get this working the will all work. But I am stumped on this one. I searched the forums but it seems to be unique at this point. Hopefully it is because I don't want anyone else dealing with this.  Any help would be awesome!

Thanks 
Lexam


The Way to fix this if you receive this error and it does not give you the specific line. 

1. type sudo gedit /var/lib/dpkg/status
2. In a new terminal type dpkg -i
3. This will give the line and the syntax error. track it down using the go to line tool. May take a little hunting but this should fix the problem.

---

### Post by earthmeLon on 2008-06-25
[http://egypt.ubuntuforums.com/showthread.php?t=332671](http://egypt.ubuntuforums.com/showthread.php?t=332671)


Try that yet?

---

### Post by Lexam on 2008-06-25
Ah thanks for finding this. Unfortunately mine does not give me the specific lines. Is there a way to debug the status file?

---

