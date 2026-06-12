---
title: "ALL UPPERCASE on tty1"
date: 2008-04-09
forum: General Help
---

### Post by Old1 on 2008-04-09
I installed 7.10 LAMP server as a test environment to work on a web site .
All is rather nice besides I get only uppercase chars on TTY1.
TTY2 is lowercase as normal.

On TTY1 I get the boot messages in mixed case as expected.
Then it goes:
LOGIN: ...
PASSWORD: ...
USERNAME@TESTBOX: ...
I can login though my username an password have both lowercase chars.
"MC" starts midnight commander which it shouldn't because the name is "mc".
mc as such looks normal, though on its command line all is uppercase again.

I can "su -" and still it looks   ROOT@TESTBOX:~# 

Obviously the keyboard works correctly if I type "ls -a" and "ls -A" it shows my input as "LS -A" but the result is different again as expected.

What could be wrong?

---

### Post by brian_p on 2008-04-09
> **Old1 said:**
> I installed 7.10 LAMP server as a test environment to work on a web site .
All is rather nice besides I get only uppercase chars on TTY1.
TTY2 is lowercase as normal.

On TTY1 I get the boot messages in mixed case as expected.
Then it goes:
LOGIN: ...
PASSWORD: ...
USERNAME@TESTBOX: ...
I can login though my username an password have both lowercase chars.
"MC" starts midnight commander which it shouldn't because the name is "mc".
mc as such looks normal, though on its command line all is uppercase again.

I can "su -" and still it looks   ROOT@TESTBOX:~# 

Obviously the keyboard works correctly if I type "ls -a" and "ls -A" it shows my input as "LS -A" but the result is different again as expected.

What could be wrong?

You can get this behaviour when you login if the Caps Lock key has been activated. Quite what you have done I don't know but the behaviour is normal. It is there for backward compatibility .

Try typing

```
reset
```

---

### Post by Old1 on 2008-04-09
I tried   reset   and got the lower-caps back but now my international chars are gone. Well, they got screwed and apeared as 2 chars.

reboot
testbox login: ...
PASSWORD: ...    <--- from here everything is upper case

ok now is everything upper case but the national chars are normal upper/lower as expected.

Any further suggestion ?

---

### Post by brian_p on 2008-04-09
> **Old1 said:**
> I tried   reset   and got the lower-caps back but now my international chars are gone. Well, they got screwed and apeared as 2 chars.

reboot
testbox login: ...
PASSWORD: ...    <--- from here everything is upper case

ok now is everything upper case but the national chars are normal upper/lower as expected.

Any further suggestion ?

Sorry, nothing else. Maybe someone else? Or Google?

It is so long ago when since it happened to me that I've forgotten the details of the fix.

---

