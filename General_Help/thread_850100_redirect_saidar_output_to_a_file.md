---
title: "redirect saidar output to a file"
date: 2008-07-05
forum: General Help
---

### Post by Novus on 2008-07-05
how can I redirect saidar output to a file?

---

### Post by Claus7 on 2008-07-05
Hello,

saidar [options] > file

Regards!

---

### Post by Novus on 2008-07-05
ahh I wish it was that simple bot it's not :( the file would be empty
it's like top (but top have a -n flag which sadly saidar don't) but I don't want to use top, saidar have better formats IMO..

It'll be used to monitor my server and send the data to a file which I can then pickup with conky on my desktop

---

### Post by Claus7 on 2008-07-05
Hello,

I thought that it might be easy, yet it's not. I tried to see more about input and output redirection, yet to no avail. It would be nice to find out a solution, I think there should be one.

Regards!

---

### Post by ghostdog74 on 2008-07-05
if the only concern about not using top is because of the formats, top's format can be customized to suit your need. you can look at the man page.

---

### Post by Novus on 2008-07-05
> **ghostdog74 said:**
> if the only concern about not using top is because of the formats, top's format can be customized to suit your need. you can look at the man page.

There's 2 things I don't like about top (in this situation)
1) MEM and SWAP is showed in absolute values, I rather have it in %
2) top split the CPU usage % in 8 categories (us, sy, ni, id, wa, hi, si & st) and saidar in 3 (id, sy & us) and I only want those 3.

getting MEM and SWAP in % should be easy with a bash script only thing I got against it is that I always want to take the shortest way to solve a problem :)
I guess same thing can be done with CPU % but I donno how it should be added.. ni + us.. and sy + wa + hi +si? (st is always 0 on that machine)

---

