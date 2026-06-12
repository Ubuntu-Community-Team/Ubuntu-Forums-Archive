---
title: "[bash] Grep strange behaviour"
date: 2013-06-17
forum: General Help
---

### Post by vinay_wagh on 2013-06-17
I was 'grep'ping a text file:
```
vvss@vvss-laptop:~/tmp $ cat abc.txt 
abc pqr
abcpqr
pqr abc
a pqr
ab cpqr
```
grep behaves strangely if I add the --color=always option parsed to grep -v. Following are the outputs of the three different option of --color and also without grep -v parsing:

```
 vvss@vvss-laptop:~/tmp $ grep -r abc abc.txt | grep -v abcpqr
abc pqr
pqr abc
```
```
 vvss@vvss-laptop:~/tmp $ grep -r --color=auto abc abc.txt | grep -v abcpqr
abc pqr
pqr abc

```
```
vvss@vvss-laptop:~/tmp $ grep -r --color=never abc abc.txt | grep -v abcpqr
abc pqr
pqr abc

```
```
vvss@vvss-laptop:~/tmp $ grep -r --color=always abc abc.txt | grep -v abcpqr
[COLOR=#ff0000]abc[/COLOR] pqr
[COLOR=#ff0000]abc[/COLOR]pqr
pqr [COLOR=#ff0000]abc[/COLOR]
```
```
 vvss@vvss-laptop:~/tmp $ grep -r abc abc.txt | grep -v abcpqr
abc pqr
pqr abc

```

What happens if you give --color=always option? Why does it ignore the grep -v parsing? 

Thanks in advance

VInay

---

### Post by Vaphell on 2013-06-17
it puts formatting sequences in the output. When you print to terminal, it interprets these special sequences to change color to highlight matches, but when you pipe the colored output to another command they are polluting your data.
use --color=always only in the last step, when you print out to terminal.

If you want to see these sequences redirect grep output with --color=always to a file and open it in gedit. That's what your* grep -v* step gets

---

### Post by vinay_wagh on 2013-06-18
Thanks Vaphell for the explaination.

I want to use --color=always  in the last step and wish to print the output to terminal. However  while printing I dont want string 'abcpqr'. So logically I would parse  it to grep -v. The reason I gave --color=always was I wanted coloured  output at the end, but after parsing the colour effect vanishes.

Now I agree with you for regarding formatting sequence. I could see that by parsing the output to less (without -R option).

So to get the filtered output, redirecting is the only way out? 

VInay

---

### Post by vinay_wagh on 2013-06-18
Ah silly me :-)

Here is a simplest solution:

```

grep -v abcpqr abc.txt | grep abc

```

This  gives me a coloured output without lines containing 'abcpqr'...

VInay

---

### Post by markbl on 2013-06-18
```

grep -w abc abc.txt

```

---

### Post by HiImTye on 2013-06-18
> **markbl said:**
> ```

grep -w abc abc.txt

```

+1 fewest steps

and as per usual, Vaphell knows what's wrong! I may like to contradict him sometimes, but the man knows his stuff
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

