---
title: "[SOLVED] Trouble Understanding $PATH"
date: 2008-03-30
forum: General Help
---

### Post by thelugnut on 2008-03-30
I am having trouble understanding the $PATH. Here is an example. I have a test file named "phrases.txt" stored in "bin" in the "Home" folder.

I want to change permissions on this file.

I have to "cd to bin" to be able to do this, even though $PATH shows the first segment to be /home/james/bin.
------------------------------------------------------------------------------------------

```
james@james-desktop:~$ echo $PATH
/home/james/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

james@james-desktop:~$  ls
bin  func_param.py~  log-ins   nautilus-debug-log.txt

james@james-desktop:/$ chmod 777 phrases.txt
chmod: cannot access `phrases.txt': No such file or directory
 
james@james-desktop:~$ cd bin

james@james-desktop:~/bin$ chmod 444 phrases.txt
```

Checking the permissions in "Properties" shows Owner, Group, and Others as Read-only.

```
james@james-desktop:~/bin$ chmod 777 phrases.txt
```

Checking the permissions in "Properties" shows Owner, Group, and Others as Read -Write.
-------------------------------------------------------------------------------------------

So I guess the question is, "Why must I change to the bin directory, when it is obviously listed in $PATH?".

I hope I have made this clear.

---

### Post by danwood76 on 2008-03-30
chmod doesnt look at the $PATH variable.
You can use chmod without using full paths as its easier.

Generally its only when launching apps that bash uses the $PATH variable.

---

### Post by markthecarp on 2008-03-30
As danwood76 points out chmod doesn't check $PATH. 

You could run chmod without cd'ing to ~/bin with...
```

mark@spinach:~$ chmod 777 bin/phrases.txt

```

HTH,
-mark

---

### Post by thelugnut on 2008-03-30
That answered my question. Thank you for the quick replies.

---

