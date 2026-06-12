---
title: "[SOLVED] Program for naming files"
date: 2008-04-08
forum: General Help
---

### Post by alejandro.mc on 2008-04-08
I'd like to know if a program to name files exist. What I mean is the following. I have lots of files in a folder, lots of them. I'd like to put a number from 1 to 1000 in their names. For example, if I have:

Alpha.doc
Beta.doc
Gamma.doc
...

I'd like to change all of them to the following:

1_Alpha.doc
2_Beta.doc
3_Gamma.doc
...

See what I mean. Because I have thousands of files, and can't and don't want to name them manually. So I'd like to know if a program or a tool or a plugin for nautilus, or a gnome coming to my place to type them for me, exists. =)

Thanks in advance to eveyone! 

Good luck!

---

### Post by sisco311 on 2008-04-08
gprename
```
sudo aptitude install gprename
```

---

### Post by Wobblybob on 2008-04-08
I use krename which is a KDE program but I use it on Gnome and should do what you want.

---

### Post by alejandro.mc on 2008-04-08
Thanks a lot to both. I tried the two programs and I'm using the Krename. Very nice GUI =)

Thanks a lot, good luck!

---

### Post by ghostdog74 on 2008-04-09
> **alejandro.mc said:**
> I'd like to know if a program to name files exist. What I mean is the following. I have lots of files in a folder, lots of them. I'd like to put a number from 1 to 1000 in their names. For example, if I have:

Alpha.doc
Beta.doc
Gamma.doc
...

I'd like to change all of them to the following:

1_Alpha.doc
2_Beta.doc
3_Gamma.doc
...

See what I mean. Because I have thousands of files, and can't and don't want to name them manually. So I'd like to know if a program or a tool or a plugin for nautilus, or a gnome coming to my place to type them for me, exists. =)

Thanks in advance to eveyone! 

Good luck!


do your own script. you are in linux after all!
```

ls -l | awk 'BEGIN{q="\047"}         
        /^-/{  newfile=NR"_"$NF
           cmd="mv "q $NF q " "q newfile q
           print cmd ; 
          # system(cmd)  #uncomment to use
        }'      

```

---

