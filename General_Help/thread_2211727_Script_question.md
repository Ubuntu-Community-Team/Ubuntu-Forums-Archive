---
title: "Script question"
date: 2014-03-17
forum: General Help
---

### Post by Korkel on 2014-03-17
Hello,

I want to make a script to resolve my Skype problem, it won't start by default.

I got only one question, how can I make a new file with some text in a specfic map? It must be in this map:
```
*/usr/bin/skype
```*Thanks!

---

### Post by Impavidus on 2014-03-17
You'll probably need root permission to create a file there. Use```
gksu gedit /path/to/directory/filename
```enter your password, write the file, save the file and close the editor. Or use any other editor you like.

---

### Post by Korkel on 2014-03-17
> **Impavidus said:**
> You'll probably need root permission to create a file there. Use```
gksu gedit /path/to/directory/filename
```enter your password, write the file, save the file and close the editor. Or use any other editor you like.
Can I then add also some text in it automatic?

---

### Post by Impavidus on 2014-03-17
If you don't want to type in the text file, there are some possibilities. For example```
echo "Text you want in your file" | sudo tee /path/to/file
```Or if it comes from a file you aready have, copy it there```
sudo cp /path/to/source /path/to/destination
```

By the way, on my system there are no directories in /usr/bin. There are only executables and symlinks to executables, which the the idea behind /usr/bin. Sure about the directory where you have to be?

---

### Post by Korkel on 2014-03-17
I got now this, but it isn't working, when I run terminal close directly:
```
sudo mv /usr/bin/skype /usr/bin/skype-bin
echo "#!/bin/sh
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
exec skype-bin "$@"" | sudo tee /usr/bin/skype-bin
sudo chmod 0755 /usr/bin/skype

```

---

### Post by ajgreeny on 2014-03-17
I do not follow what you are trying to do.  Do you already have skype installed on the computer and if so, why do you want to replace the executable already in that site?

For skype to work you need that executable file in /usr/bin so I would leave well alone.  If you are having problems starting skype at boot time you need to look at other possible solutions such as adding a sleep delay to the startup, which you could do with a script.

Tell us more about what you really want to do, and why.

---

### Post by Korkel on 2014-03-17
> **ajgreeny said:**
> I do not follow what you are trying to do.  Do you already have skype installed on the computer and if so, why do you want to replace the executable already in that site?

For skype to work you need that executable file in /usr/bin so I would leave well alone.  If you are having problems starting skype at boot time you need to look at other possible solutions such as adding a sleep delay to the startup, which you could do with a script.

Tell us more about what you really want to do, and why.
Sorry... I must run [this]("http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html") before my Skype is working, for that reason I want an automatic script. :)

---

### Post by ajgreeny on 2014-03-17
Did you put the 
**#!/bin/sh**
line at the top of the shell script and make it executable with the
**sudo chmod 0755 /usr/bin/skype**
command after saving it in /usr/bin

---

### Post by Impavidus on 2014-03-17
> **Korkel said:**
> I got now this, but it isn't working, when I run terminal close directly:
```
sudo mv /usr/bin/skype /usr/bin/skype-bin
echo "#!/bin/sh
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
exec skype-bin [COLOR=#ff0000]**"$@"**[/COLOR]" | sudo tee /usr/bin/[COLOR=#ff0000]**skype-bin**[/COLOR]
sudo chmod 0755 /usr/bin/skype

```
This won't work anyway. The "$@" has te be escaped to be passed into the output. Furthermore, you wrote the script to skype-bin instead of skype, overwriting the binary and not creating the /usr/bin/skype file.

---

### Post by Korkel on 2014-03-17
Ehm... :S

Any ideas?

---

