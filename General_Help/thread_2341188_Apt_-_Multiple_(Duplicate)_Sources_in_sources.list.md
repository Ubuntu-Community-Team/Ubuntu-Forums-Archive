---
title: "Apt - Multiple (Duplicate) Sources in sources.list"
date: 2016-10-25
forum: General Help
---

### Post by Alan5127 on 2016-10-25
Hi All,

I have the following 'error' coming up when I run apt (for example, if I run 'sudo apt-get upgrade'):

```
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
```


If I look at the two lines referenced, I see:

```
05:    deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties

10:    deb-src http://archive.ubuntu.com/ubuntu xenial main multiverse universe #Added by software-properties
```


I *think*, but am not 100% certain, that this has only been showing since I upgraded from Ubuntu 14.04 LTS to Ubuntu 16.04 LTS.  Having said that, it is possible it has been there for much longer, and I just didn't notice.


Question:

Am I right in thinking that I need to remove the duplicated items?  If so, I am guessing that if I removed 'xenial main' from line 5, then that would fix the issue (and not cause any problems)?


Thanks in advance,

Alan.

---

### Post by Bashing-om on 2016-10-25
Alan5127; Hey ..

Yes and no :
> 
Am I right in thinking that I need to remove the duplicated items? If so, I am guessing that if I removed 'xenial main' from line 5, then that would fix the issue (and not cause any problems)?

