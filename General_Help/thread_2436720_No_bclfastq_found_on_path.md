---
title: "No bclfastq found on path"
date: 2020-02-11
forum: General Help
---

### Post by yueli7 on 2020-02-11
Hello,

I tried to run bcl2fastq, but it said ```
[error] No bcl2fastq found on path
``` 



  Thanks in advance for any help and suggestion!


  Best,


  Yue

```

li@li-HP-Pavilion-Desktop-590-p0xxx:~$ bcl2fastq --help
BCL to FASTQ file converter
bcl2fastq v2.20.0.422
Copyright (c) 2007-2017 Illumina, Inc.

Usage:
  bcl2fastq [options]






li@li-HP-Pavilion-Desktop-590-p0xxx:~$ cellranger mkfastq --id=tiny-bcl  --run=cellranger-tiny-bcl-1.2.0  --csv=cellranger-tiny-bcl-simple-1.2.0.csv
/home/li/opt/cellranger-3.1.0/cellranger-cs/3.1.0/bin
cellranger mkfastq (3.1.0)
Copyright (c) 2019 10x Genomics, Inc.  All rights reserved.
-------------------------------------------------------------------------------

Martian Runtime - '3.1.0-v3.2.3'
2020-02-11 20:16:39 [jobmngr] WARNING: configured to use 21GB of local memory, but only 19.0GB is currently available.
2020-02-11 20:16:39 [runtime] Reattaching in local mode.
Serving UI at http://li-HP-Pavilion-Desktop-590-p0xxx:39889?auth=ECJkP0tXgwBHrQwqlcZBN1UtFck0Of4F83ahq6jb0OU

2020-02-11 20:16:39 [runtime] (reset-partial)   ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT.fork0.chnk0
2020-02-11 20:16:39 [runtime] (reset-partial)   ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT_LOCAL.fork0.chnk0
2020-02-11 20:16:39 [runtime] Found orphaned local stage: ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT
2020-02-11 20:16:39 [runtime] Found orphaned local stage: ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT_LOCAL

[error] No bcl2fastq found on path. demux requires bcl2fastq v2.17 or greater for RTA version: 1.18.66.4
```

---

### Post by Bashing-om on 2020-02-11
yueli7; Hello

As we have:
> 
[error] No bcl2fastq found on path


Let's look -
What returns:
```

which bcl2fastq
echo $PATH
sudo sh -c 'echo $PATH'

```
and see here what we have to work with.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by yueli7 on 2020-02-11
Hello, George,

Thank you so much for your replying!

Thank you again!

Best,


Yue

li@li-HP-Pavilion-Desktop-590-p0xxx:~$ which bcl2fastq
./usr/local/bin//bcl2fastq

li@li-HP-Pavilion-Desktop-590-p0xxx:~$ echo $PATH
~/opt/cellranger-3.1.0:./usr/local/bin/:/home/li/miniconda3/bin:/home/li/.aspera/connect/bin:/home/li/.local/bin:/usr/local/bin:/usr/bin:/bin:/usr/games:/snap/bin

li@li-HP-Pavilion-Desktop-590-p0xxx:~$ sudo sh -c 'echo $PATH'
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin

---

### Post by Bashing-om on 2020-02-11
yueli7; Hey :)

Looks to me as a syntax error in the path assignment.
> 
./usr/local/bin//


The trailing backslash - Or maybe the './' ,that directs "this directory right here".

my user path:
> 
sysop@x1804mini:~$ echo $PATH
/home/sysop/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin



[INDENT]computers !
[INDENT][INDENT]so literal
[/INDENT][/INDENT][/INDENT]

---

### Post by yueli7 on 2020-02-12
Hello, Bashing-om,

Thank you so much for your great help!

You are totally correct! I know I have something wrong, but I can not figure it out.


Thank you in advance for your great help!

Best,

Yue


li@li-HP-Pavilion-Desktop-590-p0xxx:~$ export PATH="/usr/local/bin:$PATH"
li@li-HP-Pavilion-Desktop-590-p0xxx:~$ bcl2fastq --h
bcl2fastq: command not found

li@li-HP-Pavilion-Desktop-590-p0xxx:~$ export PATH="./usr/local/bin:$PATH"
li@li-HP-Pavilion-Desktop-590-p0xxx:~$ bcl2fastq --h
BCL to FASTQ file converter
bcl2fastq v2.20.0.422
Copyright (c) 2007-2017 Illumina, Inc.

Usage:
      bcl2fastq [options]



