---
title: "Statistical software and Linux....."
date: 2007-12-01
forum: General Help
---

### Post by stanton816 on 2007-12-01
hello all-
i'm an economist and would like to use eviews, sas and stata with ubuntu.  my big problem is that i have most of my software cds are in a windows format. i think stata is the only one i can use with linux, if i buy a new cd.  anyway, if anyone has any advice, or experience, i'd love to hear it.  
thanks as always. :guitar:

---

### Post by -grubby on 2007-12-01
you could try them in wine . install wine by opening a terminal in applications>accessories>terminal and type:

```
sudo apt-get install wine
```

---

### Post by SeanHodges on 2007-12-01
Personally I've only had experience with R ([http://www.r-project.org/](http://www.r-project.org/)). It worked great for me, but as I haven't used anything else in the past I couldn't tell you if its what you're looking for.

If you want a commercial solution, you'll probably end up paying for a Linux version. Running the Windows version inside VMWare might be an option if you've already got a copy of SAS for Windows.

Take a look at a similar thread here: [http://ubuntuforums.org/showthread.php?t=93493](http://ubuntuforums.org/showthread.php?t=93493)

Theres an entry in the Wiki for this topic: [https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience) (scroll down to "Statistics")


Regards,

Sean

---

### Post by stanton816 on 2007-12-02
thanks, everyone.  i've managed to get stata 10 to work with wine.  i'm thinking about trying R, if i can figure out how to download it.

---

### Post by SeanHodges on 2007-12-03
Glad to hear you got things working.

If you want to try R, you can install it from the repository:

```
sudo apt-get install r-base
```

there is also a graphical front-end available called rkward (some screenshots at [http://rkward.sourceforge.net/?content=screenshots](http://rkward.sourceforge.net/?content=screenshots))

```
sudo apt-get install rkward
```

---

### Post by kstella on 2007-12-03
Is this program similar to SPSS?

---

### Post by stanton816 on 2007-12-04
i'm going to try to get r-base.  is there a lot of installation work to get it going?  my windows just keeled over and died last night, so, after trying fedora and hating it, i've decided ubuntu is the best of the three adn the only one i'm keeping.  
my stata 10 stopped working the second time i tried it.  i guess, if i can't figure out the install for r i'll be stuck working at the office.  :(

---

### Post by SeanHodges on 2007-12-04
For those of you asking if R is like SPSS/SAS, or any kind of comparison between them, I'm afraid I'm not going to be of much help. I'm a novice at R, and have never used SPSS or anything else for that matter.

I recommending checking out this site for details about the software:

[http://www.statmethods.net/index.html](http://www.statmethods.net/index.html)

It covers the general features of R and is easier on the eyes than the official R-Project website (but I recommend checking that out too - especially for the manual as a reference).

I've attached a comparison sheet I found for SAS/SPSS users. It turned out to be huge so I had to zip it up. You can also find it here: [http://oit.utk.edu/scc/RforSAS&SPSSproducts.pdf](http://oit.utk.edu/scc/RforSAS&SPSSproducts.pdf)

As for installation, just install the package I mentioned earlier, and to run from the command-line type:

```
R<enter>
```

I recommend you install the graphical UI "RKWard" to begin with as well. You might find it a bit limiting if you want to do some really advanced stuff, but it will get you started fairly easily. It also displays the commands it is using to achieve the output, so you can modify it and learn how it all works. Once you've installed it, you can run it from the command-line:

```
rkward<enter>
```

Unfortunately, neither of these packages set up launchers in the Applications menu, you can do this easily for rkward yourself (right-click on the menu in the panel) or just add a launcher on the desktop (right-click on the desktop).

Hope that's enough to get you started; if you have any questions about using R itself its probably best to start a new thread.

---

