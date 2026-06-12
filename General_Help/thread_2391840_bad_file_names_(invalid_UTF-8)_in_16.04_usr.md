---
title: "bad file names (invalid UTF-8) in 16.04 /usr"
date: 2018-05-13
forum: General Help
---

### Post by Skaperen on 2018-05-13
these files:

```
/usr/share/backgrounds/Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg
/usr/share/backgrounds/The_Land_of_Edonias_by_*.jpg
/usr/share/ca-certificates/mozilla/Certinomis_-_Autorit*_Racine.crt
/usr/share/ca-certificates/mozilla/NetLock_Arany_=Class_Gold=_F*ny.crt
/usr/share/ca-certificates/mozilla/T*TAK_UEKAE_K*k_Sertifika_Hizmet_Sa*m_3.crt
/usr/share/ca-certificates/mozilla/T*RKTRUST_Elektronik_Sertifika_Hizmet_Sa*_H5.crt
```

have invalid UTF-8 characters in the file names.  aren't we supposed to be using UTF-8 now days?  these produce errors when it try to back them up to AWS S3 storage.  but at least these are system files i can easily get back by doing a re-install, and backing up all of /usr with "aws s3 sync" just skips bad ones and keeps going.

---

### Post by papibe on 2018-05-14
Hi Skaperen.

As far as I can tell, they are in utf-8. My guess is your environment was switched out of utf8.

Could you open a terminal, run these commands, and post back the results? (you can copy/paste the text with the mouse):
```
more /etc/default/locale 

locale

env | grep -i utf

env | grep -i lang

cat  ~/.pam_environment
```
Regards.

---

### Post by Skaperen on 2018-05-14
valid UTF-8 characters do display with the correct glyphs where i see what i know.  i can read some of Danish, Dutch, Esperanto, French, German, Norwegian, Russian, and Swedish and they show up correctly enough that i can read them.  the CJK stuff i do not know.  i have done some programming in Python3 to display some UTF-8 character tables and things look right through several code planes i have done.

the error messages i see are coming from the AWS S3 service.  here is what they look like:

```
Script started on Sun May 13 04:02:23 2018
04:02:23 [17454] EXECUTING: 'aws' 's3' 'sync' '--delete' '--no-follow-symlinks' '--exclude' 'noback*' '--exclude' 'noback*/*' '--exclude' 'tmp' '--exclude' 'tmp/*' '--exclude' '.noback*' '--exclude' '.noback*/*' '--exclude' '.tmp' '--exclude' '.tmp/*' '--exclude' '*/noback*' '--exclude' '*/noback*/*' '--exclude' '*/tmp' '--exclude' '*/tmp/*' '--exclude' '*/.noback*' '--exclude' '*/.noback*/*' '--exclude' '*/.tmp' '--exclude' '*/.tmp/*' '--exclude' '.bash_history.d/*' '--exclude' '.cache/*' '--exclude' '.local/*' '--exclude' '.mozilla/*' '--exclude' '.ssh-priv/*' '--exclude' 'junk/*' '--exclude' 's3logs/*' '/usr' 's3://MYBUCKETNAME/b/lt1/usr'
upload: ../usr/local/bin/run-backups to s3://MYBUCKETNAME/b/lt1/usr/local/bin/run-backups
upload failed: ../usr/share/backgrounds/Cielo_estrellado_by_Eduardo_Diez_Vi\udcc3\udcb1uela.jpg to s3://MYBUCKETNAME/b/lt1/usr/share/backgrounds/Cielo_estrellado_by_Eduardo_Diez_Vi\udcc3\udcb1uela.jpg 'utf-8' codec can't encode character '\udcc3' in position 63: surrogates not allowed
upload failed: ../usr/share/backgrounds/The_Land_of_Edonias_by_\udcce\udc93\udcce\udcb9\udccf\udc89\udccf\udc81\udcce\udcb3\udcce\udcbf\udccf\udc82_\udcce\udc91\udccf\udc81\udcce\udcb3\udccf\udc85\udccf\udc81\udcce\udcbf\udccf\udc80\udcce\udcbf\udccf\udc85\udcce\udcbb\udcce\udcbf\udccf\udc82.jpg to s3://MYBUCKETNAME/b/lt1/usr/share/backgrounds/The_Land_of_Edonias_by_\udcce\udc93\udcce\udcb9\udccf\udc89\udccf\udc81\udcce\udcb3\udcce\udcbf\udccf\udc82_\udcce\udc91\udccf\udc81\udcce\udcb3\udccf\udc85\udccf\udc81\udcce\udcbf\udccf\udc80\udcce\udcbf\udccf\udc85\udcce\udcbb\udcce\udcbf\udccf\udc82.jpg 'utf-8' codec can't encode character '\udcce' in position 51: surrogates not allowed
upload failed: ../usr/share/ca-certificates/mozilla/Certinomis_-_Autorit\udcc3\udca9_Racine.crt to s3://MYBUCKETNAME/b/lt1/usr/share/ca-certificates/mozilla/Certinomis_-_Autorit\udcc3\udca9_Racine.crt 'utf-8' codec can't encode character '\udcc3' in position 60: surrogates not allowed
upload failed: ../usr/share/ca-certificates/mozilla/NetLock_Arany_=Class_Gold=_F\udcc5\udc91tan\udcc3\udcbas\udcc3\udcadtv\udcc3\udca1ny.crt to s3://MYBUCKETNAME/b/lt1/usr/share/ca-certificates/mozilla/NetLock_Arany_=Class_Gold=_F\udcc5\udc91tan\udcc3\udcbas\udcc3\udcadtv\udcc3\udca1ny.crt 'utf-8' codec can't encode character '\udcc5' in position 68: surrogates not allowed
upload failed: ../usr/share/ca-certificates/mozilla/T\udcc3\udc9cB\udcc4\udcb0TAK_UEKAE_K\udcc3\udcb6k_Sertifika_Hizmet_Sa\udcc4\udc9flay\udcc4\udcb1c\udcc4\udcb1s\udcc4\udcb1_-_S\udcc3\udcbcr\udcc3\udcbcm_3.crt to s3://MYBUCKETNAME/b/lt1/usr/share/ca-certificates/mozilla/T\udcc3\udc9cB\udcc4\udcb0TAK_UEKAE_K\udcc3\udcb6k_Sertifika_Hizmet_Sa\udcc4\udc9flay\udcc4\udcb1c\udcc4\udcb1s\udcc4\udcb1_-_S\udcc3\udcbcr\udcc3\udcbcm_3.crt 'utf-8' codec can't encode character '\udcc3' in position 41: surrogates not allowed
upload failed: ../usr/share/ca-certificates/mozilla/T\udcc3\udc9cRKTRUST_Elektronik_Sertifika_Hizmet_Sa\udcc4\udc9flay\udcc4\udcb1c\udcc4\udcb1s\udcc4\udcb1_H5.crt to s3://MYBUCKETNAME/b/lt1/usr/share/ca-certificates/mozilla/T\udcc3\udc9cRKTRUST_Elektronik_Sertifika_Hizmet_Sa\udcc4\udc9flay\udcc4\udcb1c\udcc4\udcb1s\udcc4\udcb1_H5.crt 'utf-8' codec can't encode character '\udcc3' in position 41: surrogates not allowed
                                                                                  
[[ 15m21s real 921.300 - user 375.188 - sys 8.036 - 41.59% ]]
04:17:44 [17454] FINISHED - status = 1
```