li@li-HP-Pavilion-Desktop-590-p0xxx:~$ which bcl2fastq
./usr/local/bin/bcl2fastq



 [COLOR=black][FONT=Calibri]




[/FONT][/COLOR]

---

### Post by Bashing-om on 2020-02-12
yueli7; Well -

If it is your intent that bcl2fastq reside in a hidden directory, then your PATH looks correct.

[INDENT]should workie[/INDENT]

---

### Post by bazok100 on 2020-02-12
Hi,
I have similar issue but when I typed the below 
commands
which [COLOR=#417394]bcl2fastq[/COLOR]
echo $PATH
sudo sh -c 'echo $PATH'

I got several directories

---

### Post by Bashing-om on 2020-02-12
bazok100; Hello Welcome also to the forum :)

> 
I have similar issue


Unless it is exact as the original poster - and we can not tell as you do not provide the command's outputs - you are advised to start your own thread on your issue.

issues are like dead men >>

[INDENT][INDENT]one to the box
[/INDENT][/INDENT]

---

### Post by yueli7 on 2020-02-12
[COLOR=black][FONT=Calibri]Hello Bashing-om,

[COLOR=black][FONT=Calibri] Thank you so much for your suggestion![/FONT][/COLOR]
 
 [COLOR=black][FONT=Calibri] I followed this link to install bcl2fastq:[/FONT][/COLOR]
 
 [COLOR=black][FONT=Calibri] [https://kb.10xgenomics.com/hc/en-us/articles/360001618231-How-to-troubleshoot-installing-bcl2fastq-](https://kb.10xgenomics.com/hc/en-us/articles/360001618231-How-to-troubleshoot-installing-bcl2fastq-)
 [/FONT][/COLOR]
 [COLOR=black][FONT=Calibri]> [FONT=consolas]l[/FONT][FONT=consolas]i@[/FONT][FONT=consolas]li-HP-Pavilion-Desktop-590-p0xxx:~$ which bcl2fastq[/FONT]
  [FONT=consolas]&#8203;[/FONT][FONT=consolas]&#8203;.[/FONT][FONT=consolas]/usr/local/bin/bcl2fastq[/FONT]
 
 In this issue: 
 [/FONT][/COLOR]
 [COLOR=black][FONT=Calibri][https://kb.10xgenomics.com/hc/en-us/articles/360036273051-How-do-I-fix-the-mkfastq-error-No-bcl2fastq-found-on-path-](https://kb.10xgenomics.com/hc/en-us/articles/360036273051-How-do-I-fix-the-mkfastq-error-No-bcl2fastq-found-on-path-)
 
 It said: 
 [/FONT][/COLOR]
 [COLOR=black][FONT=Calibri] > [FONT=consolas]which bcl2fastq[/FONT]
[FONT=consolas]/usr/local/bin/bcl2fastq[/FONT] 

There is a>  "[COLOR=#C82613]&#8203;.[/COLOR]" before>  [FONT=consolas]/[/FONT][FONT=consolas]us[/FONT][FONT=consolas]r/local/bcl2fastq[/FONT] in the path of my installation.[/FONT][/COLOR]
 
 [COLOR=black][FONT=Calibri] The cellranger in the following path: 

 [/FONT][/COLOR][/FONT][/COLOR]> [COLOR=black][FONT=Calibri][FONT=consolas]/home/li/opt/cellranger-3.1.0/cellranger-cs/3.1.0/bin [/FONT][/FONT][/COLOR][COLOR=black][FONT=Calibri]
 [COLOR=black][FONT=Calibri]Is that possible to make a soft link>  [FONT=consolas]man ln[/FONT] from there to a directory on [/FONT][/COLOR][/FONT][/COLOR][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri]> [FONT=consolas]cellranger[/FONT][FONT=consolas]'s [/FONT][FONT=consolas]$PATH[/FONT]?.[/FONT][/COLOR][/FONT][/COLOR] 
 [COLOR=black][FONT=Calibri]I think: the path [/FONT][/COLOR]> [COLOR=black][FONT=Calibri]/home/li/opt/[/FONT][/COLOR][COLOR=black][FONT=Calibri] is not able to access the programs in[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][FONT=consolas] [/FONT][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri][FONT=consolas][COLOR=black][FONT=Calibri][COLOR=black][FONT=Calibri]> [FONT=consolas]cellranger[/FONT][FONT=consolas]'s [/FONT][FONT=consolas]$PATH[/FONT]?[/FONT][/COLOR][/FONT][/COLOR][/FONT].[/FONT][/COLOR]
 

 [/FONT][/COLOR][COLOR=black][FONT=Calibri]Really appreciated any of your help and suggestions![/FONT][/COLOR]
 
 [COLOR=black][FONT=Calibri] Best,

Yue[/FONT][/COLOR]
  

> li@li-HP-Pavilion-Desktop-590-p0xxx:~$ cellranger mkfastq  --id=tiny-bcl   --run=cellranger-tiny-bcl-1.2.0    --csv=cellranger-tiny-bcl-simple-1.2.0.csv
  /home/li/opt/cellranger-3.1.0/cellranger-cs/3.1.0/bin
 
 cellranger mkfastq (3.1.0)
 
 Copyright (c) 2019 10x Genomics, Inc.  All rights reserved.
 
 -------------------------------------------------------------------------------
 
 
 
 Martian Runtime - '3.1.0-v3.2.3'
 
 2020-02-12 12:32:49 [jobmngr] WARNING: configured to use 21GB of local memory, but only 15.0GB is currently available.
 
 2020-02-12 12:32:49 [runtime] Reattaching in local mode.
 
 Serving UI at [http://li-HP-Pavilion-Desktop-590-p0xxx:46785?auth=IEt7cry3Y_IG5nnVovKfU2lbsc1s8wQK6B5bVu8kKxE](http://li-HP-Pavilion-Desktop-590-p0xxx:46785?auth=IEt7cry3Y_IG5nnVovKfU2lbsc1s8wQK6B5bVu8kKxE)
 
 
 
 2020-02-12 12:32:49 [runtime] (reset-partial)   ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT.fork0.chnk0
 
 2020-02-12 12:32:49 [runtime] (reset-partial)   ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT_LOCAL.fork0.chnk0
 
 2020-02-12 12:32:49 [runtime] Found orphaned local stage: ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT_LOCAL
 
 2020-02-12 12:32:49 [runtime] Found orphaned local stage: ID.tiny-bcl.MAKE_FASTQS_CS.MAKE_FASTQS.MAKE_FASTQS_PREFLIGHT
 
 
 
 [error] No bcl2fastq found on path. demux requires bcl2fastq v2.17 or greater for RTA version: 1.18.66.4
 
 [/FONT][/COLOR]> 
[COLOR=black][FONT=Calibri]
 
 [/FONT][/COLOR]

---

### Post by Bashing-om on 2020-02-12
yueli7; Hummm ...

Be aware that  &#8203;&#8203;./usr/local/bin/bcl2fastq is an UN orthodox location for an executable, though fine if that is what you want -
now ya got to tell cellranger where to find bcl2fastq.

Else move bcl2fastq to a place cellranger knows about.
As I do not have either installed I can not look and see what moving will entail nor how to configure cellranger.

[INDENT]A know-it-all I am not
[/INDENT]

---

### Post by Holger_Gehrke on 2020-02-12
From reading the discussion up to this point I think you made a mistake while installing the bcl2fastq program. It's probably intended to go into /usr/local/bin and you left off the '/' at the beginning or put a '.' in front of it, thereby turning an absolute path into a relative one. Having './usr/local/bin/' in the PATH is very close to useless - it means 'look for programs in bin inside local inside usr inside the current working directory'. This breaks whenever the working directory is not the one from which you installed. The program calling bcl2fastq probably changes the working directory and then can't find bcl2fastq. As a quick fix you could try putting '/home/li/usr/local/bin/' into the PATH instead of './usr/local/bin/'.

Holger

---

### Post by gsahli on 2020-02-12
I think you missed his explanation about the "." That means that the /usr/local/bin/bcl2fastq is installed in a folder in your home folder (the present working directory when you gave the command which). you could move it to the real /usr/local/bin, and then it will be in your PATH.

Oh, Holger_Gehrke I guess you were typing at the same time.

---

### Post by yueli7 on 2020-02-12
Hello, bazok100,

I have already figured it out.

I willing to help you if you need.

Best,

yue

---

### Post by wildmanne39 on 2020-02-12
> **yueli7 said:**
> Hello, bazok100,

I have already figured it out.

I willing to help you if you need.

Best,

yue
Hello, please post the answer for the benefit of other searchers looking for the solution, then use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by yueli7 on 2020-02-13
The main issue is use > ln to make> bcl2fastq soft link to>  cellranger PATH.

> li@-Desktop-590-p0xxx:~/opt/cellranger-3.1.0/cellranger-cs/3.1.0/bin$ ln -s ./usr/local/bin/bcl2fastq bcl2fastq
   

---

