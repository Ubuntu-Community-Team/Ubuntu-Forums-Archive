---
title: "How do I use history of commands?"
date: 2007-04-14
forum: General Help
---

### Post by ShirishAg75 on 2007-04-14
Hi all,
     How do I use the command history? The simple way is to use the up arrow key. But what if I remember the starting part of the command but not the full command? Is there a way to search or have a list of all the commands starting with that?

       For e.g. ' cat /proc/version_signature' is a command. Later on I just remember cat & not the full command. Is there anyway to do some kind of magic so that I can use cat along with something so it gives a list of all the commands I used having cat as the starting word. I know it would use grep in someway but do not know what else is needed to be done? Thanx in advance.

---

### Post by Compyx on 2007-04-14
```
history | grep '<the part you remember>'
```

Leaving out grep will provide you with the complete history, of course.

---

### Post by ShirishAg75 on 2007-04-14
Just found this page [http://www.sharms.org/blog/?p=83](http://www.sharms.org/blog/?p=83), this fish thing at the bottom looks cool :p

---

### Post by KIAaze on 2007-04-14
Here are some more tips&tricks:
[The command-line history]("http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x1712.htm")

The only one I knew in all this list until now was CTRL+R. :)

Those are all default functions, so they don't require any text file editing.

---

### Post by tommcd on 2007-04-14
How about the old fashioned way.
I have a folder in my /home folder called ubuntu_stuff. I also have folders for debian and zenwalk.
Whenever I come across something interesting or useful for each distro, I copy and paste it to a new file in the distro's folder, along with the url of where I got it. I now got quite a library of stuff that I can refer back to if I need to remember how to do something.

---

### Post by ShirishAg75 on 2007-04-14
I am happy with fish :)

---

