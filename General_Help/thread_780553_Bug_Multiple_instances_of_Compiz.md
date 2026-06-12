---
title: "Bug: Multiple instances of Compiz"
date: 2008-05-03
forum: General Help
---

### Post by Deeta on 2008-05-03
Hiya there I have noticed pretty wonky behavior of my Desktop after I switched compiz off and on several times.

To be more specific:
After a fresh boot with compiz activated as default I have switched compiz on and off four times. It seems that the number of compiz.real routines running is n+1 where n is the times you switched it off and on again.

(I am using a Nvidia 8600GT, my other box using a Ati Radeon 9250 does not show this behavior)

diddl@ubuntu:~$ ps -o comm= -C compiz.real
compiz.real
compiz.real
compiz.real
compiz.real
compiz.real

---

### Post by damis648 on 2008-05-03
Hmm... this must be some anomality, for i have the same card on my laptop and only one instance runs.

---

### Post by Deeta on 2008-05-03
Yeah, it could be a couple of things. Seems that it is not the 8600GT then.

Would anyone know how to access the compiz logs to see what is wrong?
(or even if accessing the logs is the correct step for trying to pinpoint the bug?)

---

### Post by Zorael on 2008-05-03
Workaround!
```
#!/bin/bash

while true;
        if [ "$(pidof compiz.real)" ] & [ "$(pidof metacity)" ]
        then
                killall compiz.real
                break
        else
                sleep 60
        fi
done
```

---

### Post by Deeta on 2008-05-03
Thanks for the Workaround script. I am not sure whether it would work though as I tried killall already earlier. Still got it in my console I think....

diddl@ubuntu:~$ ps -o comm= -C compiz.real
compiz.real
compiz.real
compiz.real
compiz.real
compiz.real
diddl@ubuntu:~$ killall compiz.real
diddl@ubuntu:~$ ps -o comm= -C compiz.real
compiz.real
compiz.real
compiz.real
compiz.real


Strange thing is that one instance is killed but the others are not.
(sudoing the killall does not help either)

I will give your workaround script a try now :D

---

### Post by Deeta on 2008-05-03
I just tried the script and it seems I did something wrong.
Yet my ineptitude with bash scripting prevents me from finding the error in the script :-/
(or my way of having pasted the script into the new file... used nano and later gedit..)

diddl@ubuntu:~$ ./workaround.bash 
./workaround.bash: line 11: syntax error near unexpected token `done'
./workaround.bash: line 11: `done'

---

### Post by Deeta on 2008-05-03
I tried to google some Bash FAQs and got so far to fix some parts.
The problem I have now is that in the following code the if conditional seems to be always true, no matter whether compiz is running or not.
Anyone got some clues how to fix the script?

```
#!/bin/bash
while true;
do
	if [ "$(pidof compiz.real)" ] & [ "$(pidof metacity)" ];
	then
		killall --signal=9 compiz.real
		echo CompiZombie killswitch enganged
		sleep 2s
	else
		echo No CompiZombie detected
		sleep 2s
	fi
done
```

---

### Post by Zorael on 2008-05-04
Pah, goes to show that I should've actually tested the script and not just written it from the top of my head.

```
#!/bin/bash
while true;
do
	if [ "$(pidof compiz.real)" ] **&&** [ "$(pidof metacity)" ];
	then
		echo rraarrr
		killall -9 compiz.real
	else
		# one or none
		sleep 5
	fi
done
```

---

### Post by Deeta on 2008-05-04
@Zorael
Thanks again :) now it works.

I would never ever have found that quirk.
I mean who could guess that bash does not seems to support a normal '&'.
(or is it that the normal AND is a '&&' in bash?  well hehe weirdness, guess I need to really learn bashing other peop... err bashing my terminal :D)

Thanks for helping me find a workaround :)

---

### Post by Deeta on 2008-05-07
After finding a workaround of course there still remains the fact that this is a bug :)

Right now it is brand new and untriaged. So if anyone would like to contribute this link is the way to go :)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/227884](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/227884)

---

