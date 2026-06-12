---
title: "perl pipe behavior different on precise than natty?"
date: 2013-03-31
forum: General Help
---

### Post by markseger on 2013-03-31
Am I imaging this?  I have a very simple perl script and the idea is to tail a file, counting various record types.  BUT I want to set off an alarm every second so I can write some counters.  The thing is this works perfect on natty but when I switch to precise the "Fell Through" message appears and I don't understand what's wrong.  I thought i had heard at one point that alarms could prematurely wake up a read but that is not what's going on here.

```
#!/usr/bin/perl -w

use Time::HiRes;

$SIG{"ALRM"}=\&sigAlarm;

my $interval=1;
my $uInterval=$interval*10**6;
Time::HiRes::ualarm($uInterval, $uInterval);

open TAIL, "tail -f xyz|" or die 'couldnt open xyz';
while (1)
{
  while ($line=<TAIL>)
  {
      Time::HiRes::ualarm(0);
      print $line;
      Time::HiRes::ualarm($uInterval, $uInterval);
  }
  print "Fell through...\n";
}

```
To see what I'm talking about simply 'touch' the file xyz and run the above code in one window.  You'll see the alarm go off every second.  Now do something like "echo 'test'>>xyz" and you'll see that message appear.  If on natty, it will simply go back to printing the alarm going off but on precise it will report "Fell Through".

Any clues as to why?

-mark

---

### Post by rnerwein on 2013-04-01
hi
i don't now anything from perl, but looks a little bit like C.
my question is: where do you init "$line". --> new system -> new stacks !
ciao

---

### Post by markseger on 2013-04-01
> **rnerwein said:**
> hi
i don't now anything from perl, but looks a little bit like C.
my question is: where do you init "$line". --> new system -> new stacks !
ciao

I'm afraid I don't understand the question.  It also occurred to me I should mention that natty is running perl 5.10 and precise 5.14.  It could have nothing to do with ubuntu.
-mark

---

### Post by markseger on 2013-04-01
Here's a new data point - I also asked the question on perlmonks and someone confirmed the same behavior and someone else said they couldn't reproduce it on a fedora system running perl v5.14 so it sounds like it might be something in the distro, perhaps the kernel?
-mark

---

### Post by schragge on 2013-04-01
I'd rather suspect tail than perl here. *tail -f* now uses [inotify]("http://manpages.ubuntu.com/manpages/precise/en/man7/inotify.7.html") while previously it made periodic checks every second or so.

BTW, I cannot reproduce it on my system (Debian wheezy):
```

[COLOR=green]$[/COLOR] uname -mrsv
[COLOR=green]Linux 3.2.0-4-amd64 #1 SMP Debian 3.2.35-2 x86_64
$[/COLOR] grep INOTIFY /boot/config-`uname -r`
[COLOR=green]CONFIG_INOTIFY_USER=y
$[/COLOR] perl -v|grep version
[COLOR=green]This is perl 5, version 14, subversion 2 (v5.14.2) built for x86_64-linux-gnu-thread-multi
$[/COLOR] tail --version|grep tail
[COLOR=green]tail (GNU coreutils) 8.13[/COLOR]

```

---

