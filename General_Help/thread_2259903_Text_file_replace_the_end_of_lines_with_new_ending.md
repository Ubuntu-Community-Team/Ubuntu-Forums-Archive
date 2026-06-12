---
title: "Text file: replace the end of lines with new ending characters"
date: 2015-01-07
forum: General Help
---

### Post by mc4man on 2015-01-07
Basically I have a file that most but not all of the lines end the same, in this particular  case with ~alpha1 (416 out of 419
I'd like to quickly remove the ~alpha1 & replace with .0
Ex. - first 5 lines,
```
libaudcore.so.3 libaudcore3 #MINVER#
 _Z10aud_resumev@Base 3.6~alpha1
 _Z10int_to_stri@Base 3.6~alpha1
 _Z10str_concatRKSt16initializer_listIPKcE@Base 3.6~alpha1
 _Z10str_printfPKcz@Base 3.6~alpha1
```

So the idea is to get,
```
libaudcore.so.3 libaudcore3 #MINVER#
 _Z10aud_resumev@Base 3.6.0
 _Z10int_to_stri@Base 3.6.0
 _Z10str_concatRKSt16initializer_listIPKcE@Base 3.6.0
 _Z10str_printfPKcz@Base 3.6.0
```

Any ideas for command would be appreciated

---

### Post by Doug S on 2015-01-07
If ~alpha1 does not appear in the middle of the lines somewhere then I think this will work. I tested it on a file test.txt:```
sed 's/~alpha1/\.0/g' test.txt >test_fixed.txt
```If ~alpha1 appears earlier in the line and you don't want to change that one, then I haven't figured it out yet.

---

### Post by steeldriver on 2015-01-07
So something like this?

```

$ sed 's/~alpha1$/.0/' file
libaudcore.so.3 libaudcore3 #MINVER#
 _Z10aud_resumev@Base 3.6.0
 _Z10int_to_stri@Base 3.6.0
 _Z10str_concatRKSt16initializer_listIPKcE@Base 3.6.0
 _Z10str_printfPKcz@Base 3.6.0

```

You can make it edit the file in place by adding the -i switch

---

### Post by Doug S on 2015-01-07
> **steeldriver said:**
> So something like this?Agh, yes, thanks.```
doug@doug-64:~/tcpdump$ cat test.txt
libaudcore.so.3 libaudcore3 #MINVER#
bla bla bla [COLOR=#ff0000]~alpha1 ~alpha1 ~alpha1[/COLOR]  _Z10aud_resumev@Base 3.6~alpha1
 _Z10int_to_stri@Base 3.6~alpha1
 _Z10str_concatRKSt16initializer_listIPKcE@Base 3.6~alpha1
 _Z10str_printfPKcz@Base 3.6~alpha1
doug@doug-64:~/tcpdump$ [COLOR=#ff0000]sed 's/~alpha1$/.0/' test.txt[/COLOR]
libaudcore.so.3 libaudcore3 #MINVER#
bla bla bla [COLOR=#ff0000]~alpha1 ~alpha1 ~alpha1[/COLOR]  _Z10aud_resumev@Base 3.6.0
 _Z10int_to_stri@Base 3.6.0
 _Z10str_concatRKSt16initializer_listIPKcE@Base 3.6.0
 _Z10str_printfPKcz@Base 3.6.0
```

---

### Post by mc4man on 2015-01-07
Thanks guys, that works fine ( sed -i 's/~alpha1$/.0/'

---

