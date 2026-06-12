---
title: "Split a file in two different parts but use it under one path"
date: 2015-08-13
forum: General Help
---

### Post by christos5 on 2015-08-13
I would like to split a large file (300GB), which is in my **home **directory under the **dev/sdb1** into two (or more) different parts and move them into two different disk drives. However, I would like my system to see the file as one.

To be more concrete I would like to split the file in two 150GB parts (or three 100GB, etc) and move those parts into different SSDs that I have. But, this file is used as an imput to a research project and I would like the system to see it as one. Additionally, I will need to specify its path in another file (a **.prototxt** file where I specify all the inputs to my program) and that is the reason why I want to have one path under which the system recognizes that (splitted) file. Unfortunately, the SSDs are not huge enough to hold the whole file.

Additionaly, when I run **df -h** the SSDs are show as:  
```

    Filesystem                           Mounted on
    cluster-name-1-int:/var/tmp/local    /import/cluster-name-1-int  
    cluster-name-2-int:/var/tmp/local    /import/cluster-name-2-int
```

My system is in a cluster but I do not think that this will make any difference because I have access from the `cluster-name-1` machine to the SSD on the others. Lastly, I do not have root access, so please tell me if your solution needs root privilages so that I would know and find a way to implement that solution.

EDIT: I provide as many information as I think would be useful. Use whatever you think might help towards a solution and any advice is welcome.

---

### Post by bab1 on 2015-08-13
> **christos5 said:**
> I would like to split a large file (300GB), which is in my **home **directory under the **dev/sdb1** into two (or more) different parts and move them into two different disk drives. However, I would like my system to see the file as one.

To be more concrete I would like to split the file in two 150GB parts (or three 100GB, etc) and move those parts into different SSDs that I have. But, this file is used as an imput to a research project and I would like the system to see it as one. Additionally, I will need to specify its path in another file (a **.prototxt** file where I specify all the inputs to my program) and that is the reason why I want to have one path under which the system recognizes that (splitted) file. Unfortunately, the SSDs are not huge enough to hold the whole file.

Additionaly, when I run **df -h** the SSDs are show as:  
```

    Filesystem                           Mounted on
    cluster-name-1-int:/var/tmp/local    /import/cluster-name-1-int  
    cluster-name-2-int:/var/tmp/local    /import/cluster-name-2-int
```

My system is ina cluster but I do not think that this will make any difference because I have access from the `cluster-name-1` machine to the SSD on the others.
I was with you all the way until you got to the cluster.  So let me just address the "splitting the file" part.  The best way to do that is to look at it from the other option.  That would be to combine all the SSD's into one volume.  To do that you can use LVM2 (Logical Volume Manager).  This would allow one large file across all 3 SSD's.
across 
The cluster adds a layer of complexity.  You might want to google "LVM2" and "cluster LVM" for more information.

In the end you do not want to spit the file up.  You do want the file to span multiple devices.

---

