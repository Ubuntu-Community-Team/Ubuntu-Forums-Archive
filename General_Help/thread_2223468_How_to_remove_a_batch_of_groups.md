---
title: "How to remove a batch of groups"
date: 2014-05-11
forum: General Help
---

### Post by frogwarrior on 2014-05-11
For some reason, there have been hundreds of guest groups created on my machine. I want to get rid of them, and theres no way I'm doing that manually. Heres what I was thinking:
```
awk -F ':' '/guest/ { delgroup $1 }' /etc/group
```
it doesn't work though. If I replace delgroup with print, it prints all the names of these guest groups, but I thought I could use awk like the way you can couple other commands to find, using the -exec operator. I tried running it as root, so its not a privilege issue. I know how I can do this in a roundabout way, but I'd prefer to learn an elegant way for future situations. Is there a way to apply an action to each line of text that awk finds?

If not, would something like this work:
```
awk -F ':' '/guest/ { print $1 }' /etc/group | delgroup
```?
I doubt that would work because it will pipe it as a string, not a series of lines (I think anyway), so I'd need to use a loop to iterate through each line. A tool like must be a built in way to do this.

---

### Post by steeldriver on 2014-05-11
I think you could safely do (NOTE: I've left an 'echo' in these expressions so you can test the loops are doing the right thing before actually deleting anything) 

```

while read grp; do echo delgroup "$grp"; done < <(awk -F: '/^guest/ {print $1}' /etc/group)

```

I added a ^ line anchor to your awk regex i.e /**^**guest/ so that it only matches entries with the string 'guest' at the start of the line (just in case there are other entries with that substring in other fields). If you wanted to avoid the external program (awk) altogether I guess you could let bash do the regex matching and splitting e.g.

```

while IFS=: read grp _; do [[ "$grp" =~ ^guest ]] && echo delgroup "$grp"; done < /etc/group

```

---

### Post by frogwarrior on 2014-05-12
It worked. Thanks a lot. Thats some elegant code BTW, I learned a lot from that. Nice one. Thats (the input one <) the one type of pipe I haven't got my head around yet, what does a double << do? I know that >> appends to files (well, output streams), does << take data from the input stream line by line?

---

### Post by steeldriver on 2014-05-12
Thanks - I've learned most of my bash from other more experienced folks on this forum, there's great advice to be had here

The double [FONT=courier new]<<[/FONT] is actually two separate things - the first (leftmost) [FONT=courier new]< [/FONT]is just an input redirection operator which says "get standard input from a file" i.e. the input equivalent of the familiar [FONT=courier new]>[/FONT] for redirecting standard output *to* a file. The second one is really part of a whole construct [FONT=courier new]<(command_list)[/FONT] which is a [process substitution]("http://www.tldp.org/LDP/abs/html/process-sub.html") that effectively makes the result of [FONT=courier new]command_list[/FONT] look like a file - in this case, the 'file' that the other [FONT=courier new]<[/FONT] is going to get the input from. The [FONT=courier new]while read ... do ... done[/FONT] is what makes it process that input line by line.

---

### Post by frogwarrior on 2014-05-12
Ah I see. Thanks again. I know what you mean about these forums, I learn way more from reading the threads here than I do reading books and tutorials. I get to see how other people solve problems, and learn the code used to do it. I'm a web app programmer (starting out, but have a lot of experience from making my own websites), PHP is my strongest language, but bash scripting is becoming 2nd runner (overtaking javascript), I want to find ways I can integrate it all together and use bash scripting as part of my projects. I suppose it will be useful in cases where I have free reign of the web server, there would be plenty of ways I can incorporate bash scripting into the web apps. I've played around with running bash scripts with PHP, and it works for simpler scripts, but have trouble with the more complex ones.  It kind of adds a new layer to the skill set, HTML and CSS for displaying web pages, javascript for manipulating how the browser processes the info, PHP for manipulating how the server processes the info, then bash scripting for gaining full on control of the server.  The cool thing about that, is you can also run external applications like awk and interact scripts. The find command when coupled grep and sed, is incredibly useful when integrated into web applications is incredibly useful. Also, by running bash scripts with PHP web apps, you can do things like transfer database info to openoffice documents. Haven't got into too much of this myself, just been playing around, is there a forum here where we can all share the useful little shell scripts we've come up with?

---

### Post by Vaphell on 2014-05-12
there is a programming subforum
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

