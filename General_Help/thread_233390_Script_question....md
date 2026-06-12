---
title: "Script question..."
date: 2006-08-10
forum: General Help
---

### Post by jr.gotti on 2006-08-10
I'm writing a small system info script for my website, and I want to show how long the system has been running...

I tried simply using $(uptime)... however that displayed;

```
02:21:16 up 3 days, 12:29,  4 users,  load average: 0.18, 0.31, 0.41
```

The only thing I want to show is "up 3 days, 12:29"

How can I limit what the command returns?

I'm thinking it would involve piping it through grep or cat, but I don't know exactly what command arguments to use.

Any ideas?

Thanks,
-Jason

(Oh, and if this is in the wrong spot, my sincerest apologies...feel free to move it)

---

### Post by bscbrit on 2006-08-10
> **pixelPOET said:**
> I'm writing a small system info script for my website, and I want to show how long the system has been running...

I tried simply using $(uptime)... however that displayed;

```
02:21:16 up 3 days, 12:29,  4 users,  load average: 0.18, 0.31, 0.41
```

The only thing I want to show is "up 3 days, 12:29"

How can I limit what the command returns?

I'm thinking it would involve piping it through grep or cat, but I don't know exactly what command arguments to use.

Any ideas?

Thanks,
-Jason

(Oh, and if this is in the wrong spot, my sincerest apologies...feel free to move it)


awk or gawk would be ideal for this problem.  See 'man awk' but essentially awk reads the line and puts each word into a different field.  It is a relatively easy problem to simply print the fields that you want to use.  Of course, you will have to define what separates each word (space, comma, EOL etc?) but that is all explained in the man page.  Alternatively, googling for awk or gawk threw up the following:

[http://www.softpanorama.org/Tools/awk.shtml](http://www.softpanorama.org/Tools/awk.shtml)

[http://www.oracle.com/technology/pub/articles/dulaney_awk.html](http://www.oracle.com/technology/pub/articles/dulaney_awk.html)

[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html) (about 2/3rds down the page, search for awk)

I only 'discovered' awk myself a few weeks back and have been kicking myself ever since.  It has quickly solved a series of problems that were becoming unwieldy to solve using bash scripts alone.

---

### Post by jr.gotti on 2006-08-10
Thanks!!

I'm QUITE sure I did this the hard way, but it works great!

```

days=$(uptime | awk '{ print $3,$4 }' | awk -F, '{ print $1 }')
hours=$(uptime | awk -F: '{ print $3 }' | awk '{ print $5, "Hours" }')
minutes=$(uptime | awk -F: '{ print $4 }' | awk -F, '{ print $1, "Minutes" }')
uptime="$days, $hours, $minutes."

```

Now all I have to do is use $uptime in my script and I get a nice, neat

```
[SIZE=2][COLOR=#00430b]3 days, 14 Hours, 06 Minutes.[/COLOR][/SIZE]
```

Thanks again!
-jason

---

### Post by bscbrit on 2006-08-10
> **pixelPOET said:**
> Thanks!!

I'm QUITE sure I did this the hard way, but it works great!

```

days=$(uptime | awk '{ print $3,$4 }' | awk -F, '{ print $1 }')
hours=$(uptime | awk -F: '{ print $3 }' | awk '{ print $5, "Hours" }')
minutes=$(uptime | awk -F: '{ print $4 }' | awk -F, '{ print $1, "Minutes" }')
uptime="$days, $hours, $minutes."

```

Now all I have to do is use $uptime in my script and I get a nice, neat

```
[SIZE=2][COLOR=#00430b]3 days, 14 Hours, 06 Minutes.[/COLOR][/SIZE]
```

Thanks again!
-jason

Great news.  Don't worry about style, that will come with practice.  And you now have another tool in your linux toolkit!

No thanks required - remember to help someone else on the forum!

---