these codes are definitely in the Unicode surrogate range (the pairings used in UTF-16 to encode Unicode above U+65535) which are not allowed in UTF-8.  for more information see [https://en.wikipedia.org/wiki/UTF-16#U+D800_to_U+DFFF](https://en.wikipedia.org/wiki/UTF-16#U+D800_to_U+DFFF)

here is the output of the commands you gave for the user i use to read and post to most forums:```
lt1/forums /home/forums 1> more /etc/default/locale
#  File generated by update-locale
LANG="en_US.UTF-8"
lt1/forums /home/forums 2> locale
LANG=en_US.utf8
LANGUAGE=en_US.utf8
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C
lt1/forums /home/forums 3> env | grep -i utf
LANG=en_US.utf8
LANGUAGE=en_US.utf8
lt1/forums /home/forums 4> env | grep -i lang
LANG=en_US.utf8
GDM_LANG=en_US
LANGUAGE=en_US.utf8
lt1/forums /home/forums 5> cat  ~/.pam_environment
cat: /home/forums/.pam_environment: No such file or directory
lt1/forums /home/forums 6>
```

---

### Post by papibe on 2018-05-14
Thanks. This is getting interesting.

Let's try one file name:
```
Cielo_estrellado_by_Eduardo_Diez_Vi**[COLOR="#FF0000"]ñ[/COLOR]**uela.jpg
```
That's using the small case Latin n with tilde (la letra eñe).

The proper UTF-8 encoding of that letter is c3b1 (see here: [UTF-8 encoding table and Unicode characters]("https://www.utf8-chartable.de/")).

In my system, this is correctly encoded:
```
$ ls -1 Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg | od -t x1
0000000 43 69 65 6c 6f 5f 65 73 74 72 65 6c 6c 61 64 6f
0000020 5f 62 79 5f 45 64 75 61 72 64 6f 5f 44 69 65 7a
0000040 5f 56 69 **[COLOR="#FF0000"]c3 b1[/COLOR]** 75 65 6c 61 2e 6a 70 67 0a
0000056

```
For what I can see in your error message here:
```
...Cielo_estrellado_by_Eduardo_Diez_Vi\udc**[COLOR="#FF0000"]c3[/COLOR]**\udc**[COLOR="#FF0000"]b1[/COLOR]**uela.jpg...
```
It is also encoded correctly, however it is being *interpreted* as escape Unicode.

I've seen this error very often in Python scripts, which by default interprets all strings as Unicode. See this example "[UnicodeEncodeError: 'utf-8' codec can't encode: surrogates not allowed]("https://stackoverflow.com/questions/27366479/python-3-os-walk-file-paths-unicodeencodeerror-utf-8-codec-cant-encode-s")".

I hope that helps, or points you in the right direction.
Let us know how it goes.
Regards.

---

### Post by Skaperen on 2018-05-15
that certainly fits the issue i am seeing.  apparently python is not handling the UTF-8 in the file name in the right way, very likely due to some bad code in scripts expecting to run in python2 which was way off in handling UTF-8.

i am getting some varying results trying to do what you did.  the variation depends on whether or not it was run in a shell script.  bash is my interactive shell.  below i switched to a program i wrote called "xd32" to see the output of "ls" more clearly.  it looks i am getting backslash octal encoding of the bytes when i run it as a real command.
 
```
lt1/forums /home/forums 26> ls -l try1.sh
-rwxr--r-- 1 forums forums 107 May 15 02:19 try1.sh
lt1/forums /home/forums 27> cat try1.sh
#!/bin/bash
( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg ) | od -t x1
lt1/forums /home/forums 28> ./try1.sh
0000000 43 69 65 6c 6f 5f 65 73 74 72 65 6c 6c 61 64 6f
0000020 5f 62 79 5f 45 64 75 61 72 64 6f 5f 44 69 65 7a
0000040 5f 56 69 c3 b1 75 65 6c 61 2e 6a 70 67 0a
0000056
lt1/forums /home/forums 29> ( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg ) | od -t x1
0000000 43 69 65 6c 6f 5f 65 73 74 72 65 6c 6c 61 64 6f
0000020 5f 62 79 5f 45 64 75 61 72 64 6f 5f 44 69 65 7a
0000040 5f 56 69 5c 33 30 33 5c 32 36 31 75 65 6c 61 2e
0000060 6a 70 67 0a
0000064
lt1/forums /home/forums 30> ls -l try2.sh
-rwxr--r-- 1 forums forums 103 May 15 02:24 try2.sh
lt1/forums /home/forums 31> cat try2.sh
#!/bin/bash
( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg ) | xd32
lt1/forums /home/forums 32> ./try2.sh
000000000  4369656c 6f5f6573 7472656c 6c61646f  5f62795f 45647561 72646f5f 4469657a |Cielo_estrellado_by_Eduardo_Diez|
000000020  5f5669c3 b175656c 612e6a70 670a                                          |_Vi..uela.jpg.|
lt1/forums /home/forums 33> ( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg ) | xd32
000000000  4369656c 6f5f6573 7472656c 6c61646f  5f62795f 45647561 72646f5f 4469657a |Cielo_estrellado_by_Eduardo_Diez|
000000020  5f56695c 3330335c 32363175 656c612e  6a70670a                            |_Vi\303\261uela.jpg.|
lt1/forums /home/forums 34>
```

