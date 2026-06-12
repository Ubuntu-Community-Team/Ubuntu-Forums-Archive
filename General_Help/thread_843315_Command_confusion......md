---
title: "Command confusion....."
date: 2008-06-28
forum: General Help
---

### Post by phillips321 on 2008-06-28
Hi guys,

Quick question. The following line works...
```
ping 192.168.0.101 > /home/phillips321/failtime.txt
```

But this one doesn't, any ideas?
```
ping 192.168.0.101 | grep 192.168.0.101 > /home/phillips321/failtime.txt
```

Cheers in advance

---

### Post by spiderbatdad on 2008-06-28
> **phillips321 said:**
> Hi guys,

Quick question. The following line works...
```
ping 192.168.0.101 > /home/phillips321/failtime.txt
```

But this one doesn't, any ideas?
```
ping 192.168.0.101 | grep 192.168.0.101 > /home/phillips321/failtime.txt
```

Cheers in advance

Command can't be piped until it has completed is my guess. Try:
```
ping -c 5 192.168.0.101 | grep 192.168.0.101 > /home/phillips321/failtime.txt
```

---

### Post by Gunman1982 on 2008-06-28
It would be interesting to know what you want to do. Do you want to see when the ping succeeds or when the ping times out? Or is it just a general question with ping as an example?

---

### Post by stumac on 2008-06-28
> **phillips321 said:**
> Hi guys,

Quick question. The following line works...
```
ping 192.168.0.101 > /home/phillips321/failtime.txt
```

But this one doesn't, any ideas?
```
ping 192.168.0.101 | grep 192.168.0.101 > /home/phillips321/failtime.txt
```

Cheers in advance

Interesting.  I get the same result but if I add a count argument to the ping it works correctly.  What seems to happen is that without the count the ping has to be stopped by an ^c. In the first version ping handles the output file o.k. but with the second version the grep does not.

---

### Post by spiderbatdad on 2008-06-28
The example without count, creates an empty file for me, so grep is successful but there is nothing to pipe because the command has not exited...is what I think is happening.

Running the command without a pipe or a count, creates a growing file.

---

### Post by stumac on 2008-06-28
> **spiderbatdad said:**
> The example without count, creates an empty file for me, so grep is successful but there is nothing to pipe because the command has not exited...is what I think is happening.

Running the command without a pipe or a count, creates a growing file.

If pipe has to wait till preceeding command terminates it would be pretty useless.  The grep command should read and process each line as supplied by standard out from ping.  Try the same thing with the ping replaced by any other command outputing lines forever and you will find it works.

I have also tried the ping|grep in cygwin and it works correctly.

I would suggest that this is a bug.

---

### Post by phillips321 on 2008-06-29
fingers crossed this is a bug (cause its confused the hell outta me), what command is causing the bug though? where do i report it?

cheers

---

### Post by ghostdog74 on 2008-06-29
```

ping 192.168.0.101 | grep "icmp_seq=3" 2>&1

```

---