As line 5 also contains the directive for the restricted repo . Now that repo should also be in this sources list file somewhere . IF it is then yes DELETE the entire line 5 - after you have made a backup of the current file.
 More information at [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) - See 
 [https://wiki.ubuntu.com/RecommendedSources](https://wiki.ubuntu.com/RecommendedSources) for the recommended way to set up your repositories.

[INDENT][INDENT]how ya gonna call
[/INDENT][/INDENT]

---

### Post by Alan5127 on 2016-10-25
Hi Bashing-om,

> **Bashing-om said:**
> Alan5127; Hey ..

Yes and no :

As line 5 also contains the directive for the restricted repo . Now that repo should also be in this sources list file somewhere . IF it is then yes DELETE the entire line 5 - after you have made a backup of the current file.
 More information at [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) - See 
 [https://wiki.ubuntu.com/RecommendedSources](https://wiki.ubuntu.com/RecommendedSources) for the recommended way to set up your repositories.[INDENT][INDENT]how ya gonna call
[/INDENT]
[/INDENT]


If I only remove 'xenial main' from line 5, and leave everything else, so that it would then read:

```
deb-src http://archive.ubuntu.com/ubuntu restricted
```

would that not mean that the 'restricted' repository would still be in the sources.list?

Alternatively, I could delete 'xenial main' from line 10, and have that line as being:

```
deb-src http://archive.ubuntu.com/ubuntu multiverse universe
```

Would that be better?

Maybe safer if I post my entire sources.list:

```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu precise partner


```


Thanks,

Alan.

---

### Post by Bashing-om on 2016-10-25
Alan5127; Yepper .

Here is what you have for the restricted repo as is now:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Good as is
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted #Good as is
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse #good as is
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted #good as is

Looks good to me .. That should fly ,, I see no fault nor any duplication, now , 

I have not. however, looked at the src repos. As to this time no issue there has presented it's self .

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by Alan5127 on 2016-10-25
Hi Bashing-om,

Thanks again for your help here.

> **Bashing-om said:**
> Alan5127; Yepper .

Here is what you have for the restricted repo as is now:

Looks good to me .. That should fly ,, I see no fault nor any duplication, now , 

I have not. however, looked at the src repos. As to this time no issue there has presented it's self .[INDENT][INDENT]look'n good
[/INDENT]
[/INDENT]



If it all looks okay, why might 'apt' be reporting the 'errors' on lines 5 and 10?

Thanks,

Alan.

---

### Post by Bashing-om on 2016-10-25
Alan5127; Allan ..

In your last paste line 10 was different than what the package manager reported . I did "assume" you had made the edit.
Let's try this again:
```

cat -n /etc/apt/sources.list

```
to get some numbering .

I did look twice, and I did not see a duplication in the /etc/apt/sources.list file .. will be glad to look again .

[INDENT][INDENT]check 3 times
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alan5127 on 2016-10-25
Hi Bashing-om,

> **Bashing-om said:**
> Alan5127; Allan ..

In your last paste line 10 was different than what the package manager reported . I did "assume" you had made the edit.
Let's try this again:
```

cat -n /etc/apt/sources.list

```
to get some numbering .

I did look twice, and I did not see a duplication in the /etc/apt/sources.list file .. will be glad to look again .[INDENT][INDENT]check 3 times[INDENT][INDENT][INDENT]act once
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Sorry about that - I should have checked and reconciled what I see in gedit, and what I pasted above.  I did this command:

```
cat -n /etc/apt/sources.list > sources-list.txt
```

and have attached the file - is that okay?

[ATTACH]271791[/ATTACH]

This is (hopefully) the same thing:

```

     1    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted
     5    deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties
     6    
     7    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8    # newer versions of the distribution.
     9    deb http://archive.ubuntu.com/ubuntu xenial main restricted
    10    deb-src http://archive.ubuntu.com/ubuntu xenial main multiverse universe #Added by software-properties
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
    15    deb-src http://archive.ubuntu.com/ubuntu xenial-updates restricted main multiverse universe #Added by software-properties
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18    ## team. Also, please note that software in universe WILL NOT receive any
    19    ## review or updates from the Ubuntu security team.
    20    deb http://archive.ubuntu.com/ubuntu xenial universe
    21    deb http://archive.ubuntu.com/ubuntu xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb http://archive.ubuntu.com/ubuntu xenial multiverse
    29    deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
    37    deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse #Added by software-properties
    38    
    39    deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
    40    deb-src http://archive.ubuntu.com/ubuntu xenial-security restricted main multiverse universe #Added by software-properties
    41    deb http://archive.ubuntu.com/ubuntu xenial-security universe
    42    deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
    43    
    44    ## Uncomment the following two lines to add software from Canonical's
    45    ## 'partner' repository.
    46    ## This software is not part of Ubuntu, but is offered by Canonical and the
    47    ## respective vendors as a service to Ubuntu users.
    48    deb http://archive.canonical.com/ubuntu xenial partner
    49    # deb-src http://archive.canonical.com/ubuntu precise partner
    50    


```


Thanks,

Alan.

---

### Post by ian-weisser on 2016-10-25
There's no magic here. Each line is just text that passes four pieces of information :
deb/deb-src, url, dist, repository
...plus lots of comments
```
Example: deb      http://archive.ubuntu.com/ubuntu          xenial            main
Example: deb-src  http://archive.ubuntu.com/ubuntu          xenial-security   universe
```



Each line may have only one dist, but may have multiple repositories within that dist.
```
Example: deb        http://archive.ubuntu.com/ubuntu          xenial                main restricted universe multiverse
```



The following lines have some duplication. Can you spot the duplication? [Answer: Lines 2 and 3 can be safely deleted]
```
1) deb        http://archive.ubuntu.com/ubuntu          xenial                main restricted universe multiverse
2) deb        http://archive.ubuntu.com/ubuntu          xenial                main restricted
3) deb        http://archive.ubuntu.com/ubuntu          xenial                universe multiverse
```

You can safely delete (or keep) comments (##). They are merely comments.
When in doubt, comment out a line instead of deleting it. Make notes - you won't remember exactly what you did, nor why.
Example:
```
deb        http://archive.ubuntu.com/ubuntu          xenial                main restricted universe multiverse
## deb        http://archive.ubuntu.com/ubuntu          xenial                main restricted        # Duplicate of line 1 on October 25
## deb        http://archive.ubuntu.com/ubuntu          xenial                universe multiverse    # Duplicate of Line 1 on October 25
```


That's really all you need to know to de-duplicate your sources.list.


Here's an example of your entire list fully de-duplicated:
```
deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu xenial partner

```

---

### Post by Alan5127 on 2016-10-25
Hi Guys,

Just wanted to say 'thank you' so much.

Not only is the issue now gone, but I have learnt much today, including 'cat -n'!

Very much appreciated.

Alan.

---

### Post by Bashing-om on 2016-10-25
Alan5127; Ouch !

You can slap me now ..!! .. Me and my tunnel vision ! We are looking at 'src' !!

And although ian-weisser has beat me to iut .. I am going to show the results of my work !

/// OK this is just my scribbling - you may ignore it and get to the gist at the bottom.
------------------------------------------------------------------------------------------
" 05:    [color=red]deb-src [/color]http://archive.ubuntu.com "
 5    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Added by software-properties
10:    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main multiverse universe #Added by software-properties

and line 5 is the culprit .

Line 5 should be " #(bdq)deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) raring main restricted " 
5    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Added by software-properties //duplicated in line 10
Line 10 should be " #(bdq)deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) raring main restricted "
10    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main multiverse universe #Added by software-properties

In line 5 is main that is already taken care of in line 10.
multiverse  src - is taken care of in line //NO ! it is not ..make up 
universe src is taken care of in line // No ! it is not make up 
-----------------------------------------------

Here is the gist:

Remove line 5 

and then edit line 10 to be similar :
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) raring main restricted

Add in the Multiverse section these 2 lines similar :
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) raring multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) raring-updates multiverse

So that you now have:
Line 10 becomes:
```

deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #  multiverse universe moved back where they belong

```

And make the multiverse stanza by adding back in the multiverse repos src for xenial and xenial-updates
```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates multiverse

```

The same treatment for universe section:
```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial universe
deb-src http://archive.ubuntu.com/ubuntu xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
deb-src http://archive.ubuntu.com/ubuntu xenial-updates universe

```

Wow .. finally I see the light and we can make it right .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Alan5127 on 2016-10-25
Hi Bashing-om,

Thanks again - I very much appreciate your assistance, and as I said, I now have a much better understanding of what the sources.list file is actually doing.

\\:D/

Alan.

---

### Post by Bashing-om on 2016-10-25
Alan5127; Hey .

Appreciate the thanks - even though it took me a while to get past my tunnel vision .

all in the process of learning :)

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

