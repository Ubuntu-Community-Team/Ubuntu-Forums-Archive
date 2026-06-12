---
title: "sed match more than one"
date: 2013-06-15
forum: General Help
---

### Post by HiImTye on 2013-06-15
I'm sure that I'm missing something painfully obvious, but this isn't working for me
```
a=$(nvida-smi); echo "$a" | grep -o '[0-9]\+C'; echo "$a" | sed -n 's|.*\([0-9]\+\)C.*|\1|p'
```
the output  I'm getting is like this
```
64C
4
```when I should be getting two digits on the bottom as well. any thoughts?
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by zero2xiii on 2013-06-15
Hay,

If what you are trying to do is display the current tempratures, awk will be MUCH easier and cleaner to do.

Please be more clear on what you wish to display.

Thanks

---

### Post by Lars Noodén on 2013-06-15
I'm not sure what 'nvida-smi' is supposed to do, I don't have it.  But shouldn't you include beginning of line and end of line markers in you pattern?  Also, the .* at the beginning is greedy and gobbling up any digits except the one before 'C'.

```

 sed -n 's|**^**[^0-9]*\([0-9]\+\)C.***$**|\1|p'

```

---

### Post by prodigy_ on 2013-06-15
First, you don't need sed becuse grep has **-o** option. See **man grep**. Second, since temps are unlikely to be single digits, you can be more specific:
```
a=$(nvida-smi)
echo "$a" | grep -o '[0-9]\{2,3\}C'
```

---

### Post by HiImTye on 2013-06-15
> Please be more clear on what you wish to display.I'm grabbing my GPU temp from a bunch of other nonsense (fan speed, etc)

> Also, the .* at the beginning is greedy and gobbling up any digits except the one before 'C'.that was it, thanks :D
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by HiImTye on 2013-06-15
> **prodigy_ said:**
> First, you don't need sed becuse grep has **-o** option. See **man grep**.I'm using sed to edit the output, so I figured I'd do it all with one tool  

(also, I was using -o in my first post, I just omitted it when I re-typed it on my tablet, since ConnectBot has no copy feature)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by zero2xiii on 2013-06-15
Hay,

Yes I gathered the collect temp info part,

```
 nvidia-smi | awk 'NR==9 {print $3}'
```

However my nvidia-smi has just that one temp. I am sure you can figure out the above syntax to print more than one result.
Grep, as mentioned above is also a nice alternative :)

Cheers

---

### Post by HiImTye on 2013-06-15
it works fine with sed, here's what I ended up with
```
w3=$(sensors | sed '/^$/d;/coretemp-/d;/atk0110/d'; echo 'Adapter: nVidia GeForce GT 220'; nvidia-smi | sed -n 's|[^0-9]*\([0-9]\+\)C.*|GPU:     \1°C|p')
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by pbrane on 2013-06-15
Another way to get the nvidia GPU temperature is with nvidia-settings.
```

nvidia-settings -t -q GPUCoreTemp

```

---

### Post by HiImTye on 2013-06-15
> **pbrane said:**
> Another way to get the nvidia GPU temperature is with nvidia-settings.
```

nvidia-settings -t -q GPUCoreTemp

```

nvidia-settings requires X to be running, even just to print to the terminal
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

