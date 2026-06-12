---
title: "bash and pid"
date: 2006-07-12
forum: General Help
---

### Post by marwal on 2006-07-12
From within i shellscript (bash) i try to start some processes and then store the PIDs of these to later on kill them.
But it doesn't work.

Take a look at this:

From within gnome-terminal:

gnome-terminal &
>[1] 6337

echo $!
> 6337

pidof gnome-terminal
> 6254

I don't want to 'killall gnome-terminal' or 'ps x | grep gnome-terminal (and some sed and/or awk to fetch the pid).

So how do i trace a childs child thru process IDs?

---

### Post by Maggot on 2006-07-12
try

[list]
[*]SYSTEM
[*]ADMINISTRATION
[*]SYSTEM MONITOR
[/list]

you may then have to go
[list]
[*]VIEW
[*]DEPENDENCIES
[/list]

---

### Post by marwal on 2006-07-12
> **Maggot said:**
> try

[list]
[*]SYSTEM
[*]ADMINISTRATION
[*]SYSTEM MONITOR
[/list]

you may then have to go
[list]
[*]VIEW
[*]DEPENDENCIES
[/list]

No, no... thats not it!
It should work from within a script.

Example :

#!/bin/bash
mozilla-firefox &
killit=$!
wait
kill $killit

This should not return "no such process ID". This is what im after.

---

### Post by Maggot on 2006-07-12
> **marwal said:**
> No, no... thats not it!
It should work from within a script.


Ah. Gotcya.

---

### Post by Maggot on 2006-07-12
#!/bin/bash
xmmspid=`pidof xmms`
kill $xmmspid

?

---

### Post by marwal on 2006-07-12
> **Maggot said:**
> #!/bin/bash
xmmspid=`pidof xmms`
kill $xmmspid

?

Yeah, that would kill some xmms process running.

But what I want is to
1) start the process
2) get the pid
3) kill THAT pid


#!/bin/bash

# here i'm starting one instance of gvim
gvim &
# here i get the pid
g1=$!
wait

# now im starting another instance of gvim
gvim &
# and here i get the pid
g2=$!
wait

#now i want to kill the first instance of gvim
kill $g1

This doesn't work 'cause my pids are useless.
$g1 and $g2 gives pids 7585 and 7589
a "ps x | grep gvim" tells me that both gvim instances run on 7588 and 7592.

OK, I could add 3 to every PID, before I kill'em, but I wouldn't like that solution.

So... HOW, do i get the pid of the process im starting from bash?

---

### Post by Maggot on 2006-07-12
running gcalctool & 

then running this script will close gcalctool for me.

#!/bin/bash
gcalctoolpid=`pidof gcalctool`
kill -9 $gcalctoolpid


No idea if that is what you are really looking for.

Oh...xmms was just an example program..obviously you can substitute anything you want.

edit: running 2 instances of gcalctool and running the script obviously kills both instances...which I think is the problem you have :mrgreen:

---

