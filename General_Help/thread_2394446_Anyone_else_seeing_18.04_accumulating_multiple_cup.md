---
title: "Anyone else seeing 18.04 accumulating multiple cups notifier processes?"
date: 2018-06-16
forum: General Help
---

### Post by maglin2 on 2018-06-16
As it says, I get multiple instances of cups notifier processes running with 18.04.

This morning when I booted up there were 9. I have seen up to about 50. I get rid of them from time to time, but they gradually return.

This was a reported bug in 12.04, but was fixed then. [https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/959195](https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/959195)

(I note that someone says at the bottom they had seen it return in 16.04 though. I can't say I ever did).

Is anyone else seeing this behaviour - indicating a return of the bug, or is it just an oddity of my installation?

The only peculiarity of my installation that springs to mind is that it has both xubuntu and unity DEs installed.
Thanks
Dave

---

### Post by VMC on 2018-06-16
The command on that bug report shows zero for my xfce:
```
$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
0
```

---

### Post by maglin2 on 2018-06-16
Thanks for that. One question - do you have a connected printer that could be subscribing to cups notifications? If not I imagine 0 would always be expected.

---

### Post by Claus7 on 2018-06-16
Hello,

in ubuntu flashback 18.04 I get:
```
ps afxvw | grep cups/notifier | grep -v grep | wc -l
1
```

how can someone verify if the connected printer subscribes to cups notifications?

Regards!

---

### Post by maglin2 on 2018-06-17
My guess would be any printer installed in the normal way would be subscribed to cups notifications to tell you job progress, printer status etc.

Having cleared out my running cups notifier processes yesterday this morning I got:
```
~$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
6
```

I've just sent a doc to print (kept printer turned off to avoid waste) and now I get:
```
~$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
8
```

According to [https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/959195](https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/959195) #4 these should all die after 15 minutes - but they don't.

Could someone else please try sending a job to print and looking at the output of ```
~$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
``` before and after, and again 30 minutes later?

Thanks

Dave

---

### Post by Claus7 on 2018-06-17
Hello,

opening computer, no print job sent, the result was 0. Having sent for printing an empty gedit file and issuing again the command, the result is 3.

I will update later...
[EDIT: Still almost after an hour I have the same output.]

Regards!

---

### Post by maglin2 on 2018-06-17
Thanks Claus7.
The fact that you had a count of 1 yesterday and 0 initially today suggests that something at least (presumably reboot) clears these processes on your system, even if it isn't the 15 minute timeout. Mine never clear until I close them manually. Currently I have
```
~$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
10
```


It appears that this isn't an 18.04 bug, but a bug all of my own!
Dave

---

### Post by Claus7 on 2018-06-17
Hello,

> **maglin2 said:**
> Thanks Claus7.
The fact that you had a count of 1 yesterday and 0 initially today suggests that something at least (presumably reboot) clears these processes on your system, even if it isn't the 15 minute timeout. Mine never clear until I close them manually. Currently I have
```
~$ ps afxvw | grep cups/notifier | grep -v grep | wc -l
10
```


It appears that this isn't an 18.04 bug, but a bug all of my own!
Dave

you are welcome! Just to mention that now, issuing again the command, after reboot, without sending any job to printer, the output I get is 2. Initially, it gave me the same impression as you mentioned, that reboot was clearing these processes, yet it seems not. Maybe the magnitude of the number reported has to do with the job someone is sending to print, for example number of pages? 

Just to add one more thing. Issuing the command:
```
ps afxvw | grep cups
```

among other things I got:
>  5301 ?        S      0:00      0     0 86412  5848  0.0  \_ /usr/lib/cups/notifier/dbus dbus://
 5302 ?        S      0:00      0     0 86412  5916  0.0  \_ /usr/lib/cups/notifier/dbus dbus://

where the 0.0 in both cases corresponds to %MEM, which is ... zero. Is it so important as an output message, if the result of occupied memory is zero? I suppose that at next or so reboot these messages should be gone, since the other time the result I had got was zero.

So my question is: if you send a lot of jobs to your printer, isn't it normal for you to have more of that kind of messages? And if affirmative, is it bad if the memory they occupy is zero?

Just some more input that I hope it helps.

Regards!

---

### Post by maglin2 on 2018-06-18
Thanks again.

My output from that command gives 
```

  954 ?        S      0:00      0     0 86412  6132  0.1  \_ /usr/lib/cups/notifier/dbus dbus://
  955 ?        S      0:00      0     0 86412  5792  0.1  \_ /usr/lib/cups/notifier/dbus dbus://
  956 ?        S      0:00      0     0 86412  6012  0.1  \_ /usr/lib/cups/notifier/dbus dbus://
  957 ?        S      0:00      0     0 86412  6028  0.1  \_ /usr/lib/cups/notifier/dbus dbus://


```
So not quite zero memory. I send very few jobs to the printer, and I don't think memory use is ever likely to much of an issue as long as I clear out those processes once  month or so.

Initially I thought this may be a general 18.04 bug. If so I would have filed a report.

As it is I apparently system specific I'll just put up with it. It would be nice to know what is going on though.

---

### Post by maglin2 on 2018-06-20
I now only have the Xubuntu desktop installed, and the problem seems to have gone away.

---

