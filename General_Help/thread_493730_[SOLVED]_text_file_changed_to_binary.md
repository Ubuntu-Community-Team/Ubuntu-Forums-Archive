---
title: "[SOLVED] text file changed to binary?"
date: 2007-07-06
forum: General Help
---

### Post by lavinog on 2007-07-06
I have a dedicated server for unreal tournament running on a dapper server install.
The problem is one of the ini files has become unreadable using nano and grep, but UT, vi, and cat display and read it fine.

with nano i get this:
```
ï¿½ï¿½[^@U^@T^@2^@0^@0^@4^@R^@P^@G^@.^@M^@u^@t^@U^@T^@2^@0^@0^@4^@R^@P^@G^@]^@
^@S^@a^@v^@e^@D^@u^@r^@i^@n^@g^@G^@a^@m^@e^@I^@n^@t^@e^@r^@v^@a^@l^@=^@1^@2^@0^@
^@S^@t^@a^@r^@t^@i^@n^@g^@L^@e^@v^@e^@l^@=^@1^@0^@
^@P^@o^@i^@n^@t^@s^@P^@e^@r^@L^@e^@v^@e^@l^@=^@9^@0^@
^@I^@n^@f^@i^@n^@i^@t^@e^@R^@e^@q^@E^@X^@P^@O^@p^@=^@1^@
^@I^@n^@f^@i^@n^@i^@t^@e^@R^@e^@q^@E^@X^@P^@V^@a^@l^@u^@e^@=^@5^@
^@L^@e^@v^@e^@l^@D^@i^@f^@f^@E^@x^@p^@G^@a^@i^@n^@D^@i^@v^@=^@8^@0^@.^@0^@0^@0^@0^@0^@0^@
^@M^@a^@x^@L^@e^@v^@e^@l^@u^@p^@E^@f^@f^@e^@c^@t^@S^@t^@a^@c^@k^@i^@n^@g^@=^@5^@
^@E^@X^@P^@F^@o^@r^@W^@i^@n^@=^@2^@0^@0^@0^@
^@B^@o^@t^@B^@o^@n^@u^@s^@L^@e^@v^@e^@l^@s^@=^@0^@
^@S^@t^@a^@t^@C^@a^@p^@s^@[^@0^@]^@=^@5^@0^@0^@

```

with vi or cat  i get this:
```
[UT2004RPG.MutUT2004RPG]
SaveDuringGameInterval=120
StartingLevel=10
PointsPerLevel=90
InfiniteReqEXPOp=1
InfiniteReqEXPValue=5
LevelDiffExpGainDiv=80.000000
MaxLevelupEffectStacking=5
EXPForWin=2000
BotBonusLevels=0
StatCaps[0]=500

```

the main problem is that i am working on a script that uses grep on it but grep won't read it correctly.
if i type:
```
 cat UT2004RPG.ini | grep 'S' UT2004RPG.ini

``` 
i get:
```
Binary file UT2004RPG.ini matches

```

this just started doing this, and i'm sure it was caused by UT.
Is there a way to get it back to normal? I even transfered the file to my win box and it looks fine there too...and when i transfer it back it does it again.

Update:
ok a hex dump of the file has a better description of what happened:
```

0000000 feff 005b 0055 0054 0032 0030 0030 0034
0000010 0052 0050 0047 002e 004d 0075 0074 0055
0000020 0054 0032 0030 0030 0034 0052 0050 0047
0000030 005d 000a 0053 0061 0076 0065 0044 0075
0000040 0072 0069 006e 0067 0047 0061 006d 0065
0000050 0049 006e 0074 0065 0072 0076 0061 006c

```

while the good file should look like:
```

0000000 555b 3254 3030 5234 4750 4d2e 7475 5455
0000010 3032 3430 5052 5d47 530a 7661 4465 7275
0000020 6e69 4767 6d61 4965 746e 7265 6176 3d6c
0000030 3231 0a30 7453 7261 6974 676e 654c 6576
0000040 3d6c 3031 500a 696f 746e 5073 7265 654c
0000050 6576 3d6c 3039 490a 666e 6e69 7469 5265

```

any idea how to remove the null characters?
It almost looks like it was converted to unicode.

---

### Post by Mr. C. on 2007-07-06
Just set the editor (and possibly other programs) to you use to not use UNICODE per run:

```
LANG=C vim
LANG=C nano
```

or for all prorgrams:

```
LANG=C
export LANG
vim yourfile
nano yourfile
```

MrC

---

### Post by lavinog on 2007-07-06
Thank you for the info.

I was able to temporarily fix my situation by copying and pasting to a new file, but i will try that next time.

---

