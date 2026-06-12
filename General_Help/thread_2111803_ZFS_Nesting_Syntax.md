---
title: "ZFS Nesting Syntax"
date: 2013-02-03
forum: General Help
---

### Post by Alvinator9000 on 2013-02-03
Okay here's one for you, I can't find ANY documentation ANYWHERE for using brackets (parentheses) to describe what drives to select when creating a zpool.  For example, I am in a VERY sticky situation with money and physical drive constraints.  I have figured out a method to make the best use of what I have but it results in a pretty unorthodox (yet completely redundant and failproof [1 drive] way) of getting it all to work AND maximize the use of my motherboard's ports to make it completly expandable in the future. I am basically creating a single-vdev pool containing a bunch of different raid levels, mirrors, and stripes.

I've looked in here too: [http://docs.oracle.com/cd/E19253-01/816-5166/zfs-1m/index.html](http://docs.oracle.com/cd/E19253-01/816-5166/zfs-1m/index.html)

HOWEVER, this is how I have to do it, because of hardware constraints.
If you were to imagine how to use the zpool create, this is how it would look USING BRACKETS.  BUT THERE IS NO MENTION OF HOW TO USE BRACKETS (or that they even can be used) PROPERLY in any zfs documentation.  Basically either brackets, commas, &&s, etc, anything that would give me the desired affect.  

zpool create mycoolpool RAIDZ1 ((mirror A B) (mirror C D) (mirror E F) (G) (stripe H, I) (stripe J, K, L) (M))

Yes I have 7 1TB 'blocks' or 'chunks' in a RAIDZ1, each consisting of different configurations.

You see, if I were to do this without the brackets, it would create this mess:
zpool create mycoolpool RAIDZ1 mirror a b mirror c d mirror e f g h i j k l m
^^Basically you see here that I would end up with a RAIDZ1 across 3 mirrors, the third of which consisting of a redundancy level such that 8 drives could fail... not what I want.

And yes, I have indeed seen all the warnings and read countless people say "you shouldn't" but NEVER have I seen anyone deny that it could be done and NEVER have I seen anyone actually answer on HOW to do it.

I've made up my mind that this is the method and approach that I need to take so please heed your warnings as much as you can as they will be said in vain.

Thank you very much in advance for a response!!!

As you can guess, A through F are 1TB partitions on two 3TB drives, whilst G and M are 1TB drives themselves, and finally H and I are each 500G, and JKL are 500, 320, and 200.
Basically combining them for a total of 5TB of EXPANDABLE BY SWAP data space.

As a final note, I am intending to use a ZIL and cache, but I'm not worrying about that atm as I know how to add that later.


And for a visual, it would look something like this (NOTE, I have NOT done this, this is a visual of what way I want my drives configured):
# zpool status mycoolpool
pool: pool
state: ONLINE
scan: none requested 
config:

NAME STATE READ WRITE CKSUM
Mycoolpool
...RAIDZ1-0
....Mirror-0
.....A
.....B
....Mirror-1
.....C
.....D
....Mirror-3
.....E
.....F
....G
.....H
.....I
....M
.....J
.....K
.....L

^^Minus all the STATE READ WRITE CKSUM data, that's basically what I'm wanting/trying to do :)

I'm using UbuntuStudio 12.10, but this pretty much applies to all Ubuntu varients.  I'm also a noob to both Ubuntu and ZFS as I've only been on it for a week.
Also, if you (a mod) feels this should be better posted under another category please feel free to do so :)  


THANKS AND CHEERS!!

---

### Post by Alvinator9000 on 2013-02-03
Reserved, for answer.

---

