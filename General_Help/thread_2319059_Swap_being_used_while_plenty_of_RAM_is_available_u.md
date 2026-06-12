---
title: "Swap being used while plenty of RAM is available using Ubuntu 14.04"
date: 2016-03-31
forum: General Help
---

### Post by c_xy on 2016-03-31
Hello,

Here are the specs of our system:

dell r730
10 Core
96 GB ram
28 TB storage space

We are running Ubuntu 14.04 LTS, and using ubuntu-mate installed as the DE. We are running high-end computations on this system, thus the need for many cores and plenty of memory. But, it seems the memory isn't best utilized if it access swap too much?

Here is the output from the command:

```
%free -m

             total       used       free     shared    buffers     cached
Mem:         96573      95994        579        197        654      79551
-/+ buffers/cache:      15789      80784
Swap:       183103        565     182538




```



Swap usage very slowly, but gradually increases over time. However, the free memory of 80784 is still not used. Rarely does the used portion exceed over 20000 MB.

The question becomes, why does our system use swap when we have plenty of RAM available?

Should we change the default value of swappiness (60) to a lower number? Or is there something else occurring?


Any input or suggestions would help a great deal.

Thank you.

c

---

### Post by grahammechanical on 2016-03-31
Figures can be misleading. Most of your used memory is cached memory. It is used memory in one sense but not used in another sense. Just set aside or allocated ready to be used.

It is similar with swap usage. Is the system actually using swap or just allocating a section of the available swap partition ready for use? Run the command with just the desktop loaded. Or install htop and run that and see what is actually happening in that system.

Regards.

---

### Post by Yellow Pasque on 2016-04-01
You could change swappiness to 10 if it really bothers you, but you'll probably still have some swap used (same with swappiness 0).
That's just the way virtual memory works. If the memory manager decides it definitely won't need the data again, it will swap it out.

---

### Post by SeijiSensei on 2016-04-01
I believe the kernel puts some small pieces of itself into swap if it is available even when there is plenty of physical memory as well.  Since so little swap is being used, why not turn it off entirely with "sudo swapoff" and see what happens.

---

### Post by SamInside on 2016-04-01
Well, I wouldn't recommend that.
Setting swappiness to a lower value is a better solution.

---

### Post by QDR06VV9 on 2016-04-01
I run with no swap at all(not recommended though) and never have had any kind of mishaps from that.
Just my 2 cents worth. But Yes Setting swappiness to a lower value is a better solution for most users.

---

### Post by SeijiSensei on 2016-04-01
> **SamInside said:**
> Well, I wouldn't recommend that.
Setting swappiness to a lower value is a better solution.

Why not?  There's no intrinsic requirement that the machine have swap unless it's a laptop and you use swap as storage for the memory image while hibernating.  On the OP's machine with **96 GB** of physical memory, there's no need for swap.

---

### Post by QDR06VV9 on 2016-04-01
> **SeijiSensei said:**
> Why not?  There's no intrinsic requirement that the machine have swap unless it's a laptop and you use swap as storage for the memory image while hibernating.  On the OP's machine with **96 GB** of physical memory, there's no need for swap.

+1

---

### Post by c_xy on 2016-04-01
Thank you everyone for the feedback and suggestions.

I ran the following command overnight:

```
vmstat -S M 1 > memory_log.txt  
```



Here is the selected output where swap was utilized:

