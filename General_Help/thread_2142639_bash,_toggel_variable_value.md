---
title: "bash, toggel variable value?"
date: 2013-05-06
forum: General Help
---

### Post by zero2xiii on 2013-05-06
Hay all,

Somehow I can not get an answer from google for this. I wan to do a simple if, then, to toggle the value of a variable between 1 and 0:

example:
```
var="0"
selection="a"

if [ $selection = "a" ]; then toggle $var; fi

echo $var
```

The result should be "1".

I want to use this in a little interactive script for selecting and deselecting certain options. All the variables values are either zero or one.

Thanks in advance

EDIT:
Just be clear I want $var to toggle between 1 and 0:
```
echo $var
0
echo $var
1
echo $var
0
echo $var
1
```

---

### Post by matt_symes on 2013-05-06
Hi

Something along the lines of...
```

selection="a";
var=;

[ "$selection" = "a" ] && var="1" || var="0";

echo $var;
```

Is that the kind of thing you want ?

Or is it more like this ?

```

selection="a";
var=0;

[ "$selection" = "a" ] && { [ "$var" = "0" ] && var="1" || var="0"; } 

echo "$var"

```

Kind regards

---

### Post by zero2xiii on 2013-05-06
Hay,

The second option works the way I intend it:

```
~/:~$ [ "$selection" = "a" ] && var="1" || var="0";
~/:~$ echo $var
1
~/:~$ [ "$selection" = "a" ] && { [ $var = "0" ] && var="1" || var="0"; }
~/:~$ echo $var
0
~/:~$ [ "$selection" = "a" ] && { [ $var = "0" ] && var="1" || var="0"; }
~/:~$ echo $var
1
~/:~$ [ "$selection" = "a" ] && { [ $var = "0" ] && var="1" || var="0"; }
~/:~$ echo $var
0

```

I will try this in the script and see if it works there :).

Thanks for the quick response!

EDIT: It works in the script and I will credit you for the help :). The script will be posted in my signature's link "help us help you" thread when I am done.
Thanks

---

### Post by alan9800 on 2013-05-06
you might also try the following code```
var=0
selection="a"

if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi

echo $var
```

---

### Post by zero2xiii on 2013-05-06
Hay,

That does not do what I want, it simply counts up:

```
~/Scripts/DebugTool/:~$ var=0
~/Scripts/DebugTool/:~$ selection="a"
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
1
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
2
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
3
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
4
~/Scripts/DebugTool/:~$ 
]
```

The above post's is a fix so thanks. It also works perfectly in the script so I will use that. Thanks :D

---

### Post by alan9800 on 2013-05-06
> **zero2xiii said:**
> Hay,

That does not do what I want, it simply counts up:

```
~/Scripts/DebugTool/:~$ var=0
~/Scripts/DebugTool/:~$ selection="a"
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
1
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
2
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
3
~/Scripts/DebugTool/:~$ if [ "$selection" = "a" ]; then let "var=-(var=~var)"; fi
~/Scripts/DebugTool/:~$ echo $var
4
~/Scripts/DebugTool/:~$ 
]
```

The above post's is a fix so thanks. It also works perfectly in the script so I will use that. Thanks :DSorry, in my previous post I wrongly used the "~" (bitwise not) operator instead of "^" (bitwise xor) :oops:.
Hopefully the following code should do what you wish:```
var=0
selection="a"

if [ "$selection" = "a" ]; then let "var=1^var"; fi

echo $var

let "var=1^var"
echo $var
```

---

### Post by markbl on 2013-05-06
To toggle var:
```

var=$((var==0))

```

---

### Post by alan9800 on 2013-05-06
> **markbl said:**
> To toggle var:
```

var=$((var==0))

```or also```
var=$((1-var))
```which avoids confusion between boolean values and arithmetic ones.

---

