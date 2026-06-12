---
title: "[SOLVED] aptitude... VERY STRANGE?"
date: 2007-10-03
forum: General Help
---

### Post by holihue on 2007-10-03
I want to have "aptitude" to run "aptitude -v" as default.

So I:
```
sudo cp /usr/bin/aptitude /usr/bin/aptitude2
sudo cp /usr/bin/aptitude /usr/bin/aptituder
sudo rm /usr/bin/aptitude
sudo gedit /usr/bin/aptitude
```

And in the /usr/bin/aptitude I added:
```
#!/bin/sh
/usr/bin/aptituder -v
```

And when I tested it:
```
sudo aptitude install totem-mozilla
```
I got something like Synaptics in terminal...
I haven't checked this, I just added this thread.

Please try this.:)
I have a screenshot...


It was very surprising...

:)

---

### Post by holihue on 2007-10-03
how can I use this script with the command...

I mean that when I run this program it runs only aptitude -v.

I want it to run aptitude -v [and the command, like "install package-file"]

I tried /usr/bin/aptituder -v %s, but I got unknown command...

---

### Post by Namtabmai on 2007-10-03
You need to pass in the arguments for you're script into aptitude.

e.g.

```

#!/bin/sh
/usr/bin/aptituder -v $*

```

---

### Post by Lord Illidan on 2007-10-03
You shouldn't have done that.

What you should have done is make a bash alias like the ones here : [http://www.hypexr.org/bash_tutorial.php#alias](http://www.hypexr.org/bash_tutorial.php#alias)

```
alias aptitude='/usr/bin/aptitude -v'
```

would have done the trick. Just put that code in your ~/.bashrc

Now, try and clean up the mess you did before by restoring the files back to their default positions.

---

### Post by maniacmusician on 2007-10-03
set up a bash alias?

edit ~/.bashrc, and add a line like:
```
alias aptitude="aptitude -v"
```
or better,
```
alias install="sudo aptitude -v install"
```
so you can just do "install *name_of_package*". I personally use apt-get instead of aptitude, but to each their own.

---

### Post by holihue on 2007-10-03
I tried to edit the .bashrc, but nothing changed.

I also tried:
```
alias ubuntu="gedit"
```

but nothing happend.
then I restarted the terminal.
And it worked...


Thanks a lot, guys

---

### Post by strabes on 2007-10-03
In order to apply the settings you can run :```
source ~/.bashrc
```

---

### Post by koenn on 2007-10-03
> **Lord Illidan said:**
> You shouldn't have done that.

but nonetheless, he managed to get his OS to do what he wanted it to do. Not too bad.

---

### Post by Lord Illidan on 2007-10-03
> **koenn said:**
> but nonetheless, he managed to get his OS to do what he wanted it to do. Not too bad.

Sure, but it's not the recommended way to do things, and could also mess up the system.

---

### Post by holihue on 2007-10-04
> **Lord Illidan said:**
> Sure, but it's not the recommended way to do things, and could also mess up the system.

I knew what I was doing.
And I took a backup of the file...
And if I'm messing up my system I just format it, and then I learn a new bad idea.:):):)

---

### Post by Lord Illidan on 2007-10-04
> **holihue said:**
> I knew what I was doing.
And I took a backup of the file...
And if I'm messing up my system I just format it, and then I learn a new bad idea.:):):)

Sure :P
What I should have said was : That was not the way I would have done it..hehe

---

### Post by koenn on 2007-10-04
> **Lord Illidan said:**
> Sure :P
What I should have said was : That was not the way I would have done it..hehe
and if you hadn't mentioned aliases, I'd have.

---

