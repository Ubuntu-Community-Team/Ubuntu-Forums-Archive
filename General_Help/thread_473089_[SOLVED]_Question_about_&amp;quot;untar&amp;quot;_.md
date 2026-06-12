---
title: "[SOLVED] Question about &amp;quot;untar&amp;quot; commands"
date: 2007-06-13
forum: General Help
---

### Post by Interestedinthepenguin on 2007-06-13
I've begun 'untarring' things through the terminal, and have a couple of questions regarding the tar commands, 'zvvxf', 'zvxf', and 'xzvf'.  

What's the difference between the three?

What do the commands stand for?  

Thanks.

---

### Post by ironfistchamp on 2007-06-13
I *think* that the last two are the same just in a different order. I am not sure what the double V means. Curently on a Windows computer so can't investigate. 

Have you had a look at the manual?

```

man tar

```

(For those who don't know how to read the manuals)

HTH

Ironfistchamp

---

### Post by meatpan on 2007-06-13
The 'vv' means print extra verbose output, such as file properties.  There are no other differences between the options you listed.

---

### Post by Interestedinthepenguin on 2007-06-13
Thanks, to both of you.  

@ironfistchamp:  

I've looked at the manual, but it didn't tell me straight out, at least, what the command stood for.

I looked again, and here's what I have to ask:  

Is the command, 'zvxf', actually shorthand for: -z for 'uncompress', -v for 'verbose' or 'label', -x for 'extract', and f for whatever f stands for?  

*"noob" written all over face*

---

### Post by spier on 2007-06-13
> **Interestedinthepenguin said:**
> Thanks, to both of you.  

@ironfistchamp:  

I've looked at the manual, but it didn't tell me straight out, at least, what the command stood for.

...Since you asked had I looked at the manual,  I looked again, and here's what I have to ask:  

Is the command, 'zvxf', actually shorthand for: -z for 'uncompress', -v for 'verbose' or 'label', -x for 'extract', and f for whatever f stands for?  

*"noob" written all over face*

reading further:

 -f, --file [HOSTNAME:]F
              use archive file or device F (default "-", meaning stdin/stdout)

       tar -xvvf foo.tar
should read as -xtract -vverbosely -file foo.tar!?

---

