---
title: "curl looping in script"
date: 2013-12-30
forum: General Help
---

### Post by j-phat on 2013-12-30
what i have: 
[LIST]
[*]i have a list of URLs in a .txt
[*]a script that can loop through and echo to screen
[*]curl command that outputs to file
[/LIST]
the problem is when i embed the curl statement that works on the terminal into the script,
if doesn't loop through all the links and gives me one output that says page cant be found

this is the script that if i switch to echo, works fine but not curl
```

while read url
do
curl $url >> out.txt
done < x.txt

```

thank you

---

### Post by frankmorris2 on 2013-12-30
Hello,

I am not familiar with curl, but for this kind of work, I use wget.

input.txt = text file with the links (one per line)
output.txt = text file containing the summary of the work

Here is the command line:

```
wget --output-file="output.txt" --input-file="input.txt"
```

Also, there are several options to wget (retry on connection lost, SSL certificates, etc.) that could be useful in this situation.

I hope this helps.

Hace a nice day.

---

### Post by j-phat on 2013-12-30
thank you Frank

---

