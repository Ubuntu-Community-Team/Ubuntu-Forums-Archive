---
title: "Help making shell script to automatically remove programs"
date: 2007-11-01
forum: General Help
---

### Post by Primobmx on 2007-11-01
I'am new to linux and want to use a shell script to automatically search and remove any game on the system, I have this so far but iam stuck and not sure what to do next

```
dpkg -l | grep game | less
```

I basically need a way for it to read what grep puts out and remove it, not sure of any other commands to make it read grep.

---

### Post by Primobmx on 2007-11-01
tried force removing but cant get it to do it only to the grep list

---

### Post by kuja on 2007-11-01
sudo apt-get remove $(dpkg -l | grep game | grep -e ^ii.* | cut -d ' ' -f 3 | tr '\n' ' ')

---

### Post by Primobmx on 2007-11-01
Thank you!

now just to figure out what all those commands mean, but it worked nicely thanks.

---

### Post by kuja on 2007-11-01
grep -e means to search using regular expressions ("^" refers to the beginning of the line, ii has to appear immediately after the beginning of the line (which when listing with dpkg means the package is installed), ".*" is a sort of combo, "." refers to any character/space/etc (except the newline character), but when followed by a *, it will be any (and every character) right up to the newline (unless you put something after the .*). You should look into regular expressions, they're rather handy (though it does take a while to learn how to use them) Actually, come to think of it, we could have used "grep -e ^ii.*game.*" instead of "grep -e ^ii | grep game" and it would have worked just as well. 

cut, well, cuts a line at a given delimiter (-d switch, in this case it's a space), and displays the field of your choice (-f switch), we picked 3 for the third field (field following the second space)

tr is the command for "translating"  characters. In this case we're changing '\n' (which refers to the newline character) with ' ' (a space)

Hope that sheds some light on it for you.

---

### Post by Primobmx on 2007-11-02
thanks again

---