```


pr    ocs    ------    #NAME?    mory---    -------    #NAME?    wap--    -----    io---- -system-- ------cpu-----
r    b    swpd    free     buff    cache   si  so    bi    bo   in   cs us sy id wa st
1    0    569    21307    2094    52975    0    0    3388    176 3096 5250  1  0 99  0  0
1    0    569    21349    2095    52941    0    0    720    8 2693 5730  0  0 99  0  0
1    1    569    21376    2096    52920    0    0    1780    0 2842 5574  1  0 99  0  0
1    1    569    21422    2099    52866    0    0    2556    52 3157 5573  1  0 99  0  0
1    0    569    21430    2102    52859    0    0    3096    28 2832 4357  0  0 99  0  0
1    0    569    21433    2105    52846    0    0    3548    164 3084 5083  0  0 99  0  0
2    0    569    21430    2106    52839    0    0    616    12 2998 5201  1  0 99  0  0
2    0    569    21421    2108    52839    0    0    2552    0 2990 4611  0  0 99  0  0
1    0    569    21407    2110    52839    0    0    1896    28 2874 4124  0  0 99  0  0
2    0    569    21413    2113    52833    0    0    3212    116 3090 3680  1  0 98  0  0
1    0    569    21408    2115    52829    0    0    3632    176 3114 4526  0  0 99  0  0
2    0    569    21408    2115    52822    0    0    544    0 2687 4759  0  0 99  0  0
1    0    569    21402    2117    52817    0    0    2428    0 3108 4763  1  0 99  0  0
1    0    569    21398    2117    52810    0    0    2024    780 2845 4083  0  0 99  0  0
1    1    569    21394    2118    52802    0    0    3448    28 2824 3230  0  0 99  0  0
2    0    569    21389    2121    52797    0    0    3052    176 3274 4831  1  0 99  0  0
2    0    582    21389    2121    52789    0    12    1336    12648 2903 4769  0  0 99  0  0
2    0    582    21384    2122    52784    0    0    2048    0 2880 4487  0  0 99  0  0
2    0    582    21376    2124    52780    0    0    4252    0 3459 4174  1  0 98  0  0
2    0    650    21373    2126    52777    0    68    2528    69648 3156 3792  0  0 99  0  0
1    0    670    21371    2128    52777    0    20    1780    20652 2922 4924  0  0 99  0  0
2    0    684    21368    2129    52777    0    14    1516    14728 2941 4476  1  0 99  0  0
1    0    690    21365    2131    52777    0    5    1520    5540 2802 4609  0  0 99  0  0
1    0    710    21359    2135    52777    0    20    4108    20944 3774 3868  0  0 99  0  0
2    0    722    21356    2137    52777    0    12    1864    12312 2817 3684  1  0 99  0  0
2    0    740    21353    2138    52777    0    18    1824    18744 2951 4564  0  0 99  0  0
1    0    769    21348    2142    52777    0    28    3968    29440 3511 4013  0  0 99  0  0
2    0    771    21361    2145    52777    0    1    2432    1828 3248 4025  1  0 99  0  0
1    0    771    21350    2147    52777    0    0    1900    8 2910 4950  0  0 99  0  0
1    0    771    21340    2148    52777    0    0    1684    60 2855 4892  0  0 99  0  0
1    0    771    21327    2150    52777    0    0    1540    256 2847 4751  1  0 99  0  0
1    0    771    21312    2154    52777    0    0    4240    0 3109 3655  0  0 99  1  0
2    0    773    21301    2156    52777    0    2    2732    2752 2721 3652  0  0 99  0  0
1    0    777    21296    2158    52777    0    3    1476    3336 3129 5031  1  1 99  0  0
1    1    777    21286    2160    52777    0    0    1656    32 2784 4856  0  0 99  0  0
1    0    777    21276    2161    52777    0    0    1556    160 2903 4517  0  0 99  0  0
1    1    777    21258    2165    52777    0    0    4232    0 3281 3463  1  0 98  1  0
1    1    777    21245    2168    52777    0    0    2788    0 2770 3610  0  0 99  0  0
1    0    779    21237    2169    52777    0    2    1304    2392 2684 4589  0  0 99  0  0
1    0    784    21234    2171    52777    0    5    1912    5172 3238 4686  1  0 98  0  0
1    0    786    21232    2173    52777    0    2    1552    2468 2984 4788  0  0 99  0  0
1    1    789    21226    2177    52777    0    2    4004    2788 3231 3872  0  0 99  1  0

.
.
.
1    0    789    21204    2211    52777    0    0    2568    0 2707 4000  0  0 99  0  0
2    0    796    21201    2213    52776    0    6    1704    6756 3007 4637  1  0 99  0  0
1    0    803    21198    2214    52776    0    7    1696    7496 2957 4780  0  0 99  0  0
1    0    809    21195    2216    52776    0    6    1552    6336 2905 4761  0  0 99  0  0
1    0    809    21190    2220    52776    0    0    4232    0 3269 3393  1  0 99  0  0
1    0    815    21185    2223    52777    0    6    3328    6336 2943 4203  0  0 99  0  0
2    0    820    21183    2224    52776    0    5    856    5180 2759 4899  0  0 99  0  0
1    0    824    21179    2226    52776    0    4    1688    4464 3109 4730  1  0 99  0  0
1    0    854    21175    2228    52777    0    30    2700    30868 3290 4657  0  0 99  0  0
1    0    867    21169    2231    52776    0    12    3160    13244 2933 3328  0  0 99  0  0
2    0    896    21167    2235    52777    0    28    3184    29276 3240 4428  1  0 98  0  0
2    0    900    21163    2236    52777    0    4    1020    4192 2813 5214  0  0 99  0  0
1    0    906    21158    2241    52777    0    6    5448    6436 3581 3899  0  0 99  0  0
1    0    908    21156    2241    52777    0    2    548    2164 2422 3194  1  0 99  0  0
1    0    908    21151    2244    52776    0    0    2700    0 3113 4723  0  0 99  0  0
1    0    912    21147    2247    52777    0    4    3396    4156 3147 4776  0  0 99  0  0
1    0    912    21138    2248    52777    0    0    648    168 3035 4706  1  0 99  0  0
2    0    912    21124    2252    52777    0    0    4244    144 3308 4041  0  0 99  0  0
1    0    912    21110    2255    52776    0    0    2520    24 2658 3364  0  0 99  0  0
2    0    912    21100    2256    52777    0    0    1604    20 2932 4533  1  0 99  0  0
2    0    912    21090    2258    52777    0    0    1672    0 2892 4730  0  0 99  0  0
1    0    917    21086    2259    52776    0    4    1552    4592 2896 4674  0  0 99  0  0
1    1    917    21074    2263    52777    0    0    4216    172 3383 3677  1  0 98  1  0
2    0    917    21062    2265    52776    0    0    1976    8 2567 3476  0  0 99  1  0
2    0    917    21055    2267    52776    0    0    2132    0 2902 4619  0  0 99  0  0
1    0    917    21070    2269    52776    0    0    1320    0 2847 4790  1  0 99  0  0
1    0    917    21063    2271    52776    0    0    1896    16 2803 4818  0  0 99  0  0
1    0    925    21060    2275    52777    0    8    4180    9540 3458 4208  0  0 99  1  0
1    1    930    21055    2276    52777    0    5    1216    5344 2481 3188  1  0 99  0  0
1    0    936    21050    2279    52776    0    6    2780    6244 3288 5139  0  0 99  0  0
1    0    943    21046    2280    52776    0    6    1428    6852 3181 4977  0  0 99  0  0
2    0    949    21043    2282    52776    0    5    1920    6096 3154 4805  1  0 99  0  0
2    0    955    21037    2286    52776    0    6    4376    6320 3513 4129  0  0 99  0  0
2    0    966    21034    2288    52776    0    10    2572    10728 2875 3735  0  0 99  0  0
1    0    976    21031    2290    52776    0    10    1680    10488 3036 4861  1  0 99  0  0
1    0    981    21025    2292    52776    0    6    2732    6260 3008 4952  0  0 99  0  0
1    0    984    21021    2293    52776    0    2    1588    2436 2894 4715  0  0 99  0  0
1    0    990    21018    2297    52776    0    6    4244    6392 3729 3694  1  0 98  0  0
1    0    990    21004    2300    52776    0    0    2180    28 2636 3713  0  0 99  0  0
1    0    994    20999    2302    52776    0    4    2400    4184 3098 5577  0  0 99  0  0
1    0    1000    20994    2303    52776    0    6    1888    6344 2925 5564  1  0 99  0  0
1    1    1000    20998    2304    52770    0    0    2544    8 2940 5362  0  0 99  0  0
2    0    1000    21105    2308    52651    0    0    4648    212 3274 5118  0  0 99  1  0
1    1    1000    21155    2309    52584    0    0    704    52 2439 3639  1  1 99  0  0
2    0    1000    21144    2312    52584    0    0    3528    16 3154 4874  0  0 99  0  0
1    0    1000    21135    2313    52584    0    0    824    0 2658 4889  0  0 99  0  0
1    0    999    21152    2315    52571    1    0    4156    8 3397 5831  1  0 99  0  0
1    1    999    21276    2319    52439    0    0    4060    244 3341 5651  0  0 99  1  0
1    0    999    21369    2320    52334    0    0    1532    132 2413 4527  0  0 99  1  0

```

As you can see, there moments where swapping out occurs, yet the cache stays ~52-53 GB.  What could cause the use of swap yet there is so much memory available?

The concern is the misuse of swap or some underlying issue with the system, DE, or some type of memory leak or cap.

I think I will try the suggestions of lowering the swappiness and see if that will help.

I will report my findings.

Again, any feedback or suggestions are appreciated.

Thanks again.

c

---

### Post by Yellow Pasque on 2016-04-02
> **c_xy said:**
> As you can see, there moments where swapping out occurs, yet the cache stays ~52-53 GB.  What could cause the use of swap yet there is so much memory available?

Once again, that's the way virtual memory works on Linux: [http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/](http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/)
The system is using swap for what it is intended for and it does not indicate any kind of problem. If it bothers you, turn swappiness down. I personally don't see a reason to turn swap off entirely unless you have a ton of RAM and are short on disk space, or your system is doing a lot of disk i/o for some reason.

---

