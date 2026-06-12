---
title: "How to create a desktop launcher out of a *.sh"
date: 2007-03-30
forum: General Help
---

### Post by alek66 on 2007-03-30
I want to make a desktop launcher of mercury msn, and the file that I execute from console is a .sh file...

---

### Post by ardchoille42 on 2007-03-30
> **alek66 said:**
> I want to make a desktop launcher of mercury msn, and the file that I execute from console is a .sh file...

The command portion would be
```

sh filename.sh

```

I make launchers for .sh scripts and that works great.

---

### Post by alek66 on 2007-03-30
Nothing, I created a launcher using sh /pathoftheprogram/startup.sh
and nothing
I tried the optiones, create an aplication and also tried writing sh '/pathoftheprogram/startup.sh'
help
i am using gnome

---

### Post by ardchoille42 on 2007-03-30
> **alek66 said:**
> Nothing, I created a launcher using sh /pathoftheprogram/startup.sh
and nothing
I tried the optiones, create an aplication and also tried writing sh '/pathoftheprogram/startup.sh'
help
i am using gnome

Is the .sh file executable?

---

### Post by alek66 on 2007-03-30
yes I can execute it from console... using sh jaja.sh

---

### Post by fdrake on 2007-03-30
create a costumed luncher icon on the panel or desktop with rightclick. and write the command you use.

---

### Post by noynac on 2007-03-30
I don't know what mercury msn is, but I make shell scripts executable with the following command:

sudo chmod 755 script-name

I then either put the shell script in the path or include the path to the script file in the launcher command line.

Are you talking about something else?

---

### Post by fdrake on 2007-03-30
what you actually should do is to create a link to your msn luncher.
first you need to find out where is the luncher of the command: 
type <msn command>  copy the path
link <msn path> ~/Desktop/msn

---

