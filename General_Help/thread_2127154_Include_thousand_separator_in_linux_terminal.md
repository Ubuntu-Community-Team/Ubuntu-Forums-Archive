---
title: "Include thousand separator in linux terminal"
date: 2013-03-19
forum: General Help
---

### Post by Binary-Synapse on 2013-03-19
Hello.

How can I include the thousand separator when I'm listing directory contents?
I would also like that setting to be system-wide.

So instead of this:
```
ls Documents -l
-rwxrwxrwx user user 123456789 Files.txt
```


I would like to obtain this:
```
ls Documents -l
-rwxrwxrwx user user 123.456.789 Files.txt
```


Thank you

---

### Post by schragge on 2013-03-19
At least, you can
```

[COLOR=green]$[/COLOR] ls -hl Documents
[COLOR=green]-rwxrwxrwx 1 user user 117M ... Files.txt[/COLOR]

```

---

### Post by Binary-Synapse on 2013-03-20
Hello,

Yes the 'h' switch is nice when you want to read it in 'human-format'.

But the purpose would be to include the thousand separator, to make it more easy to read the _exact_ size of a specific file.

---

### Post by schragge on 2013-03-20
Then try
```
ls -log --time-style=+|sed -r 's/^[^ ]* *[^ ]* *//;s/ +/\t/;:l;s/(.*[0-9])([0-9]{3}[,\t])/\1,\2/;tl'
```
or, if your login shell is *bash* (would also work with ksh93, pdksh, or with any shell if using */usr/bin/printf* from GNU coreutils)
```
ls -log --time-style=+|while read -r p l s n;do printf "%'15d %s\n" $s "$n";done
```

---

### Post by Binary-Synapse on 2013-03-21
Hello.

It works.
Huge commands   though... :-)

Thank you schragge

---

### Post by schragge on 2013-03-21
Well, the first one may be shortened a bit if you don't mind all the other data you'll get with *ls -l*:
```
ls -l|sed -r 's/ +/\t/5;:l;s/(.*[0-9])([0-9]{3}[,\t])/\1,\2/;tl'
```
For the second, the following also should work, but it makes the command only marginally shorter
```
ls -log|while read -r p l s r;do printf "%'15d %s\n" $s "$r";done
```

---

### Post by schragge on 2013-03-23
FYI, the GNU coreutils 8.21 sport a new command [numfmt]("http://www.pixelbeat.org/docs/numfmt.html"), hopefully to be included in Ubuntu after *raring*.

---

### Post by Binary-Synapse on 2013-03-25
Hi schragge

That really is a nice feature, to include in a near future.

I have always had trouble reading exact file sizes from Linux terminals.

Thanks for sharing.

---