i did did find that the "echo" command output the real byte codes whether in a script or interactive.  and "ls", when not outputting to a pipe, outputs question marks.

```
lt1/forums /home/forums 47> ls -l try4.sh
-rwxr--r-- 1 forums forums 96 May 15 02:40 try4.sh
lt1/forums /home/forums 48> cat try4.sh
#!/bin/bash
( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg )
lt1/forums /home/forums 49> ./try4.sh
Cielo_estrellado_by_Eduardo_Diez_Vi??uela.jpg
lt1/forums /home/forums 50> ( cd /usr/share/backgrounds && ls -1 Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg )
Cielo_estrellado_by_Eduardo_Diez_Vi\303\261uela.jpg
lt1/forums /home/forums 51> ls -l try3.sh
-rwxr--r-- 1 forums forums 95 May 15 02:42 try3.sh
lt1/forums /home/forums 52> cat try3.sh
#!/bin/bash
( cd /usr/share/backgrounds && echo Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg )
lt1/forums /home/forums 53> ./try3.sh
Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg
lt1/forums /home/forums 54> ( cd /usr/share/backgrounds && echo Cielo_estrellado_by_Eduardo_Diez_Vi*uela.jpg )
Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg
lt1/forums /home/forums 55>
```

i guess lots of programmers are not fully Unicode and UTF-8 ready, yet.  i think things could be easier if UTF-16 would go away.

now to try to study the AWS Python code to see if this is an issue in the client.  if so, it might be fixable.

---

### Post by papibe on 2018-05-15
This is a script that may help you. It get the offending filenames and print them in different ways.

You can see that Python3 stores the string in Unicode (ñ represented as 0xf1, see table liked above), and a way to converted to UTF-8.
```
#!/usr/bin/python3

from os import listdir
from os.path import isfile, join

# Directory with ofending filenames
mypath = "/usr/share/backgrounds"

# List of file names in mypath
onlyfiles = [f for f in listdir(mypath) if isfile(join(mypath, f))]

cielo = onlyfiles[6]    # "Cielo_estrellado...."

print('{}'.format(cielo))       # results would depend on your environment
print('{0!a}'.format(cielo))    # forced to ascii

# Print each character by itself
for char in cielo:
    value = ord(char)
    # print non ascii characters in a special way
    if (value > 127):
        print('({0}->{1})'.format(char, hex(value)), end='')
    else:
        print('{}'.format(char), end='')

print()

print('{}'.format(cielo.encode('utf8')))    # conversion to UTF-8

```
This is the output in my system:
```
$ ./script.py 
Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg
'Cielo_estrellado_by_Eduardo_Diez_Vi\xf1uela.jpg'
Cielo_estrellado_by_Eduardo_Diez_Vi(ñ->0xf1)uela.jpg
b'Cielo_estrellado_by_Eduardo_Diez_Vi\xc3\xb1uela.jpg'

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Skaperen on 2018-05-15
here is what i got ...```
lt1/forums /home/forums 3> py3 scan_names.py
Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg
'Cielo_estrellado_by_Eduardo_Diez_Vi\udcc3\udcb1uela.jpg'
Cielo_estrellado_by_Eduardo_Diez_Vi(&#65533;->0xdcc3)(&#65533;->0xdcb1)uela.jpg
Traceback (most recent call last):
  File "scan_names.py", line 28, in <module>
    print('{}'.format(cielo.encode('utf8')))    # conversion to UTF-8
UnicodeEncodeError: 'utf-8' codec can't encode character '\udcc3' in position 35: surrogates not allowed
lt1/forums /home/forums 4>
```

bug in forum:  when i do Preview Post it shows the post OK, but does not reload in in the input buffer.  maybe because of line 2 or line 4 of the code.

---

### Post by Skaperen on 2018-05-15
also, when i tried to edit the post to fix a typo (s/reload in in the/reload it in the/) the typing buffer came up empty, just as in the preview case.

---

### Post by Skaperen on 2018-05-15
i was playing around with what i believe is correct code in python3 to convert between unicode in strings and utf-8 in bytes and it all seems to be working for me.  i get _\xc1\xb3_ in bytes and _\xf1_ in strings as expected.

---

