---
title: "Help combining commands"
date: 2012-12-17
forum: General Help
---

### Post by cbillson on 2012-12-17
Hi, believe and hoping this is possible, but unsure fully how it works. i know you can redirect output, and also take the output of one and use it in another command, need some help constructing this:

i want to use the logger command to send the output of "myprogram --version"

the output should be "myprogram vx.x.x"

Not sure if i should be doing:

myprogram --version > logger ........

or 

logger ...... | myprogram --version

any help apreciated.

Cheers
Chris

---

### Post by steeldriver on 2012-12-17
I think logger accepts standard input from a pipe

```
$ echo "Testing logger redirection" | logger
$
$ tail -1 /var/log/syslog
Dec 17 07:34:36 lap-t61p logger: Testing logger redirection
```or you could just use the output of your command as a message string via $(...)

```
$ logger "$(echo "another way to do it")"
$
$ tail -1 /var/log/syslog
Dec 17 07:37:45 lap-t61p steeldriver: another way to do it

```

---

### Post by cbillson on 2012-12-17
> **steeldriver said:**
> I think logger accepts standard input from a pipe

```
$ echo "Testing logger redirection" | logger
$
$ tail -1 /var/log/syslog
Dec 17 07:34:36 lap-t61p logger: Testing logger redirection
```or you could just use the output of your command as a message string via $(...)

```
$ logger "$(echo "another way to do it")"
$
$ tail -1 /var/log/syslog
Dec 17 07:37:45 lap-t61p steeldriver: another way to do it

```

Fantastic, thanks very much, these give me some options going forward..

one last question if i may.. lets say the output of "myprogram --version" is just 1.1 - is there any way i can prefix or suffix this with something in either of the two examples you gave so it sends "myprogram 1.1"

Cheers
Chris

---

### Post by cbillson on 2012-12-17
sorted.. 

program=$(myprogram --version)

logger "myprogram $program"

---

### Post by steeldriver on 2012-12-17
sure - try

```
$ logger "Version of myprog is: $(myprog --version)"
```

---

### Post by fdrake on 2012-12-17
if you want to apply that to diffente programs then:
define $myprog=....
```
$ logger "Version of $myprog is: $($myprog --version)"
```

---

