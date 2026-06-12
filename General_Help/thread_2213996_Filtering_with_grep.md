---
title: "Filtering with grep"
date: 2014-03-29
forum: General Help
---

### Post by chris137 on 2014-03-29
Hi,
so I'd like to filter some strings out of a line of a document.
I got a document with over 4000 lines consisting of lines like this:
```
auth.log:Mar 23 04:48:21 mail sshd[19971]: Failed password for root from abc.def.ghi.jkl port 1889 ssh2
```
I'd like grep (or maybe something else?) to write only "Failed password for root from abc.def.ghi.jkl" in a file.
I thought of
```
grep -v "auth.log*]:" >> output.txt
```
But my usage of a wildcare does not seem to work. Also I am not sure if I understood the usage of -v correctly.
At this point obviously only the part before "Failed..." would get filtered (if entered properly).

Anyone able to help?
If done I'd also like to sort the output by name.
Ubuntu's standard text-editor does not seem to be able to do this.

Hope someone can help

---

### Post by apohal9 on 2014-03-29
The usage of "-v" will grep all lines except the matching ones to your command. So if you do > grep -v "Failed password" you will get all the lines that do not have "Failed password" in them.
To filter out those lines, omit the -v and simply use > grep "Failed password" >> output.txt

**man grep**

>        -v, --invert-match
              Invert the sense of matching, to select non-matching lines.  (-v
              is specified by POSIX.)



---

### Post by chris137 on 2014-03-29
So this will not work at all?
File:
```
Mar 22 11:54:38 mail sshd[18096]: Failed password for root from 202.17.185.99 port 40410 ssh2
Mar 21 14:43:16 mail sshd[16158]: Failed password for root from 116.10.191.171 port 2378 ssh2
```
What I want:
```
 grep *idontknowthatswhyimhere*
```
The output:
```
Failed password for root from 202.17.185.99
Failed password for root from 116.10.191.171
```

I guess this will not be possible with grep but after that it should be sorted by name.
So the final output would be:
```
Failed password for root from 116.10.191.171
Failed password for root from 202.17.185.99
```

---

### Post by steeldriver on 2014-03-29
You can tell grep to only output the actual matching part of the line (instead of the whole line in which the match occurs) using the -o option

```
grep -o 'Failed .*' *yourfile*
```

(matches the string "Failed" followed by a space and then zero or more additional characters)

See man grep

```

       -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.

```

EDIT: if you want to include the IPv4 address, something like this might work (although note that it matches sequences of up to 3 digits - not quite the same as IP octets) 

```

$ grep -Eo 'Failed .* [0-9]{,3}\.[0-9]{,3}\.[0-9]{,3}\.[0-9]{,3}' *yourfile *| sort
Failed password for root from 116.10.191.171
Failed password for root from 202.17.185.99

```

You could write the regular expression more compactly using a repeated group as 

```
'Failed .* [0-9]{,3}**([.][0-9]{,3}){3}**'
```

---

### Post by apohal9 on 2014-03-29
Ok. So this solution is getting ugly (because of it's middle of the night here ;) ). Supposing your log is named auth.log:

> awk -F" " '{print $6" "$7" "$8" "$9" "$10" "$11}' auth.log | sort

This will do the job if your lines are really like
> Mar 22 11:54:38 mail sshd[18096]: Failed password for root from 202.17.185.99 port 40410 ssh2

---

### Post by chris137 on 2014-03-29
[COLOR=#000000]steeldriver[/COLOR]'s solution is not too good because there would still be the port at the end.
But works good until this point.

		apohal9 is actually exactly what I was looking for.
One-liner even.
Thanks so much!

---

### Post by apohal9 on 2014-03-30
But I like steeldriver's solution more as this is regex based and more precise then mine.
Anyway, both will work.

If ok, mark the thread as solved :)

---

