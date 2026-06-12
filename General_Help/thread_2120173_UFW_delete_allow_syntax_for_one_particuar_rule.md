---
title: "UFW delete allow syntax for one particuar rule"
date: 2013-02-25
forum: General Help
---

### Post by bpb_21 on 2013-02-25
I've got a silly little question about UFW.  I set a rule like this:
"514/udp                    ALLOW       192.168.1.0/24"
I don't even remember exactly what I typed to set it.  Anyway, on further reflection, I want to delete this rule.  I've tried every combination of "to", "from", "port", "proto", etc. and received every combination of:
"ERROR: Bad destination address", "ERROR: Wrong number of arguments", "ERROR: Need 'from' or 'to' with 'port'", and read the man ufw pages until my eyes watered.  I can't for the life of me figure out how to delete this rule.  I'm rapidly approaching the point of absolute fury in trying to get rid of this rule.  I even removed and reinstalled UFW.  Still there.  Rather than destroy a perfectly good computer, well - what was a perfectly good computer until this UFW thing, I figured I'd kindly ask the community for a tip.  (If anyone tells me to use Google or read the man pages, a: I've already done that to the point of exhaustion, and b: it will probably push me over the edge into an absolute berzerk rage which we'll all regret!)
Thanks for any/all help!  ):P

---

### Post by steeldriver on 2013-02-25
I've always just deleted by rule number e.g.

```
$ sudo ufw status **numbered**
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW IN    192.168.1.0/24
[ [COLOR=Red]2[/COLOR]] 80/tcp                     ALLOW IN    192.168.1.0/24

**$ sudo ufw delete [COLOR=Red]2[/COLOR]**
Deleting:
 allow from 192.168.1.0/24 to any port 80 proto tcp

```

---

### Post by bpb_21 on 2013-02-25
> **steeldriver said:**
> I've always just deleted by rule number e.g.


Oh, I've tried by number.  Believe me.
```

     To                         Action      From
     --                         ------      ----
[ 1] 514/udp                    ALLOW IN    192.168.1.0/24

sudo ufw delete 1

```

The result of that command is the same as running sudo ufw --help
It's the strangest thing.  Also infuriating.  Did I mention that?  I meant to.  I even did su - to become the root user and then tried all of the above.  Same effect.

---

