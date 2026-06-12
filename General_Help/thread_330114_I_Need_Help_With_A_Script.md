---
title: "I Need Help With A Script"
date: 2007-01-02
forum: General Help
---

### Post by OffHand on 2007-01-02
Hi 

I'm looking for someone who can make a script that executes the following command if powernowd is on  'sudo /etc/init.d/powernowd stop' and  'sudo /etc/init.d/powernowd start' if powernowd is off.

Can anyone help me with this please?

Thanks in advance...

---

### Post by evilghost on 2007-01-02
I could write it in perl but I'm really confused by what you're asking, so let me summarize:

If powernowd is on, turn it off.
If powernowd is off, turn it on.

Isn't this an infinite loop?

---

### Post by OffHand on 2007-01-02
> **evilghost said:**
> I could write it in perl but I'm really confused by what you're asking, so let me summarize:

If powernowd is on, turn it off.
If powernowd is off, turn it on.

Isn't this an infinite loop?

It should act like a toggle button. So if powernowd is off and I click it, it will start powernowd again. And if I click it when it is running the script has to put it off.

---

### Post by evilghost on 2007-01-02
I'm with you now, run as sudo:

```

#!/usr/bin/perl -w

my $pid = `pidof powernowd`;
if ($pid > 0){
        print "Powernowd is started with PID $pid, stopping...\n";
        system("/etc/init.d/powernowd stop");
}else{
        print "Powernowd is not started, starting...\n";
        system("/etc/init.d/powernowd start");
}

```

---

### Post by OffHand on 2007-01-02
sudo sh togglepowernowd 
togglepowernowd: 3: my: not found
togglepowernowd: 4: Syntax error: "{" unexpected (expecting "then")

---

### Post by evilghost on 2007-01-02
> **OffHand said:**
> sudo sh togglepowernowd 
togglepowernowd: 3: my: not found
togglepowernowd: 4: Syntax error: "{" unexpected (expecting "then")

You asked for a perl script solution, not a bash script.  Try running it with perl. ;P

---

### Post by OffHand on 2007-01-02
sudo perl togglepowernowd 
Argument "" isn't numeric in numeric gt (>) at togglepowernowd line 4.
Powernowd is not started, starting...
 * Starting powernowd...                                                 [ ok ] 
xxxxx@xxxxx:~$ sudo perl togglepowernowd 
Argument "" isn't numeric in numeric gt (>) at togglepowernowd line 4.
Powernowd is not started, starting...
 * Starting powernowd...                                                 [ ok ]

---

### Post by evilghost on 2007-01-02
Replace:

```

my $pid = `pidof powernowd`;

```

With:

```

my $pid = `pidof powernowd`;
chop($pid);

```

---

### Post by OffHand on 2007-01-03
Sorry for the late reply but I just had to crash.
I have changed the lines you told me to change and I now get the following warming:

sudo perl togglepowernowd 
Argument "" isn't numeric in numeric gt (>) at togglepowernowd line 5.
Powernowd is not started, starting...
 * Starting powernowd..

---

### Post by OffHand on 2007-01-03
I have tried to make my own script which looks like:
```

#!/bin/sh

pidof powernowd
a=$?

if test "$a" = "0"; 
then
echo "Powernowd is running... stopping Powernowd"
	exec sudo /etc/init.d/powernowd stop
else
echo "Powernowd is not running... starting Powernowd"
	exec sudo /etc/init.d/powernowd start
fi


```

Which results in:

$sh togglepowernowd
Powernowd stopped... starting Powernowd
Password:
 * Starting powernowd...                                                 [ ok ] 
$ sh togglepowernowd
Powernowd stopped... starting Powernowd
 * Starting powernowd...               

Now I think the problem has to do with the fact that powernowd starts eventhough it's running already. Am I on the right track?

---

