---
title: "Show output of a running process"
date: 2008-06-22
forum: General Help
---

### Post by lennartack on 2008-06-22
Hi,

Is there a command to display the output of a process in the current terminal? Per example if you have started a program using alt+f2 rather than in a terminal. That would be fun :P

Thanks,
Lennart

---

### Post by rraj.be on 2008-06-22
I dont know how much this one helps you. But have a try.


You can use this command to make your process display every System calls It executes

```
strace <application name>
```


Example 
```
strace firefox
```

[linux.die.net/man/1/strace]("linux.die.net/man/1/strace")

---

### Post by fahadsadah on 2008-06-22
I think there is something in the proc filesystem...

EDIT: Woops, beaten to it. The above does not display the STDOUT of a running process
EDIT2: Nope, looks impossible

---

### Post by Zorael on 2008-06-22
What if you started the application with '**app >> output.`date +"%y-%m-%d"`**'? Then use that terminal tool I don't remember the name of to monitor the changes to it. Remove the date part if you want to keep it to one file.

---

### Post by lennartack on 2008-06-23
> **fahadsadah said:**
> 
EDIT2: Nope, looks impossible
Ok, I can live with that :). However, I don't understand why this isn't possible. Such a tool would be very useful... Ofcourse you can set up something like Zorael said, but you have to change startup scripts for all programs you might want to monitor one day, and I'm not going to do that :P.

---

