---
title: "sudo and SIGINT from terminal"
date: 2013-07-17
forum: General Help
---

### Post by hbar1054 on 2013-07-17
On 
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

when running 

> sudo cmd

and trying to exit with Ctrl-C

it used to be that the signal would be forwarded to the sudo process
but right now this does not happen.  Reading some forums it seems
that this behavior may be tied to pam, but I haven't found a solution
and I don't know how to exactly debug this problem.

any help would be greatly appreciated.

thanks.

---

### Post by papibe on 2013-07-17
Hi hbar1054. Welcome to the forums ):P

The fact that Ctrl+C doesn't stop a command, it does not mean that the signal is not send to it. It may mean that the program can handle it. In other words, it can perfectly receive it correctly, but it chooses to ignore it.

An interactive Ctrl+C in bash is equivalent to a SIGINT signal, which can be handle it (ignored) even by a shell script.

Does that help? Let us know how it goes.
Regards.

---

### Post by bugbear6502 on 2013-11-18
I am presently experiencing this issue; I was using pppd, and need to use sudo to run it.

However, when I hit ctrl-c, it prints "^C" in the terminal but pppd continues to run.

However, if I use a sudo pkill pppd from another terminal instance, the pppd comes to an immediate halt.

if I create a root shell (via sudo bash) pppd can be run, and ctrl-c stops it immediately.

In a bit to diagnose things, I wrote a trivial perl script.
```
#!/usr/bin/perl

use strict;
use Data::Dumper;

$SIG{'INT'} = 'INT_handler';

sub INT_handler {
     print("int recv'd\n");
     print Dumper(getpwuid($<)), "\n";
     exit;
}
sleep(10);

```

If I run this perl script as myself, ctrl-c stops it, and it reports my user name and id.

If I run the script via sudo, ctrl-c ALSO stops it, and reports root as the runner.

So why doesn't ctrl-c stop a sudo'd pppd ?

 BugBear

---

### Post by bugbear6502 on 2013-11-18
Life is getting weird. I thought of (and tried) another permutation.

I created a one line shell script, that called pppd.

I created a sudo shell.

I ran shell script from the command line of that shell.

ctrl-c was (again) ineffective.

So it appears that pppd placed in "any kind of process wrapper" is blocking/absorbing
signals.

So in my case, it's not sudo that has the odd behaviour, it's pppd.

 BugBear

---

