---
title: "How to bind a file to a command?"
date: 2007-06-17
forum: General Help
---

### Post by wconstantine on 2007-06-17
It's quite hard to explain in the title but this is what I mean:

I want /usr/local/apache2/bin/apachectl to be binded so I just need to write apache in the console.

This should be doable right?

---

### Post by drummer on 2007-06-17
Sure is.. open up the .bashrc file in a text editor (it's in your home directory, create it if it isn't and notice the dot there), then add this line:
alias apache='/usr/local/apache2/bin/apachectl'

---

### Post by wconstantine on 2007-06-17
Ah. That's whats that file is for! :P

Thank you very much.

---

### Post by Ocxic on 2007-06-17
you can also create scripts to simplify longer tasks

simply crreat a text file with .sh as the extenstion, type in your commands, a new line for each command, then just save it and make it executable.

then simply run, the script with "./mysript.sh" from a terminal, and it will go through executing each line in the order you've put them in.

---

### Post by wconstantine on 2007-06-17
> **Ocxic said:**
> you can also create scripts to simplify longer tasks

simply crreat a text file with .sh as the extenstion, type in your commands, a new line for each command, then just save it and make it executable.

then simply run, the script with "./mysript.sh" from a terminal, and it will go through executing each line in the order you've put them in.

Knew bout' that one but I figured I didn't want to use ./ every time. ;)

---

### Post by drummer on 2007-06-17
or you could even combine the two; create a script to do lots of stuff at once, put it in a folder (say /home/name/bin) and add that folder to your PATH environment variable by adding this to .bashrc: ```
export PATH=$PATH:/home/name/bin
```
Then you can run your own scripts without having to add the ./ ;)

---

### Post by Ocxic on 2007-06-17
no worries, just thought I'd mention it.

---

### Post by wconstantine on 2007-06-18
I got a problem with these methods. It doesn't accept sudo in the start. It says "sudo: apache: command not found". But if I write apache it do work just that I need root permissions to start the server.

---

### Post by AZzKikR on 2007-06-18
What you can do instead, is making a symbolic link in your ~/bin/ directory.

Let me explain this a little further. When you open a Bash Shell, the files .bashrc, .bash_login and .bash_profile are executed. If you inspect the .bashrc, you'll see some block to "append the bin dir to the PATH, if the user has one in its home directory".

So, make a bin dir in your home directory by:
```
mkdir ~/bin/
```

Then, make a symbolic link to /usr/local/apache2/bin/apachectl by executing something like:
```
ln -s /usr/local/apache2/bin/apachectl ~/bin/apache
```

If you look in the ~/bin/ dir, you will see a symbolic link. Next time you start a bash session, when you type 'apache' what actually is executed is the executable to where the symbolic link points. You can use sudo like this.

Hope this explains a bit.

---

### Post by wconstantine on 2007-06-18
> **AZzKikR said:**
> What you can do instead, is making a symbolic link in your ~/bin/ directory.

Let me explain this a little further. When you open a Bash Shell, the files .bashrc, .bash_login and .bash_profile are executed. If you inspect the .bashrc, you'll see some block to "append the bin dir to the PATH, if the user has one in its home directory".

So, make a bin dir in your home directory by:
```
mkdir ~/bin/
```

Then, make a symbolic link to /usr/local/apache2/bin/apachectl by executing something like:
```
ln -s /usr/local/apache2/bin/apachectl ~/bin/apache
```

If you look in the ~/bin/ dir, you will see a symbolic link. Next time you start a bash session, when you type 'apache' what actually is executed is the executable to where the symbolic link points. You can use sudo like this.

Hope this explains a bit.

Yeah, that did the trick. Thanks.

---

### Post by RedSquirrel on 2007-06-18
If you need sudo to run the command, you can just make that part of the alias:

```
alias program='sudo /path_to_program/really_nice_program'
```

---

