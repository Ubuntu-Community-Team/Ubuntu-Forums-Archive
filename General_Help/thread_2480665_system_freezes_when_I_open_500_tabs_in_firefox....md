---
title: "system freezes when I open 500 tabs in firefox..."
date: 2022-11-05
forum: General Help
---

### Post by bitrat2 on 2022-11-05
Hi,

I have a bit of ADHD and tend to open 500+ firefox tabs and never close them.  At the same time I commonly have a couple of other browsers open, as well as GIMP, Inkscape, meld, Jupyter, R-Studio, etc, then I run clang and my system locks up.  :(

Sometimes I can open another terminal (or even log in from another machine) and kill firefox, but usually the whole system has ground to a virtually complete halt.

As an experiment, I tried running firefox in a sandbox...
```
systemd-run --user --no-block -p MemoryHigh=1G firefox
```
... but I see that 'firefox' is itself a rather involved script, and I probably should be calling firefox-bin directly.  I may explore this further, but...

I wrote this script a while ago, as a first cut at monitoring memory
```
USED=`free | grep Mem | awk '{print "scale=5; " $3 ".0/" $2 ".0 * 100"  }' | bc`
echo "In use:" $USED "%"
[[ -z "$1" ]] || (BY=`ps -o pid,user,%mem,command ax | sort -b -k3 -r | grep -i "$1" | awk '{print $3" + "}' | tr '\n' ' ' > ~/junk && echo '0' >> ~/junk && cat ~/junk | bc` && echo "By $1:" $BY "%")
```
It occurred to me that I could run a cron script every minute or so and pop up a system modal warning dialog if resources are critically low.

I know how to monitor resources manually, but I need something in the background.

Any ideas?

---

### Post by dragonfly41 on 2022-11-05
Having so many tabs open is a waste of memory.  Use Stacer to see the amount of memory for each open tab.
I use extensions in Chrome and Brave .. but not Firefox.
these useful extensions are:
Tab-Sidebar
OneTab
Group Tabs
Session Buddy

and remember that you can use multiple Firefox profiles so you can assign different tabs to different profiles.

You can also try saving your tabs in Zotero for better management.

---

### Post by bitrat2 on 2022-11-05
> **dragonfly41 said:**
> Having so many tabs open is a waste of memory.  Use Stacer to see the amount of memory for each open tab.
I use extensions in Chrome and Brave .. but not Firefox.
these useful extensions are:
Tab-Sidebar
OneTab
Group Tabs
Session Buddy

and remember that you can use multiple Firefox profiles so you can assign different tabs to different profiles.

You can also try saving your tabs in Zotero for better management.

Hi dragonfly41, 

500 was a bit of an exaggeration really, but if you know anyone with ADHD you'll know what I mean.  

I'm not much good with tab manager extensions.  I forget to use them and forget how to use them and forget how I've decided to use them, and so on.

But that's a good idea to use different profiles.  I have considered it, but it's probably time I tried it.

What I don't understand is why the system can't just lock up firefox, rather than bring down the whole sh'mozzle.  Sometimes I pine for the MS Windows WM event loop...

bitrat

---

### Post by MAFoElffen on 2022-11-05
> **bitrat2 said:**
> Hi dragonfly41, 

500 was a bit of an exaggeration really, ...

My wife just opens more and more tabs, without closing anything... The struggle is real. LOL.

I always thought it might be easier to make sure your have plenty of room in swap, and pop a warning when it starts paging.

---

### Post by bitrat2 on 2022-11-05
> **MAFoElffen said:**
> My wife just opens more and more tabs, without closing anything... The struggle is real. LOL.

It's so good to be understood!  :D

> **MAFoElffen said:**
> I always thought it might be easier to make sure your have plenty of  room in swap, and pop a warning when it starts paging.

Yes, that's a plan!  Any ideas how I could implement this to put up a warning dialog...

I've got 2G of swap...  

I think I'll have a play with this:

**[FONT=courier new]ps -eo min_flt,maj_flt,cmd,args,uid,gid[/FONT]**

Something like...

[FONT=courier new]**TOTAL=`ps -eo maj_flt,cmd | grep firefox | awk '{print $1}' | tr '\n' '_' | sed 's/_/ + /g'` && echo "$TOTAL 0" | bc**[/FONT]

---

### Post by #&amp;thj^% on 2022-11-05
> **bitrat2 said:**
> Any ideas how I could implement this to put up a warning dialog...

I've got 2G of swap...  

When my Wife was allowed to touch any of my computer's I used something like this: (She has her own stuff)
```
#!/bin/bash

free_mem="$(free | grep 'Mem:' | awk '{print $7}')"
used_swap="$(free | grep 'Swap:' | awk '{print $3}')"

echo -e "Free memory:\t$free_mem kB ($((free_mem / 1024)) MiB)\nUsed swap:\t$used_swap kB ($((used_swap / 1024)) MiB)"
if [[ $used_swap -eq 0 ]]; then
    echo** "Congratulations! No swap is in use."**
elif [[ $used_swap -lt $free_mem ]]; then
    echo "Freeing swap..."
    sudo swapoff -a
    sudo swapon -a
else
    echo **"Not enough free memory. Exiting."**
    exit 1
fi

```

---

### Post by QIII on 2022-11-05
I can't tell you how to deal with ADHD.  I am not a medical professional, nor is anyone here free to provide medical advice anonymously.  But I am aware that telling you not to open some large number of tabs is not helpful.  If it were, you would already have a handle on it.

I am not convinced that anything that dictates how you are to use your OS other than you paying attention to what you are doing and being prudent is a good thing.  What Microsoft does with its hand-holding OS that dictates user experience is of no consequence here.

However, in your case where you are sometimes robbed of the ability to be attentive and prudent by no fault of your own, I believe that earlyoom is still available, but I'm not sure how active development is.  [This]("https://manpages.ubuntu.com/manpages/jammy/man1/earlyoom.1.html") appears to be current with Jammy.

I don't remember that there is any graphical indicator presented.  I think it just kills whatever happens to be the largest memory consumer when some threshold is reached.  Your browser would just go poof and you'd have to restart it.

(Folks, I'm not sure if a manual terminal-based solution is necessarily helpful when an unwanted health issue makes things difficult enough.  An unattended process, preferably one with a GUI pop-up in the face, would be a better solution to offer.)

---

### Post by dragonfly41 on 2022-11-05
[COLOR=#000000]> but if you know anyone with ADHD you'll know what I mean.
Actually I do. I understand.

I have written in other posts that I use automation scripts to streamline workflows. 
I can see this being another candidate. A helper script to routinely scan tabs, and tidy up drawing on proven extensions.

A simple tool I use is Actiona and this can be used for most automation profiles. After installing extensions the helper script could auto click on buttons in top bar of browser. You can capture coordinates of target buttons by simply:

- maximise browser window
- identify target locations of extensions buttons by running this command
      watch [/COLOR]xdotool getmouselocation[COLOR=#000000]
- use these coordinates to move cursor and auto click 

Read the Actiona tutorials.

You can also build in Actiona a library of commands to open popular browser links through the command line:

[/COLOR]xdg-open [https://ubuntuforums.org/showthread.php?t=2480665](https://ubuntuforums.org/showthread.php?t=2480665)

[COLOR=#000000]Or you could access a database of URL's.

Many options to ease the workflow.
[/COLOR]

---

### Post by bitrat2 on 2022-11-05
> **QIII said:**
>  What Microsoft does with its hand-holding OS that dictates user experience is of no consequence here.

It's not so much hand holding as driving everything from an system wide event loop, which is arguably a robust alternative to squabbling philosophers in user space...

> **QIII said:**
> I believe that  earlyoom is still available, but I'm not sure how active development is.   [This]("https://manpages.ubuntu.com/manpages/jammy/man1/earlyoom.1.html") appears to be current with Jammy.

Cool!  Looks like wiw.  I think I'd run it with --dryrun and inspect the output, rather than just let it kill my app.

The docs alone have provided much food for thought!

> **QIII said:**
> An unattended  process, preferably one with a GUI pop-up in the face, would be a better  solution to offer.)

Yes, that would be good.  Maybe with a beep system modal warning dialog...  I think I can manage that, and hopefully earlyloom will work for me.  :)

---

### Post by bitrat2 on 2022-11-05
> **1fallen said:**
> When my Wife was allowed to touch any of my computer's I used something like this: (She has her own stuff)
```
#!/bin/bash

free_mem="$(free | grep 'Mem:' | awk '{print $7}')"
used_swap="$(free | grep 'Swap:' | awk '{print $3}')"
.
.
.

```

Cool, thanks for this!  Similar to my script, but I didn't really know what to look for.  :)
And I love the free swap feature.  I'm going to hitch this to a cron job and a GUI warning.

---

### Post by MAFoElffen on 2022-11-06
Call from CRONTAB. Tested by spinning uo way too many VM's... LOL
```

#!/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com>, 2022.11.05
#

###############
## Variables ##
###############
SwapAvailable=$(awk '{print $3}' /proc/swaps | grep -v 'Size' )
SwapUsed=$(awk '{print $4}' /proc/swaps | grep -v 'Used' )
SwapPercent=$(( $SwapUsed * 100 ))
SwapThreshold=75  # Set to a percentage

###############
## Functions ##
###############
function TestSwap() {
   SwapLevel=$(echo "scale=0 ; $SwapPercent / $SwapAvailable " | bc )
   
   if [ $SwapLevel -ge $SwapThreshold ]
   then
       echo "Free up some memory."
       echo "Swap percentage is at: $SwapLevel"
   fi
}

##########
## Main ##
##########
TestSwap


```

---

### Post by bitrat2 on 2022-11-17
> **MAFoElffen said:**
> Call from CRONTAB. Tested by spinning uo way too many VM's... LOL


Thanks!  Another great suggestion.  :-)

I'm liking the detection of swap behaviour at a finer resolution, but I've noticed firefox (for one) has an all or nothing swap strategy, going from zero to a hundred in a single jump, rather than gradually increasing usage.  These events typically block the GUI for several or more seconds, which makes it difficult to intervene if anything worse is on the way.  So it seems necessary to monitor physical RAM in use and warn the user (me) when that gets below a certain limit, rather than just focusing on swap itself.

---

### Post by dragonfly41 on 2022-11-17
> [COLOR=#000000]So it seems necessary to monitor physical RAM in use and warn the user (me) [/COLOR]

Stacer offers a nice dashboard in background session ... also you can view memory per running process...

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgAAAADYCAIAAAAS6MzGAAAACXBIWXMAAA7EAAAOxAGVKw4bAAAgAElEQVR4nO2dd3wVVdrHn3Nm5tb0EJLQkQAaUUCaIh0EFRUbimDZVVd3XduurmXV1dd13bWsu2vfFVdXbKAgoIJUARUpoffeQgkljSS3zMw57x9pt cmuTN37p3nq3ySzJ2ZO3fueZ7feZ7zzDkkr2shIYQQAoQAEGj8B5wDAABw4MA555zZ07IAQZIFV2UpIYQQ2tjwG1q/HxxtAUlKaNR7cg2vAkESCbQFJEmIXgAQBEGQpEKM9wWYCZrac9Q1t40f3L97bqaVVZ06tmvL2rnTZy3Y7xIKp/zvxeu6p0kCgOJ1VZ4 tnPz6q //GbR/moOQPOvee jO7NnPnHjuzuVxrN1vPOd1  l06fc /leFsdPhZgPknfrG28/1G7VU3e srDcPx4iaaOefP2lkSf/dcfjHx/jACD1/ 23L43L9u9qsjPz75v0zloFpEEPfvfi8JJpf7jjw/2y/5uI59z037endFj653EvF/m8JOX2HjPl pFDLuicn0rdZ45uXfvDl9O/XVHsrr8O2uX65/7zqwsyrQLhquyuOnV0/4aVSz6Z cPus9DmsidmPDGw/IsnJ72709t4zW1vfOXNx3tu 8tdz88 aa7wDgVAL6SO1z3z7OND2rgOFi2avfxoNUnLP6ffgBGDls36bj8QR0ZOqrD/u/98vLGGWlPatOs bOykF0cN6/vsky vroz3pSOIP0JGTialGZfcc3PPZf/28aQAlp7X/npkJqXu7HQKx9T6zereBf/7YrunYTfuPnxIBQDiyMp0UKn79VOu OaFuad9nC/JHPfLCedZiZKRZgeoEwDi7HvHM6/edp799PYli2fPLWNpHXuNGn3730ePmPnicy/9eIYBABBbRlaG5dTSqTNWnGaiPb3DuYPGT37kshHnPfrgf1Z /9mnN/a/98obLpvx4reldW9n7z3htj7ivk8/mWcy7w8oAHph6X3n449dmrp7 rMPv7eptKHDTgQRGoyEndi0/NuFVbVt8MPZW//x3m vv3PcjLVfHIrDBSNIeGhmmwyiqrzzVRPHffnC12fq/SbJGDNlXFfCVEjLSqfg07aPb1g8c0FVkH8l2dnplKvMcdEvbuj5nY WSD2vvuNiB1M5Tc/IoFDJAIBkDLn3r7edq6z69 1/nrfXXbvj9Hc/Hv6nVx  /vGH9ux79svj9e/AKrYuX/rtUQYAMGfOzM1//OzRy  7et6qTw5 9t7iCS NvfOmnotqgwCSN GOy9qdWfa7L/Z5wXTgGIAekOxhd13TEXZ/8dxUH 8PAFxVwvQ52Mn1P 9XhQ4dOwu6XCKCRA1JScuU2O5589bTi267rkCq3y52u/K2iy2b5yzYzqwZGbbgaqrgM2VkplPXmhnzT3UYf/2YzPojSPqom8d2ObNs g9nIT09vdZL0Y433Doku3rt63 fX /9AQC8x1a89ObyUseFt99QaAn9LqxkzbodKu3SraMIUL1u rsrqztdc8fEDgIAyRw65ZcXKj9/9NnKs6br/gMKgD44 wzoa1e3LVlxUG165zos7TrnUn72bKUZmyViaEhqehphZbvnfrD4TJfx1w5PJQAAxDlk4uXdyld8MH13GaMZGWm AmBxpmdlZWbX/p ZnlInGkJaegqvOPn9jLkbpf63Xt2ptrdDO1025VLb1lmzFh8/S9LSMwgAAM3pfck5gmvd8mWlASbBzxat LGc5PXve06Y3pKY0zaXQk11DQcAXvrdf77YBOfdee wto7CO381JHXXrH8tOGXOcTQUAB2gbfJyLNx15Ehp5EZWayS5 Z0uGDT2gRcevj5X2TVv6VYl4jEIojs0LS2dqmcry9Z8OW 7Y9CkcbkUgOaOuGWYc/ecOSvLqs7KkJGZ6uNcpEEPvLNw5v/q///Pk4MkAABiz0gTeVVVxbGl05ZVFlx11UA7AFj7X3d5z6qV0 YfqzhbzW3pmXYCALRtblvKSoqPu4MvSD524LhKc9rmNb6lYE9NzcjIaJvfqffQ65574qrO/Nj8RTtqxxLUI/P//sVBx Dbn3/2nhvyjk1/6 t9ZrUyHAPQg7rn6proy0uDHnhn4QO1v3Nv2f6lU//198/3eVGlEYNBU1JSwVXlYqx40Scrr39hwpUXzJmmThjfRy567psjjKdXVUNqaopPBKBum/Hqu tcdX9x9dQeBQCApKSnUF5TXc1qVn65YN YCbeM Gz16j63jMk 9NXcH86yjGoXI860FID6Soho42Gx4N53pt1bf5D39PbpL7751uaGUWjvjs/f 2LEC5MHZByb 3/v 4xOmw0UAB3gZ06VqqRLh/YZFE6HDwLUbTNefbeoWva6K8 cOHy03NXQ2FWmAghiQHwriAKAqkafVUKQmCA5nVZw19Rw4GeXf7n06D9H3nzZYTYuv2TR20vLOQiuahfYU xiQ/UOsNL9m35eEzQITOypTuAVrhoAdf Cz9dNePK6cWNyBlxMt7z69T4FeE21C0hmqpMCqOxUyUlGe3TIs8K moDziPld8gV26lRJg3WpR2a9PHXxaSZ0HP3EA0PVn798b9lRvzFe146vFh64 Ze2hfO3BI9NmwfsXOoAr9qyebss9BpxSX6kcTFWun/Tz2s3rt20c1exj/cHYGfLSr0kKz/X6ZdVze3YlrKysjITN18kHpCUFAfh7ho3AIB3 7yZO yjH7x3TMq mbO3ewCAe9weAEeKs8lRYOJMdVLudns4AC9dNPOH0m43PDv5nMrl33x3kgOA4vUqxJHqAABgJzevOqDa w0fkRlwXpIyYNiQDF6ybsO ht4Qrzm8bdPq9ZtWznnnuZlH88bf/9jwzABnxxiLIi5PclAA9ICd P7jZWVSr5ufvrnA3yoIiaJUAtzbV21xW/pdMbHAWr9J7HzlVcOc8vZ1W3GUGNEX4nDaCfe4PAwAgJd8M2tNtWRxr/726 LaLV6Xh1OnIwoBsDnt4HHXnghq1s bc0Cwike/nrO GgAAuNvtAUeKkwIAsMMzP/6p1DnwwUcv72ZtPIclf gT94/Idm2ZNnNbqDpO1/r/vvHpwbTL7r97dKByIJgC0gd dvlbr33U6cnb73lp5rBVS9YeOF7FbFn5hX0vZHMe/8P88qYOL5v/35kT/jHl3n  1mvRys2nWFbBoCuGdhX2z3rz2xJzVi8g8YPY7VbCq111o7G84scPf/fcD3TvuvryHI/bw0m602cQgOb3HXOD1TfVrhYXLVlVbreL3OX21B2nHvz8xT/vySlfv6tuTJZ7PG4QnU4JQAbgZT/854 f5r46 dcffTBk8YrN 8t5WofCkSP7dqLFc/76ry PhekKeXa9/ aC0a9c eCdS1a9tt6U1Z5hQQHQCV65 Y2Hf7f 2utvHn3RFTcNTpXU6rKSfTvWLzoaYvLJYDy7v3jgwVN33TF 9MgJFzuI68yRDV 9OfWjxdtrsDkjemOz2wj3NPhtUE5u uFk48vc4/Jw4nQ6Glu2UDDuzifH Z7Du T55as3We2kLgNUe2TF/vVL9/ueyePmNMXpoFDDAICfXff 05M3jLv1 uFDxt0wNoW6S4/uWP7Jm9O/ f5QJEuo2Tjj3R H/nncbTd/tWnqfhw1a4REPR0045zjFLhIMtHS6aDRFpAkAccAEARBTAoKAIIgiElBAUAQBDEpKAAIgiAmBQUAQRDEpIQTAI7rniJmhEPQfDNoC0jSghEAgiCISUEBQBAEMSkoAAiCICYFBQBBEMSkoAAgCIKYFBQABMEqH8SkoAAgCIKYFBQABEEQk4ICgCAIYlJQABAEQUwKCgCCIIhJQQFAEAQxKbgmcPzgnHPOgQHnwAEI55w0TD1GAAAIJxyAUEKAAAAFQoCQaNYQRpBEQaCQYWMZNpZhVzNsLNXCLSK3CNwicIkCAHhU4lXBoxCvSjwKKXPR0zXC6Rpa5aFYwNtKUAC0h9e6ehUYY4wBMM445zz68nO/RaxrJYBQQighhFBKqECARrW0PILEFUqgY7rSo43cLUtpn6a0S1Pbpyl5KSptUev1quRMDT1RJRwsEw WSQfLxUPl4pEKQVbRGKIFBUATOGdcVRlTOVM5a4avj LUtSuUq9xXFwgQQgkVKBWJIGCQgBiHLDsb0MEzoIOnMEfuni1bxZjZgkXg alqfqraN9/bsFFlsOu0tKXEsvmEZdMJy5Hy2L1fMkLyuhYSQgghQEht4oEAAOHASf2N48CBc8Y5t6dlxfFaDQ5nnDGZM5WpKvB4tjpCKaEiFQRKBUAxCI rsjRU46/7Vw/3WREAbSEq0qysf3vvwA6egR08BdlK/eY4GEWFm649av3pkPWnQ7YTVYL F2BwUABaC2cqUxWmqJyrTe tO4QKlApUkIiAA/6BoADEEAJwYb53dDf3oA6ec9vKjXcwWrevuTzsK5V PGRddsC24ZiVYVwAACgALYYzVVUUrso8rp396CGUUEGiokQIKkEdKAAxoUO6elXPmqvOdXXKUJreu4Hm2U0sraykSvhuj33 bseOk1JiWK9moAA0E85VVWaKzBmL96W0EEoFKkpUEDE7hALQGlKtbGx39zXn1vRt521672bREq/ckmMOl4tzdzpmbXOcrjFpdggFIFoYU1XZy9Xm9HEMDaGiQEWJUvMWAqAAtAACMLCj58ZeNSPP8ViEkG5Xy151C88d6TCFkcV7bZ9vSdlwzGK2gMC8xh89TFGY4mXMiCn VsCZojBFIVQQJAsVsCUgTUAAhnV13zuwqleu3NSOvsTUqYaLWpt4k0jBrkj55T1cl/dw7Tkjfbwx5euddoWZJTjGCCACXJVlVfHGt6RHHwiplwGztHwAjACihhIY2919d/ qHm2UWDh0fQ2qme927Kzw36KU2TscXhM8T4ACEBqmyKrs5TxRE/0tgxAqSFYqmiUaQAFoEpHC HNdv pf3TlDgRC NFauPE59rPBve6paeGd1ypfbHJGjh0THLKYePUxRVNljNtdfC dM8bqITAXJQkUp3peDxBMCcNW57vsHn22XqvpuBAAfRfRXyla9WwC6SEL4hFKOUz1VqcqumuTuEiXtB2sBnKmq15N0uf5mwzlTvG6iyqJkIxRrRs1IQbby9Miz/drXlvfUukkfj0x8PGdoMYBWe/A4SUL9m5 uJkt209ouEVUEwZKctoACAAAAHBTZzZTIQ1vmgquqolZTyUIlC0nqKBjxxSHxXw qvr1vddCDgw1tgAdsJj6beYj9gw5pIVqOLQfx2LcprH7wjzGVuaupKImSNcmKp1EAgCmy4vXgyuDBcABV9jJFESxWLBNKegjAmALP48PP5qawEL1 vx0bCHT4eokBaBoiHK2gqw4EbmSK7FUVQbIKSZQdNbVVc8YV2cVVs d8IsM5UzwuIoiiZCMtm7YRMTydMtQnR5wd0jngka4IMuC7Q9A /mIQ4rWQR7WWmEnCo984Q88VwbnqdTNVES3W5Hii3rwCwBRFlV0mqPCMDVxVZFYlWmxUSJ7uD1LLhEL306OqbA3zZgYaRRgvH U YXNEoKUYBJ8/2nfZfVrYUBxpB64qiksVLNYkKJQwowDwehmP94UkGhwUj5uKqmixJndtnHmwS/ypkVUTCt31G oWIqr7K7QSRPahkZQAwuaIQHsxCH6X0O/12NfOJh/94cAVr5soimi1JfTs66YTAMZUxeMGU1Z5xgSmyDJTRYs9KYsiTEVBtvrq MpuWcEp0HpHH9rhRxMQNLVbgxiEUALQSwyC3wvWHRV3lkQ9fylTFHeNaLURmqhTCZlLAJgsK4obh3tbCWdM9lSLki0JQmDTMqHQ/cyo6vrlWUJ6 nrPSEI76egCAohWCcAIYgBPzbM36104Z4q7RpBsVEpIWzCLAHDgqsfDVCz0jBEcFK bMkW02DAdlFjYJf7MqOqrCz0AAb4unEP3yQuFlYHQr4XZM8zOzRODaN6xeSzbbzl4ptnn5ACK7KZMESz2hMsGmUIAautYEncCZ8PCFEVWXZLNnmTF0UlM2xT27 squ7dRodZ91n5xfinvlslAhAMj7Bx f/8cUZj9YhwcPLfABtBCL8FUhbtrRJstsaqDEulaWwZnquKuQe vEZyrsqfanDNnJBxds9RPJlV2b8MaJjyq86Ah9JuECexIXVlPWMUn4Y9t0f71r5PIb9t4nhb2Rb7Zbj1R0apmzLkqJ5qrSXIB4KqiuF2JsmhXgsIZl93V3PRTaBicC/OUaTdX5qc2uCfi/4OEkYGQ MiAbkoAPkqggRi8uNQa/c5h4Vxx17DEebQomQWAKbLicQU hoJoAQfZU8MZVtYalKFd5f/eVJVhC9jsrwHQrFDA56UmPG1ze XR W7/sKCVYvDZBmtpVWx67hy44q1RE2RemaQVAFX2Kl43 n794KC4XTjMbkCuKfS dW2VTeT1iR9fSIh0kIYy0DIlaDosaI0YcA7/WB6L7n/jGUH1uhNCA5JzEFiVvarsifdVmA4OoHjcgoULoiXe14LU8cv nkeGuQBI3TApAeDBo7V1r5KGrYSEehgqwjBv/UtNjwQ3a6w44KimDiQ PyMMV/udEP692lrpjn3iXvW6AcDgEwclYQTAZBm9fxxRvR5VifUq4UiL EWd96 F P8MDgXqfkQMBYIPDHgpmmgAQvbEoyPqA6MLCxiHf6/Uqr9i/Dgg2QSAKV5Fdje9H6IlqteDc2vHnWsKvY8Oc/u7viY1IJpRAWjKBfvLQFRK0AKapwThxODV5XaXV8O6HYNrQFIJgFo3sTMSf1SvG8eE48iwrsoLl7tCOXofDQgxJAChNaA1MtDkjo17aKwEPvvW/pQZfFykeRpc9bqZYlBbSJ4xAK4qaoL1/QmhhAAFCgRoXf Ek/rOU23xKq//j3HGE6jcngPIHpdkdSTuNCmJS 989bWrXZQQnxx4mN/rhgSCJ4GoGxKAJkYFAvcK8ypEHh7gAMcrhYPlQmkNrfaSapnUeEntL4yDVQCbyK0iz7CxbAdr42RtU1iHNFUSwsxdEc0AAwEAeH6Rw6voYVOq1wXEQQXD2UKSCACvneLN2BBCgApUEAihhFICtNk9Hg4cVM4YZ5wzxpli6EccOMieGsnmTKxnIxOdrlnsnetr7BKvG/MlDYXQzdUACDEyDBBeBqKZG65OBspq6Npiafdp8UCZeKBMOFwueJTmGQMl0D5N7ZqldM9WLsyTL8iTc5yBjzg0fISQ1Mjw1Waqz0pQHED1uIjdToixNCAZBIAzLntc nyRzYYQSgUqSESgMfCDBAgIRBCgvhVxrnKFMaZwphhRCzgonhrJ6sS5IvQhN4W/d4Mr3QbgW/fTQg2AmIYCUOUlRcWWNUcsq49Ie8 IoVdciRrG4UiFcKRCWHHAWvveeanq0C7e0QXuQR28PutZhg0LnprvUFT9bIYDl90uyeYwVH I5HUtJISQujRffVKQcOA k4Jz4Jxxzu1pWXG81pBw4Iac6YEIokgFiegV9HEArqpMkZmqGE0LCREku72lGV4NcVWWhmr8ENiFbHyY0NC2YJf4p5NrerSptQUOAfPocJ/fG H v4ZeByvU3uFCgcAdXTJZtNf69Q7r2mKLqouZplr50C6e0d08Q7t47FLwRXIAKHeRwa871VaqUPMhRBDtduMssp3wEYDqcRvK 1NBFESJ6L6CLgEggkAFAYAzRWWq1zjPo3OuKl6PaAl8DhWJLc M8fTIYb6d/cYgoDb34p/RadgN/I6AyOmgxpfDhgIAQBiHnw9LX  wLd1nccm6 ruzHjJvl23eLptV5Jd29k7uXTOoo29dMgGAx75x6O/9AYBzVfW4Ratd/7cOSWILAFO8BlnYiwAQURIkiwHiO0JFkYoi54wpsqp4jRAPMEVmVMD1A7Tj2l7yhPOV4ISPnwZA43afQwM0IHiHwN0ijwq4FTJjs 2j9faSqjjbgkchS/dZl 6znpuj3HFR9RU93LWpoeOVdMW JgcttIKpClO81BgPSyZwCogxVXXXGMC5EUEUqWg15oLpnHMme5kix39OJAKS1WmodcSSJgVU0IZNv7XG1tCda/TIAWkd31YQORcUvEPgxuB0ULWXfLrRPm2DrcxloG 5gdwUdXIf1029an4907H2UJzNQbIZokAuYQWAM6/bFd VHQkQKkmCKEH8e/1NwbmqeJkcZxkglEo2h3EGA5JDAOwSTL/V1S2b fjkQEcfajAAWqoBIU5RI5MPiuyfbrBVeozy5YbDaeEut x2e M7VEYIFW2OuK8nnKgpIMXria/3FwSJWqxx//6ihRBBsgqiRfG645g044ypXo AgwEx5enRnm7ZAbYQmPAJNRgAQameKHNBftsJwLxd1ldXOE7GO ETJdVeAtRisUuq7InjM7qcM8XrluI9GJCQAqDW1brEB0KoYLFS3Yd5YwAhotXOmKJ6PPF6pkxVZEJFKibg3TMk1/ZSru3VYAvBHjyYWGrAwTLhhaXOVYcTcGiHEMFio6KkeONWRcJVhaleKsRzMCDx7JAzzuI334MgSVS0JUq/PySUitQuqIqsxuk2KrJLEvDpsBjQKZM/M8bb5JhtUJ1/eKcf8Gdd0U I88sqvL3K8eE6u2yUWrOWQKgg2ZxxnDxY9XiJTYrj8GHiCYAix2eNF0KoYLVRA4zbxAIiiBZKBdnjjkMmjYPi9cQ9 E10CMDTo702KXwqO8hv 22IVAXj/1pQeeiRcvrItynbTyae9wiJIFmoKCjxKCjnwBU5nomgBOuF5Z9LKY2D96eiJNkdyeL96yBUsNgcVIhD/M5VxSD1u4nLmB7qpV1VgIAxdeL3OwncTnz/DHo1zHn8jl64xzLx0/Sk8f61ECJIVme8bCGOQxGJ9C3aUsjIe5wAzu9eKz xp0a3MECUrFQyRNFu7CFEtNpURahdvEJPVK H2AXjPBKZWDgs8OQoX68RTVV7qFRP2MGAoC0EZAVeXu78fJM13gXF2kBAtNqYShWP3gVCTHYLghiX6VISKQK4aILV4iAWB7n6qczL7s R7Dr0x4losSet969HECXJ5tDZFXPOmIzrxrSQ31wi56ZGSP34/B70tZKAX6OLA8pc5I4vUj9LVu9fDxUsks2uc3Uf5xCvQYiEEYDsTkKPIXWOmBDo0t9y 1t55wxI0c5tEUokm8Mk9Sq1o2E6D0Yx2WuoaTwShYI27Bf9axNofhmdMJDg38PvHloDjlXS2z5P3XzcPLag95RtqiIzFofx9MQQAELgklvsAY2TCjD6/vRrns6xZ8Q c0eoIBrssVWtIYRKVqee09VyAFy rbkQgD9dJgshGmYIRx/qrwAXT5raAXafEm/9PPVgWVINgDUBofqP cWluDExHFy3QZacrkLIjktugWXKP3N6jU2PYe VUEHUPQw0BIRINrue7b52BlPd3i4JuPp8tX H5oZNIVpy ESQ3x9FxeIdM1IS5SGvmEIEm51Q/YIexlT9Fw5LgO VitD36ropvxvwdc6EwMVTnBP/1jY9z9r6tyNEkKwGmq9VbwgRrbr2fVQcCYgakcKDQxT/2Sp8fzYvCIioAQAARcXivbOcZw0/u4NGECCizaanBqiKW fx5wQQgIKLLSnZTVwnAUjLFSa lD1wUqYgtvxDEUIlm83sq5cQEK36LV3EOWMqBgFRcVWh2i6tZQ6CRM7zBO /57TwwBxncxfqSjJqNUC3pRw546q QYDRBYCK0PvKJvv1jW30wivsk/ Zm1vQotlmCBFt9gSY2U0HCJFsdt3GhFWvIeasNjgCgXsuViK57sCXmv76wgUBxyqpmfv vhAgokW/MWGdS OM7uyCuv8 NWthYlxrCrn66axR92VLtuboNgHJaqzV2uIMIaJVp9pQzhk F9Ykl/VUu2RFWIsx Peg3aJLBJW5yD0znabM 4eBgG61oZwzpuqnAYb jqkIfWq7/01XuwU243MGWqe8ldu5nzNKFyZZHaaq YkGQqhkdejzXqoSt/mdEgICcO8lgWWCUTTtyLuEKPqUVfjtbOfBMrQFfwgVrTota6p4Zd3iYUN/zd0GNp399yXgyxEFGPNA lVPtrGnNjGMI1isRlicwYAQKugzezNnGAREYkQB65kT8BxvKAKHgoNeDvWi77aXl9k3H0dbCAGhgmiJQZlJ03DG9SqNM7AAECgc2cQjuGFjMp/tuT0sk1/POW90argIjlBRMMbybMZEECV95kjBcqBwEIBfXxJZHZsxMhDy1dofC3ZLn29EWwgLFSV9ngxVFZ1swbgCkNNFyO4U8l5H4fUDNhEy LaUG/6Wk5Yb1LgJFa24PkkTiBarDmPjnKmMYRAQgkGd2QX5/tNztpywFc7F5fTZhTYcjI MKNl1yBVzxvR5MNi4AnDeiLpoK9STi2GJ8Gp6rjDxpez E9OpT52oaLGZ8YGv5kKIPjLJZKwHDcFNvcP6gjC9nqasJGg0WFbh99/Yq7Dsp0kIiBa7DrdJnwckDSoAthTStb9/bz1czjNcdXOo52QAoPd4x6R/tM3pZgMAKll0q/BNdCgVBIvmyQGmqj4LmiMAAKlWGNU95KO/0Xuhpqv 3/rZur0EbSEqCKU6TBDJFEWH2miDCkD3Sy0tXnKxycZuTyXXPJPZ78YMUdJlSCdZEESL9mWynDEMAvy4/FzV0uiZo8v1R/MAgM8 B0rph0VoC81AkKzaJ4K4DiMBhhQAAj2HRG6O0fV9wgQBtZzY2dzLQogOFUFqQq8xqAHXnN/EzD8R6oGa3gsAAF5YYsO73lx0sAUdskBGFIDsDkJa20gXFti0g7JATerDvlXKqf3Y5JsNFQTa4tAsOjhT4rVgvQHpmMH7hZz6LQZJ6LogYN5OcdVhTP40G0oFQdS2Oo5zxjUeCjaiAHQdIMVuYs8QP2U33zAbHztqIaLFpvVMefrPiWhYri5kzSnxDMgCNR0EVHvJK8uxCq6FCJJVc67ASF4AABwLSURBVFvQ OEY4wkAgXP6BQ6wBD 03hq2LZJdlTjS2FIIoZK2HR cG64WEkX p5Xv8EGR5WQVVv60FEKoRVtb0HpuOMMJQJtOQmpO6Ml//PHP 0TIAvkHAV4X7FyG/qVVCKJF044PZ5pHvglB73a8U2ZUPZWovwy/Hau85OP1cVgGPZmgokXb SE403TVPMMJQGD1ZxhafMt3LPHKLuz tw4dggDMAgFc1qMFlh85C THZxsknO zlRAggsYloZoGxIYTgC59Y JZQgcBsovv B67/zGAihaN z0YAcCgzhHL/1t4/ sOcyvw0Trs/scAQZQ0fZZU086QsQTAmUkj1//4EyELFJq9K2Xs/scEQgjVsgSCMbM/EZZmg/Nyo7kDEdt9 CBgxiaptAa7/7GAEKrlZGKcM 3q4owlAPk9myoxbHGLJQAAu1Zg9z9maD2DHlNNHQQM6Mia1dib8xgYYRw LMJJ32KG5vWgmtmCsQSg3blhBSDEzOVNnCyw83Nsu3L2FBaYxwxCqKYTaegzGZZhGdRZwwDo50NCyVns/scOQomWz8do1xkykgAQyA8vAFGdIGKT3vUDdv9jjKbTRGvX60kIBnWKorMSjQ8PlQWauw2z/zFG1DII4FyrYQADCUBqG5qSFfJ6WjXXeV31Zw0/ug0LS2IMFUXtauA4V7lZhwGyHLx7TvSfvXnPybhkWLJXj0ntzYUgajevMGcctBkGMJAA5PfwaZSxvpOHNyo41bwGEE3XxzBtEDCwU2Tv33SWP8JrC3eLLgyGYw0BIFTDIEDVxhYMJADZHf0SymGbcMTRrpAaTAAOFqH71wRts0BmHQYIyv 0rkPknwX6ejt2/zVBEDUcEtPIFgwkAFkdtbh9BAA81fzEbhQATSCCoN1TwaYdBz4/T6vcV5WXrDmCU79pAhHEqKrRWwTnyS0ABLI6NNEuo5v2NgTHd6pm9SSaQwCIZrVAnKs6rIlhNAQCBdEPAJBQPwJ hcYgoOgIVbEUTjMo1UxcVU0swSgCkJJFY7XOWpAGk O7sPuvIUS7Rs/BhFNDd8zkNs2SNKtx5mct0W6ydA5cC1swigBkN9X9D0c0onFiF/b/NUTTFQI0inyNTI9m1P80G5z6X1O0i4YBQItZ4YwiAE3lf4Lj2WipKWOV PyXlhBKtZsXiDPT5YAK2kAr63xC70OgzEX3njaKySclhNDEGgYwSmtIa9sa5QxK vhsOHXQjHlknaHaFcCZLwXUPr1V7TWC 1l7hJpPT/VGu8fjuQbDAEYRAGemVldSVmw6D6I/2i2QzVAAmiTq58B2nTSKvScxhGg3JJbEApARVdwUcqfIR5YWmy6JrD EaNaQzNdl7ZARw5P5Gcf MqPYexKjnS0k8yBwzCOAhiwQRgA6QATN8p7mU4Dc1NZ 4nBfxsFSnABOc6igmVNN4ghAtDazaQal/UPupcpQVYYCoDkENKwENdvCABqJKQc4jBGADhCtaiI4cB7r8UxDN4jW38aacoYjwHpAgFDtKoHwK4ToJkSPlCI9VkHc DyMLmg3K1zMbcHAAtCcexi64ROoKUffoRMapj5Rw5skCmM5hN1/3UicYYAEahMtEdXqcsz/6EXi9HrMQPCXcQYXgNQLLSOAGJ8vgQSgjvC3NsQrLowA9EO751/wS4wB1d54X4Fp0LAoDgWgkSgcjuxB36ET2vV6sOPaHMIOA1R78UbqRsLc6kQWAH9C3nLViwKgG9o1evwSY0ANRgC6oWEGyLxjAC1BwUavF9qtCmDeDFDTdzTS6kgBGzAC0JGEudVJJgCB912VTes89IYnTJs3JwTHAJIBHANoHuiV9IIQ1FpDg6agGwlkC4klAEGzXjU1S7TFhs1eJ8ybqDEcodu806rzZZiXBLKFxBKAZiPFaJUxpGk0a/TaFVUnPb53LsUSt8swHYljC0YXgOZ/Xr8jJIwA9EO7bg9 ibU0dR8ivp5iTZx acKTMLZgdAFoJSgA pFAca8pcWIEoBuJYwvGFoBW9v8BLPYYXQnSFBrO2IMiHokm1sho A0jAN1IIFswtgBEQ4g70rjJgmMAuqFdr0e7B vNRBoKgG4kji0kqmlF6ddTchL1AyYc2q3eruHUWmaiQ uWGkaiJ4FsIeH8Y/M f1obKmi2XDnSCNdkvbpaUACaQfhb1TGT20Qdr8S0JJQtGEUAYnjHiP8fGfmaLVaF1MO5ZgsvEzDbIIAam 5j4DAAATgnG2dH15zEsgWjCEBNRWybZuNtysg3ymdMYjjTrMtjmCaqG6eqtBK8gjaYBdKcxLIFo1hX5clW3LWI9pLRziifMYnRLuYF7VaaNCqHy5p7RLS3qAAjAO1JLFswinOsPKVV3JTRDlNAmqNlr8d0X9/hstbZefijMQLQgcSyBcMIQPgIIFx7jmAlvi9ldxRMlkOOA9o1emq COBIeZRNu0kChwHOy2Wmu5u6k1i2YBgBOBXzu1Z3sxwZBIcBNIUzllhhr8E51OwUULS0TeHd2mAWSEMSzhaM4hnLjmk2dA7QvhDL3zSEMUW7kxNiuhTQvjMaat6lXVAANCThbMEoAlBRoirRLt8Yyjwimkz781EANISrmjV6ouX62kbl4BnilmN/2loTGdJVw54WknC2YBTr4gzOHIll0/RVhLzuomg1XSZBLzhTtfIplJpx/EblsONkcz92Uytj1DOgI7Pjo5FakXi2YBQBAIAzh0Pdu1Z95rqDqQh53U2XSdAHpmqYUjBh97 W7SWxsvXA80gCDOiIQYAmJKItGMjAQgtARKK3kg69MAukCZxpkK1ogJpUtref0DDwGXYODgNoQiLagoEEoGSvhuMnXQdIOClQ7OGgKhp a9SsArDhqCYCUHvSK89TrdgdijmJaQsGEoCKk6xVE0IEmYzvBquTdLkIFSDGMFXWcuZbQqiB2qeeHColdRNCaCAE6TY tgdmgWJMgtqCkQyMw/FdMZfQRgPqMRSXRIoxTNEw5qWCSbv/AMABVh O1fPAIc5zU28N 6rmJEFtwUgCAHB8Z5TtsiW2kVsg4LxAMYQzxpiGHUlCTZ2nWHO4uW21GUZxUQdWgE ExY7EtQVjOcRjYSKAWMXBPTEIiB1M8Wp6fsHEEQAArD7UgjlQmqbh4Jt6YxYoZiSuLRhLAM6eYuXHm9cuI1tDwKu5BWasK9cIjbs81OQrQR4pJ/tOa9hY 3XAeYFiRuLaguGi7EMb5JYv4UIg1GrMBICXHWVbFngOFsnaLddsNiSbkymKKnu1WAGDmjv/U8uSPbRbm5jcWz/D2H2KTl0tfrdLQFOIFYlrC4Yzs0Mb5d5X2mJ4wpI9yuYFnqPbFHT9MYeKIhVFpqqq7OUxnQWFioZrmfqzeA 955JWOJSg/lBRMX1vlfjjAXT9sSdBbcFwZnb6kFpTzhwZMQh5Dm StyzwnNyPuU5toYJABTtXmap6WExKoQkhZn0CwJftJ0jJWZKbEgN3vXSvMHW1uPGYqbNqOpBwtmA4AeAcDq6XC0dZW3wGpsK 1d6tCz3lJ7DOQT IQEXBzkWmKl6uyK1xWgJ2/wEAgHFYvJtOuSj6Hkxgn19h8PU24f214n4tZxhFAkggWzCipe352esnAOEz wGbFA/ftcK7bYm3ugxdf3wglIoWG5csTJFVWQ75zTUJFbBYq445W5slAI24ZJi UfxfkVByFl1/fEgIWzCiAJw rJYdUzOjXsqRALiq PYlnp3LvZ5qTG/GH0KoIFkFyaLKMlO8vDlPSBJKTfsAcDDbTpC9p0mzlnIsc5FpRcJnG4QKN7r  GNwWzCiAACHPT97B95gj2bfqjNsy0LPnpVy1MsJILpBBMkiiBZVlZnsjXKlJIpzNvnAAWZvpY OiCoIOFpBPlgrztoiaLGcANI6DGoLhhQAgH2r5AHX20nEHkxpsbplgedAkazZGpxILCAgiBIVJR5NnRwBQUQB8OPr7fT3w9XIqwHuOkXeXy3O30m1nJAYaTXGswWDCkBNBTu0QQ43fduJ3crmBZ7ibVjUnzAQACKKVBQ5UxSvHK5OjlIJIsu  ThVRRbvoWN7hHbta4/QqauFH/dTNIVEwVC2YFABAIBtSzy AlA75ntoY21lJ05llagQKko2MVydHJWw x CaUWCvwAQAL5kD526WtiElZ0JixFswbgCcGKvcuawmt1JAACmwt7V3i0LPc2dKAIxJg11ckzxqvXTKFIqmHYBgMisLybbS0hhLoe6yk76/hoBKzuTg/jagpCSmUMIIYQAIbVz5/j 84EDgGSNamA2VigytC8Ud3zv/X5qzd5VXncVhrlJBSGECiIVJQKEMyZIFp2f/1I8rugafwBxsAWPQgZ3YZ sFx75Wpy7TShzofdPKuJlCySva2EoG DASb275cCBc8Y5t6dl6XBNDQgiiFaClZ3mgGuy klEXJWlUQgABw5xtwWLAHYJKtx6vicSL/SzBeOmgABAVUBV0PubBOzSRsKrghfTn2ZBP1vAESQEQRCTggKAIAhiUlAAEARBTAoKAIIgiElBAUAQBDEpKAAIgiAmBQUAQRDEpKAAIAiCmBQUAARBEJOCAoAgCGJSUAAQBEFMCgoAgiCISUEBQBCchw4xKSgACIIgJgUFAEEQxKSgACAIgpgUFAAEQRCTggKAIAhiUsIJAMHKCAQBALQFJInBCABBEMSkoAAgiA8E8LEAxDygACAIgpgUFAAEQRCTggKAIIjBENqNmDTp9sH56J60Bu8wgiCxw3bB7/77ybznR e3YiRFOu/y39197YWOKh6764o5QsGNH3w17b2bOwvxvpLWIMb7AkyBJe iybdff WAgo4ZtLrkwOr501 fvr5EqXtV7HPv3L Pz23UYmXzO/fdNeMEAyCObjc89OvbL mS6T648IM3X5l/yA0AAFLBLf976 qT/3zw9/NPszh8ICRBIPbu4259aNLQPu0cSumh1Qumv/7xmqNy4F7i XfOfP3aDgG9QVY558lfPL9GCdwbgDg6DL/u2htH9D2/Y5aTespLinduXjv789lLj3iASja73eGwCgAAtNPVj//jjgvzMxwWyhVPdWlJ8Y71P834fP7qk0EX0Yh04cjB a4Nb60OLQC2Llf89dW7Oy144qb39qgNWy2D/zrn8bG2Rtnxrvzn2KeWng06PIK5BWPN63P9TVddcXHPrjkpklx1svjApjXLPv78 11VnIhWh92qWkUAAJIx5tE/PzI0L8tpEYB5aypOFO/f8OPCj2auqrNYo4ICoD208 3PP31X1r4lC2Z8VWHtdum4q /6Y1fpiTs 3FtrBNRut7Nj89/57IfS2kbIy/eUMwAA6YLbHn3kwoP/ev6DI dc 9TDj/5y78Pv7FGBtBl/99VdD819bhF6fyQCpN0Vf3jnkV5ly7986cPj1h6jfzH5yXey/3Lb34sq/D2revSH11865GjwicTZ54bbr8k/vOd4iPZFcy996qWHJnRkh9evnP3D0QqSmtuu0wX9h/b5btbSIwA16/86ZeLLXFU5ABBHTvuOGZWL33vvx1JiS81s36PfFePvenPYeX 67 X5J8P07y2FY4dkV6/54OezQTsI6eePm/zEry8vTGWHAj6q1e4Q2K45b/9vc53HVU/vcoU6fXhzC7x7mf3v Nez1xVKpzasWDbtYDlzZrfvWNBvdO8lny3dBaDs/OSWqz4HRa011TYd2rfxbnz/nRWHmSU1M6fgoqGX3/XkqH5T73rs6/0hNNQooABoDzs845VnfzyxdWdtg56z1fPBnyeOGtxj2t5tKgCA6HDYeMm6xSsWlPu3eKH9xQNyDn730hdFB9UN3nnj/zaoX 6/9xx39L/57n413/xx7h4DNywk/ojnTbr1IueOj 76y6xDKsCy1bvpP6feMOnaz9f/r9jP4/HyPUsW7qn/i6QM M2vuigb3nlrxpEgxyh0nPL0Q9e0Oz3n/5772wqfbrwoikp9c2Sq6nsIL9u64vt5x2vb9szpm5/58tFBNw5ru DLkpDdF1vvIcOzq39atiGw8 7o/fAbT07pouxYvGrPqIEW/xeJ0 Ek3gNFyxb8GCG2AIhgbv7QtqOeefq682pWvfDYa7MPeRq3iyI0fFDF/4NWHVyxcNn22m3T5/z0xJuvjL78ym7z3tzlt5uhwDEAHeCVe7bsbOjOeE8cOcmI3emoi1ZJapqTqFWVNcHNUZREkGWFAwAoXhlEQQCxyy2/GulcN31qUYgDEKQBmnXOuTlwYsvW4jr/492 ckMJ7TKgd2qk/Lx4zq33jsk5MOfvc44G y3noBtuL7QUz3nrlRX SRyl3v2LPR aNvvnv4xKDX12Xn7qjJtHeNbC1n/kwKyzRQuLagJfcR0pWjjrmd/cd dba4KDB5KSlgbVFVVNhsQRzM0X8YIbJg5NrVjw5ptzfLw/ADBFqX0P2v66DxfN uCmvNA lLtKTlVzwz9TggKgNzSn76XdaeWWzfXdApqRkUZYdt/LR40Z2KNDis Qklq8cXt1t Gj mTYsnuPGtmhYsv2kzmX3Tq5c/FnU78vQfePRIS7aqpVkpqZ0dBZZmdOn2ZCm5ys8GZPMofdOLFr1ZKPvtkdIr4Ue13cN4MfW7J4Z3My24LVnpKakpKZnddz4PinfjM8o7zoqxUnQ7tqx4VjL0kr//nHtcHpG1764/QZ3 2uVEO1fJqWlkaEDv1GXzm093ltbeE/YHhz87vkToMH5kLFmnmrg/NQ4RFEe4ozNTWtTV7n/lfc9fg17au3Lfxun3G7/4ApIL2xdrnl8TsuVje/8t9VlfUty6JWHirNu K ByZZBfCc Gnav579dFs5BwD3z/99e86LD/171o2EVW798rWpewrvfeyimkUvfLoPsz9IE/CqjUvXVQ8ZPvmhtWc WFMiO9oUDOyeTcFNwndLad746wakHp7zaYgEPABx5uemUHXPgRCxQXjEnve//8n9DVcln1jw6ocLw/RfUvoNHZJasWTp5pDp wgIony62FMw4Z7/S7EQXnNg2UdPvzov5CBAeHPzgea0b0vVA8WHm8gn V9Dh2v/M/va r84O7PutTe 22tsS0UB0BFr54nPPvfQ aVfPvv3L4obTEjd8tFTN30EQGy5PQfc9Ku7b7vzj8 cfvAPC84wAHZ69cv33PZWm5w075njlaz7ba9clbLplWmb04b84sVfDL8wj55YP/8f/5i uhTDASQIXvrta692fuqBKU/9YyIB4KzG5bURvqGsMlxzEbqOvPo8sn3qkp3h3BYBAOD vXeSOfLFt27NX/jSXR/uDqEM6qEZL/5ncSkQKqXmdB4w9qrrHn lbdYzv/18vzfw5CmXjOqXcuaHRZsDX2kS95qpt66ZCiCk5J87euIvHp5wz2vuk7e8WhT0USOZm  lEADgPOBoy6DfzHjkwpWvPPDy2hA3iJUs 9vLiw4yoKI9u1Ph2Ouu/P3rf8v54x/f2GjcbC2mgPRC6nDdM8/9oV/13D8/98rqihANgrtLdv7w5rPvLqxMGTx2YJvGXppaffrE8UqZthlx38ROB2dNm0fH/umJsc5V7z385Afrc69/8cGhmUbPNCLxgZ1Z/ bv7x4z6f5bf/O7ibfccdenxYyX7t5fFiZTLvQYeWlXtnvBslDVPwDAa06ddjGhbcd8/8wJtWW0yc52iqGbIa8 smPruo1bitav/37BVy8//vz7 xx9brlmkDVwR5Lab wA 8kff9jYbP/fgFp1fNucN/72xnpv2xEjB9rC7xjW3AAAgJWeOMOEvHbtAlJE1tS2bbLSrWE qPv0jk1b1m3csrZozXezPnz0kQ/Wkq43TxqcYWDzRAHQBZI6 LdPPT5IXfTy//31pzMRBqp4zeG9J5iQkZEe M04Btw6abBr dtf7JfO73MBK5r20cqNm5f/ 6utjr59ChP6WRREW9Tqk4d37Ny3v6L9VeO60hOrluwIk8Ch7QYPaMf3Fa0MV6AJyvaNO1y048hhXaQWX45yfP8RmdjTs2wBfpFkXDz0Ytuppct2ttz/18LL9x0oB0t6prMJ1xvW3NRD6zZXQla/MX0iaEgTsNIjByq5mJ6ehgJgcmwXTnrsquxd0/76/JKTkbOntM35/TpSz9FjASVy4jnjf3t56tqPp6 s8qssCIxRESQk1g5XPfLwTe3PLvtw9qbavDZxdOjRNdenG04yCi/qSo5v2no0bA Fly2fPecoFEy879d9g7oo0UEz 43oZeFnjh2u9m 7JGPYqAutx39evKPVWXOxfb9e2VBx/EhtAijokzZeTBhzA/CsmfXNDjnnmgfuGtG2Zd0rklI4aGAWqS4 esrAT vgGIAO2C4eP6K9cmjFibyhw/PqN7KS7au3nGJCt tf U2Xwxv3FFeotpyC4eOG9xEPfDh9tV/ukmRdfte13Yu/vvO7kwygZuvGrcLkyVMGnl5tufza810b3w7XpUNMjrVdr6G9Orbvet6wUYN7Z51d9d5fnl9c /Agyb/mj58/dIFr4V8m/G1NbcWleE5Bd0HesudIJAfs2fb2C9MK/nr7HS /ecnPP/6w/XiZLKR26NdFgLBHkcxew0dfXQ6SPSUrv/uQURf3yihf9sqcTf4H0KyBY/tIR2b uL0F/l 84P6XrsvauW13STVz5PUePvqyHp4N78wt8gZ Uk805gYAAMr r/70erc3fjf2lfcLf162ev3hMg x5/TuFsFjkpQuw8eN7sYFe0p6Xrc l43olefa q/PggtaDQQKgPbQrE7tHdTac8qTj09p3Opd8vyUx773gFJ20jt4 PWD8tIkter0/q3z//Lx9Ln VXaOvjfdM9Dz3Z/m7JQBANjx755/qd3Tdz3w7s305Ia5T7  AseAkVCQ1H4Tn/ttQeXxI9tXfvrY3AXLDlQ3dEarS46erOlScbS0vs6FpOXnpULF8VOeMGerw7Vr1oP37Lp20oTxFw ZfEmqlXury08dKlqxekPwc ncdfrYsbO9R979wFgKXPVUnD6xf8u3L82ZO3tjwM4kZ8jQvuLRj5e16LFZyXOyhF4y8rqxOU7Re/bYvs3/ 8uMD76vUzK/TxqFudWjHJz38m37Rtx282UjLrlywBU2orgqTh0vWr7upyPBHS75zNHjpd0u/OUj/SgB1VN1pqR4x/wPXvpy/o9HDV0GRPK6FhJCCCFASONyGLVj/XVuhQMHzhnn3J6WFb9LRZAY46osJYQQQhsbfugFYTjagraQtpP  fbvUmbeds9noQqJEK2IPo9n4IEMBNEVtIUYQ/MHjy0U9i1buRe9v77gIDCCIPGFdhw2pBAOLFoRPPcQoi3Rp4A45wzDXiSZcFWWEkIJIc1MAaEtIEkCRgAIgiAmJZIAYKYTMRURGjzaApKUNCcCiDCHFIKYCrQFJCmIWgCwwSPJR132v7lHxf5CECQuRCMA2N6RpCfKRo62gCQVzUgBYdtHkowWN2m0BSQ5wCogBEEQkxJBAIjvr9jlQZKSoLr/kC0dbQFJTiJGACSg4WPLR5IM0uDcQz8B5rMj2gKSfESZAiK1BsBUQ89shyDRw1TF1/n7/xIBtAUkefh/UYJ1eyhm7isAAAAASUVORK5CYII=[/IMG]

---

### Post by bitrat2 on 2022-11-17
> **dragonfly41 said:**
> Stacer offers a nice dashboard in background session ... also you can view memory per running process...

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgAAAADYCAIAAAAS6MzGAAAACXBIWXMAAA7EAAAOxAGVKw4bAAAgAElEQVR4nO2dd3wVVdrHn3Nm5tb0EJLQkQAaUUCaIh0EFRUbimDZVVd3XduurmXV1dd13bWsu2vfFVdXbKAgoIJUARUpoffeQgkljSS3zMw57x9pt cmuTN37p3nq3ySzJ2ZO3fueZ7feZ7zzDkkr2shIYQQAoQAEGj8B5wDAABw4MA555zZ07IAQZIFV2UpIYQQ2tjwG1q/HxxtAUlKaNR7cg2vAkESCbQFJEmIXgAQBEGQpEKM9wWYCZrac9Q1t40f3L97bqaVVZ06tmvL2rnTZy3Y7xIKp/zvxeu6p0kCgOJ1VZ4 tnPz6q //GbR/moOQPOvee jO7NnPnHjuzuVxrN1vPOd1l06fc /leFsdPhZgPknfrG28/1G7VU3e srDcPx4iaaOefP2lkSf/dcfjHx/jACD1/ 23L43L9u9qsjPz75v0zloFpEEPfvfi8JJpf7jjw/2y/5uI59z037endFj653EvF/m8JOX2HjPl pFDLuicn0rdZ45uXfvDl9O/XVHsrr8O2uX65/7zqwsyrQLhquyuOnV0/4aVSz6Z cPus9DmsidmPDGw/IsnJ72709t4zW1vfOXNx3tu 8tdz88 aa7wDgVAL6SO1z3z7OND2rgOFi2avfxoNUnLP6ffgBGDls36bj8QR0ZOqrD/u/98vLGGWlPatOs bOykF0cN6/vsky vroz3pSOIP0JGTialGZfcc3PPZf/28aQAlp7X/npkJqXu7HQKx9T6zereBf/7YrunYTfuPnxIBQDiyMp0UKn79VOu OaFuad9nC/JHPfLCedZiZKRZgeoEwDi7HvHM6/edp799PYli2fPLWNpHXuNGn3730ePmPnicy/9eIYBABBbRlaG5dTSqTNWnGaiPb3DuYPGT37kshHnPfrgf1Z /9mnN/a/98obLpvx4reldW9n7z3htj7ivk8/mWcy7w8oAHph6X3n449dmrp7 rMPv7eptKHDTgQRGoyEndi0/NuFVbVt8MPZW//x3m vv3PcjLVfHIrDBSNIeGhmmwyiqrzzVRPHffnC12fq/SbJGDNlXFfCVEjLSqfg07aPb1g8c0FVkH8l2dnplKvMcdEvbuj5nY WSD2vvuNiB1M5Tc/IoFDJAIBkDLn3r7edq6z69 1/nrfXXbvj9Hc/Hv6nVx/vGH9ux79svj9e/AKrYuX/rtUQYAMGfOzM1//OzRy7et6qTw5 9t7iCS NvfOmnotqgwCSN GOy9qdWfa7L/Z5wXTgGIAekOxhd13TEXZ/8dxUH 8PAFxVwvQ52Mn1P 9XhQ4dOwu6XCKCRA1JScuU2O5589bTi267rkCq3y52u/K2iy2b5yzYzqwZGbbgaqrgM2VkplPXmhnzT3UYf/2YzPojSPqom8d2ObNs g9nIT09vdZL0Y433Doku3rt63 fX /9AQC8x1a89ObyUseFt99QaAn9LqxkzbodKu3SraMIUL1u rsrqztdc8fEDgIAyRw65ZcXKj9/9NnKs6br/gMKgD44 wzoa1e3LVlxUG165zos7TrnUn72bKUZmyViaEhqehphZbvnfrD4TJfx1w5PJQAAxDlk4uXdyld8MH13GaMZGWm AmBxpmdlZWbX/p ZnlInGkJaegqvOPn9jLkbpf63Xt2ptrdDO1025VLb1lmzFh8/S9LSMwgAAM3pfck5gmvd8mWlASbBzxat LGc5PXve06Y3pKY0zaXQk11DQcAXvrdf77YBOfdee wto7CO381JHXXrH8tOGXOcTQUAB2gbfJyLNx15Ehp5EZWayS5 Z0uGDT2gRcevj5X2TVv6VYl4jEIojs0LS2dqmcry9Z8OW 7Y9CkcbkUgOaOuGWYc/ecOSvLqs7KkJGZ6uNcpEEPvLNw5v/q///Pk4MkAABiz0gTeVVVxbGl05ZVFlx11UA7AFj7X3d5z6qV0 YfqzhbzW3pmXYCALRtblvKSoqPu4MvSD524LhKc9rmNb6lYE9NzcjIaJvfqffQ65574qrO/Nj8RTtqxxLUI/P//sVBx Dbn3/2nhvyjk1/6 t9ZrUyHAPQg7rn6proy0uDHnhn4QO1v3Nv2f6lU//198/3eVGlEYNBU1JSwVXlYqx40Scrr39hwpUXzJmmThjfRy567psjjKdXVUNqaopPBKBum/Hqu tcdX9x9dQeBQCApKSnUF5TXc1qVn65YN YCbeM Gz16j63jMk 9NXcH86yjGoXI860FID6Soho42Gx4N53pt1bf5D39PbpL7751uaGUWjvjs/f 2LEC5MHZByb 3/v 4xOmw0UAB3gZ06VqqRLh/YZFE6HDwLUbTNefbeoWva6K8 cOHy03NXQ2FWmAghiQHwriAKAqkafVUKQmCA5nVZw19Rw4GeXf7n06D9H3nzZYTYuv2TR20vLOQiuahfYU xiQ/UOsNL9m35eEzQITOypTuAVrhoAdf Cz9dNePK6cWNyBlxMt7z69T4FeE21C0hmqpMCqOxUyUlGe3TIs8K moDziPld8gV26lRJg3WpR2a9PHXxaSZ0HP3EA0PVn798b9lRvzFe146vFh64 Ze2hfO3BI9NmwfsXOoAr9qyebss9BpxSX6kcTFWun/Tz2s3rt20c1exj/cHYGfLSr0kKz/X6ZdVze3YlrKysjITN18kHpCUFAfh7ho3AIB3 7yZO yjH7x3TMq mbO3ewCAe9weAEeKs8lRYOJMdVLudns4AC9dNPOH0m43PDv5nMrl33x3kgOA4vUqxJHqAABgJzevOqDa w0fkRlwXpIyYNiQDF6ybsO ht4Qrzm8bdPq9ZtWznnnuZlH88bf/9jwzABnxxiLIi5PclAA9ICd P7jZWVSr5ufvrnA3yoIiaJUAtzbV21xW/pdMbHAWr9J7HzlVcOc8vZ1W3GUGNEX4nDaCfe4PAwAgJd8M2tNtWRxr/726 LaLV6Xh1OnIwoBsDnt4HHXnghq1s bc0Cwike/nrO GgAAuNvtAUeKkwIAsMMzP/6p1DnwwUcv72ZtPIclf gT94/Idm2ZNnNbqDpO1/r/vvHpwbTL7r97dKByIJgC0gd dvlbr33U6cnb73lp5rBVS9YeOF7FbFn5hX0vZHMe/8P88qYOL5v/35kT/jHl3n1mvRys2nWFbBoCuGdhX2z3rz2xJzVi8g8YPY7VbCq111o7G84scPf/fcD3TvuvryHI/bw0m602cQgOb3HXOD1TfVrhYXLVlVbreL3OX21B2nHvz8xT/vySlfv6tuTJZ7PG4QnU4JQAbgZT/854 f5r46 dcffTBk8YrN 8t5WofCkSP7dqLFc/76ry PhekKeXa9/ aC0a9c eCdS1a9tt6U1Z5hQQHQCV65 Y2Hf7f 2utvHn3RFTcNTpXU6rKSfTvWLzoaYvLJYDy7v3jgwVN33TF 9MgJFzuI68yRDV 9OfWjxdtrsDkjemOz2wj3NPhtUE5u uFk48vc4/Jw4nQ6Glu2UDDuzifH Z7Du T55as3We2kLgNUe2TF/vVL9/ueyePmNMXpoFDDAICfXff 05M3jLv1 uFDxt0wNoW6S4/uWP7Jm9O/ f5QJEuo2Tjj3R H/nncbTd/tWnqfhw1a4REPR0045zjFLhIMtHS6aDRFpAkAccAEARBTAoKAIIgiElBAUAQBDEpKAAIgiAmBQUAQRDEpIQTAI7rniJmhEPQfDNoC0jSghEAgiCISUEBQBAEMSkoAAiCICYFBQBBEMSkoAAgCIKYFBQABMEqH8SkoAAgCIKYFBQABEEQk4ICgCAIYlJQABAEQUwKCgCCIIhJQQFAEAQxKbgmcPzgnHPOgQHnwAEI55w0TD1GAAAIJxyAUEKAAAAFQoCQaNYQRpBEQaCQYWMZNpZhVzNsLNXCLSK3CNwicIkCAHhU4lXBoxCvSjwKKXPR0zXC6Rpa5aFYwNtKUAC0h9e6ehUYY4wBMM445zz68nO/RaxrJYBQQighhFBKqECARrW0PILEFUqgY7rSo43cLUtpn6a0S1Pbpyl5KSptUev1quRMDT1RJRwsEw WSQfLxUPl4pEKQVbRGKIFBUATOGdcVRlTOVM5a4avj LUtSuUq9xXFwgQQgkVKBWJIGCQgBiHLDsb0MEzoIOnMEfuni1bxZjZgkXg alqfqraN9/bsFFlsOu0tKXEsvmEZdMJy5Hy2L1fMkLyuhYSQgghQEht4oEAAOHASf2N48CBc8Y5t6dlxfFaDQ5nnDGZM5WpKvB4tjpCKaEiFQRKBUAxCI rsjRU46/7Vw/3WREAbSEq0qysf3vvwA6egR08BdlK/eY4GEWFm649av3pkPWnQ7YTVYL F2BwUABaC2cqUxWmqJyrTe tO4QKlApUkIiAA/6BoADEEAJwYb53dDf3oA6ec9vKjXcwWrevuTzsK5V PGRddsC24ZiVYVwAACgALYYzVVUUrso8rp396CGUUEGiokQIKkEdKAAxoUO6elXPmqvOdXXKUJreu4Hm2U0sraykSvhuj33 bseOk1JiWK9moAA0E85VVWaKzBmL96W0EEoFKkpUEDE7hALQGlKtbGx39zXn1vRt521672bREq/ckmMOl4tzdzpmbXOcrjFpdggFIFoYU1XZy9Xm9HEMDaGiQEWJUvMWAqAAtAACMLCj58ZeNSPP8ViEkG5Xy151C88d6TCFkcV7bZ9vSdlwzGK2gMC8xh89TFGY4mXMiCn VsCZojBFIVQQJAsVsCUgTUAAhnV13zuwqleu3NSOvsTUqYaLWpt4k0jBrkj55T1cl/dw7Tkjfbwx5euddoWZJTjGCCACXJVlVfHGt6RHHwiplwGztHwAjACihhIY2919d/ qHm2UWDh0fQ2qme927Kzw36KU2TscXhM8T4ACEBqmyKrs5TxRE/0tgxAqSFYqmiUaQAFoEpHC HNdv pf3TlDgRC NFauPE59rPBve6paeGd1ypfbHJGjh0THLKYePUxRVNljNtdfC dM8bqITAXJQkUp3peDxBMCcNW57vsHn22XqvpuBAAfRfRXyla9WwC6SEL4hFKOUz1VqcqumuTuEiXtB2sBnKmq15N0uf5mwzlTvG6iyqJkIxRrRs1IQbby9Miz/drXlvfUukkfj0x8PGdoMYBWe/A4SUL9m5 uJkt209ouEVUEwZKctoACAAAAHBTZzZTIQ1vmgquqolZTyUIlC0nqKBjxxSHxXw qvr1vddCDgw1tgAdsJj6beYj9gw5pIVqOLQfx2LcprH7wjzGVuaupKImSNcmKp1EAgCmy4vXgyuDBcABV9jJFESxWLBNKegjAmALP48PP5qawEL1 vx0bCHT4eokBaBoiHK2gqw4EbmSK7FUVQbIKSZQdNbVVc8YV2cVVs d8IsM5UzwuIoiiZCMtm7YRMTydMtQnR5wd0jngka4IMuC7Q9A /mIQ4rWQR7WWmEnCo984Q88VwbnqdTNVES3W5Hii3rwCwBRFlV0mqPCMDVxVZFYlWmxUSJ7uD1LLhEL306OqbA3zZgYaRRgvH U YXNEoKUYBJ8/2nfZfVrYUBxpB64qiksVLNYkKJQwowDwehmP94UkGhwUj5uKqmixJndtnHmwS/ypkVUTCt31G oWIqr7K7QSRPahkZQAwuaIQHsxCH6X0O/12NfOJh/94cAVr5soimi1JfTs66YTAMZUxeMGU1Z5xgSmyDJTRYs9KYsiTEVBtvrq MpuWcEp0HpHH9rhRxMQNLVbgxiEUALQSwyC3wvWHRV3lkQ9fylTFHeNaLURmqhTCZlLAJgsK4obh3tbCWdM9lSLki0JQmDTMqHQ/cyo6vrlWUJ6 nrPSEI76egCAohWCcAIYgBPzbM36104Z4q7RpBsVEpIWzCLAHDgqsfDVCz0jBEcFK bMkW02DAdlFjYJf7MqOqrCz0AAb4unEP3yQuFlYHQr4XZM8zOzRODaN6xeSzbbzl4ptnn5ACK7KZMESz2hMsGmUIAautYEncCZ8PCFEVWXZLNnmTF0UlM2xT27 squ7dRodZ91n5xfinvlslAhAMj7Bx f/8cUZj9YhwcPLfABtBCL8FUhbtrRJstsaqDEulaWwZnquKuQe vEZyrsqfanDNnJBxds9RPJlV2b8MaJjyq86Ah9JuECexIXVlPWMUn4Y9t0f71r5PIb9t4nhb2Rb7Zbj1R0apmzLkqJ5qrSXIB4KqiuF2JsmhXgsIZl93V3PRTaBicC/OUaTdX5qc2uCfi/4OEkYGQ MiAbkoAPkqggRi8uNQa/c5h4Vxx17DEebQomQWAKbLicQU hoJoAQfZU8MZVtYalKFd5f/eVJVhC9jsrwHQrFDA56UmPG1ze XR W7/sKCVYvDZBmtpVWx67hy44q1RE2RemaQVAFX2Kl43 n794KC4XTjMbkCuKfS dW2VTeT1iR9fSIh0kIYy0DIlaDosaI0YcA7/WB6L7n/jGUH1uhNCA5JzEFiVvarsifdVmA4OoHjcgoULoiXe14LU8cv nkeGuQBI3TApAeDBo7V1r5KGrYSEehgqwjBv/UtNjwQ3a6w44KimDiQ PyMMV/udEP692lrpjn3iXvW6AcDgEwclYQTAZBm9fxxRvR5VifUq4UiL EWd96 F P8MDgXqfkQMBYIPDHgpmmgAQvbEoyPqA6MLCxiHf6/Uqr9i/Dgg2QSAKV5Fdje9H6IlqteDc2vHnWsKvY8Oc/u7viY1IJpRAWjKBfvLQFRK0AKapwThxODV5XaXV8O6HYNrQFIJgFo3sTMSf1SvG8eE48iwrsoLl7tCOXofDQgxJAChNaA1MtDkjo17aKwEPvvW/pQZfFykeRpc9bqZYlBbSJ4xAK4qaoL1/QmhhAAFCgRoXf Ek/rOU23xKq//j3HGE6jcngPIHpdkdSTuNCmJS 989bWrXZQQnxx4mN/rhgSCJ4GoGxKAJkYFAvcK8ypEHh7gAMcrhYPlQmkNrfaSapnUeEntL4yDVQCbyK0iz7CxbAdr42RtU1iHNFUSwsxdEc0AAwEAeH6Rw6voYVOq1wXEQQXD2UKSCACvneLN2BBCgApUEAihhFICtNk9Hg4cVM4YZ5wzxpli6EccOMieGsnmTKxnIxOdrlnsnetr7BKvG/MlDYXQzdUACDEyDBBeBqKZG65OBspq6Npiafdp8UCZeKBMOFwueJTmGQMl0D5N7ZqldM9WLsyTL8iTc5yBjzg0fISQ1Mjw1Waqz0pQHED1uIjdToixNCAZBIAzLntc nyRzYYQSgUqSESgMfCDBAgIRBCgvhVxrnKFMaZwphhRCzgonhrJ6sS5IvQhN4W/d4Mr3QbgW/fTQg2AmIYCUOUlRcWWNUcsq49Ie8 IoVdciRrG4UiFcKRCWHHAWvveeanq0C7e0QXuQR28PutZhg0LnprvUFT9bIYDl90uyeYwVH I5HUtJISQujRffVKQcOA k4Jz4Jxxzu1pWXG81pBw4Iac6YEIokgFiegV9HEArqpMkZmqGE0LCREku72lGV4NcVWWhmr8ENiFbHyY0NC2YJf4p5NrerSptQUOAfPocJ/fG H v4ZeByvU3uFCgcAdXTJZtNf69Q7r2mKLqouZplr50C6e0d08Q7t47FLwRXIAKHeRwa871VaqUPMhRBDtduMssp3wEYDqcRvK 1NBFESJ6L6CLgEggkAFAYAzRWWq1zjPo3OuKl6PaAl8DhWJLc M8fTIYb6d/cYgoDb34p/RadgN/I6AyOmgxpfDhgIAQBiHnw9LXwLd1nccm6 ruzHjJvl23eLptV5Jd29k7uXTOoo29dMgGAx75x6O/9AYBzVfW4Ratd/7cOSWILAFO8BlnYiwAQURIkiwHiO0JFkYoi54wpsqp4jRAPMEVmVMD1A7Tj2l7yhPOV4ISPnwZA43afQwM0IHiHwN0ijwq4FTJjs 2j9faSqjjbgkchS/dZl 6znpuj3HFR9RU93LWpoeOVdMW JgcttIKpClO81BgPSyZwCogxVXXXGMC5EUEUqWg15oLpnHMme5kix39OJAKS1WmodcSSJgVU0IZNv7XG1tCda/TIAWkd31YQORcUvEPgxuB0ULWXfLrRPm2DrcxloG 5gdwUdXIf1029an4907H2UJzNQbIZokAuYQWAM6/bFd VHQkQKkmCKEH8e/1NwbmqeJkcZxkglEo2h3EGA5JDAOwSTL/V1S2b fjkQEcfajAAWqoBIU5RI5MPiuyfbrBVeozy5YbDaeEut x2e M7VEYIFW2OuK8nnKgpIMXria/3FwSJWqxx//6ihRBBsgqiRfG645g044ypXo AgwEx5enRnm7ZAbYQmPAJNRgAQameKHNBftsJwLxd1ldXOE7GO ETJdVeAtRisUuq7InjM7qcM8XrluI9GJCQAqDW1brEB0KoYLFS3Yd5YwAhotXOmKJ6PPF6pkxVZEJFKibg3TMk1/ZSru3VYAvBHjyYWGrAwTLhhaXOVYcTcGiHEMFio6KkeONWRcJVhaleKsRzMCDx7JAzzuI334MgSVS0JUq/PySUitQuqIqsxuk2KrJLEvDpsBjQKZM/M8bb5JhtUJ1/eKcf8Gdd0U I88sqvL3K8eE6u2yUWrOWQKgg2ZxxnDxY9XiJTYrj8GHiCYAix2eNF0KoYLVRA4zbxAIiiBZKBdnjjkMmjYPi9cQ9 E10CMDTo702KXwqO8hv 22IVAXj/1pQeeiRcvrItynbTyae9wiJIFmoKCjxKCjnwBU5nomgBOuF5Z9LKY2D96eiJNkdyeL96yBUsNgcVIhD/M5VxSD1u4nLmB7qpV1VgIAxdeL3OwncTnz/DHo1zHn8jl64xzLx0/Sk8f61ECJIVme8bCGOQxGJ9C3aUsjIe5wAzu9eKz xp0a3MECUrFQyRNFu7CFEtNpURahdvEJPVK H2AXjPBKZWDgs8OQoX68RTVV7qFRP2MGAoC0EZAVeXu78fJM13gXF2kBAtNqYShWP3gVCTHYLghiX6VISKQK4aILV4iAWB7n6qczL7s R7Dr0x4losSet969HECXJ5tDZFXPOmIzrxrSQ31wi56ZGSP34/B70tZKAX6OLA8pc5I4vUj9LVu9fDxUsks2uc3Uf5xCvQYiEEYDsTkKPIXWOmBDo0t9y 1t55wxI0c5tEUokm8Mk9Sq1o2E6D0Yx2WuoaTwShYI27Bf9axNofhmdMJDg38PvHloDjlXS2z5P3XzcPLag95RtqiIzFofx9MQQAELgklvsAY2TCjD6/vRrns6xZ8Q c0eoIBrssVWtIYRKVqee09VyAFy rbkQgD9dJgshGmYIRx/qrwAXT5raAXafEm/9PPVgWVINgDUBofqP cWluDExHFy3QZacrkLIjktugWXKP3N6jU2PYe VUEHUPQw0BIRINrue7b52BlPd3i4JuPp8tX H5oZNIVpy ESQ3x9FxeIdM1IS5SGvmEIEm51Q/YIexlT9Fw5LgO VitD36ropvxvwdc6EwMVTnBP/1jY9z9r6tyNEkKwGmq9VbwgRrbr2fVQcCYgakcKDQxT/2Sp8fzYvCIioAQAARcXivbOcZw0/u4NGECCizaanBqiKW fx5wQQgIKLLSnZTVwnAUjLFSa lD1wUqYgtvxDEUIlm83sq5cQEK36LV3EOWMqBgFRcVWh2i6tZQ6CRM7zBO /57TwwBxncxfqSjJqNUC3pRw546q QYDRBYCK0PvKJvv1jW30wivsk/ Zm1vQotlmCBFt9gSY2U0HCJFsdt3GhFWvIeasNjgCgXsuViK57sCXmv76wgUBxyqpmfv vhAgokW/MWGdS OM7uyCuv8 NWthYlxrCrn66axR92VLtuboNgHJaqzV2uIMIaJVp9pQzhk F9Ykl/VUu2RFWIsx Peg3aJLBJW5yD0znabM 4eBgG61oZwzpuqnAYb jqkIfWq7/01XuwU243MGWqe8ldu5nzNKFyZZHaaq YkGQqhkdejzXqoSt/mdEgICcO8lgWWCUTTtyLuEKPqUVfjtbOfBMrQFfwgVrTota6p4Zd3iYUN/zd0GNp399yXgyxEFGPNA lVPtrGnNjGMI1isRlicwYAQKugzezNnGAREYkQB65kT8BxvKAKHgoNeDvWi77aXl9k3H0dbCAGhgmiJQZlJ03DG9SqNM7AAECgc2cQjuGFjMp/tuT0sk1/POW90argIjlBRMMbybMZEECV95kjBcqBwEIBfXxJZHZsxMhDy1dofC3ZLn29EWwgLFSV9ngxVFZ1swbgCkNNFyO4U8l5H4fUDNhEy LaUG/6Wk5Yb1LgJFa24PkkTiBarDmPjnKmMYRAQgkGd2QX5/tNztpywFc7F5fTZhTYcjI MKNl1yBVzxvR5MNi4AnDeiLpoK9STi2GJ8Gp6rjDxpez E9OpT52oaLGZ8YGv5kKIPjLJZKwHDcFNvcP6gjC9nqasJGg0WFbh99/Yq7Dsp0kIiBa7DrdJnwckDSoAthTStb9/bz1czjNcdXOo52QAoPd4x6R/tM3pZgMAKll0q/BNdCgVBIvmyQGmqj4LmiMAAKlWGNU95KO/0Xuhpqv 3/rZur0EbSEqCKU6TBDJFEWH2miDCkD3Sy0tXnKxycZuTyXXPJPZ78YMUdJlSCdZEESL9mWynDEMAvy4/FzV0uiZo8v1R/MAgM8 B0rph0VoC81AkKzaJ4K4DiMBhhQAAj2HRG6O0fV9wgQBtZzY2dzLQogOFUFqQq8xqAHXnN/EzD8R6oGa3gsAAF5YYsO73lx0sAUdskBGFIDsDkJa20gXFti0g7JATerDvlXKqf3Y5JsNFQTa4tAsOjhT4rVgvQHpmMH7hZz6LQZJ6LogYN5OcdVhTP40G0oFQdS2Oo5zxjUeCjaiAHQdIMVuYs8QP2U33zAbHztqIaLFpvVMefrPiWhYri5kzSnxDMgCNR0EVHvJK8uxCq6FCJJVc67ASF4AABwLSURBVFvQ OEY4wkAgXP6BQ6wBD 03hq2LZJdlTjS2FIIoZK2HR cG64WEkX p5Xv8EGR5WQVVv60FEKoRVtb0HpuOMMJQJtOQmpO6Ml//PHP 0TIAvkHAV4X7FyG/qVVCKJF044PZ5pHvglB73a8U2ZUPZWovwy/Hau85OP1cVgGPZmgokXb SE403TVPMMJQGD1ZxhafMt3LPHKLuz tw4dggDMAgFc1qMFlh85C THZxsknO zlRAggsYloZoGxIYTgC59Y JZQgcBsovv B67/zGAihaN z0YAcCgzhHL/1t4/ sOcyvw0Trs/scAQZQ0fZZU086QsQTAmUkj1//4EyELFJq9K2Xs/scEQgjVsgSCMbM/EZZmg/Nyo7kDEdt9 CBgxiaptAa7/7GAEKrlZGKcM 3q4owlAPk9myoxbHGLJQAAu1Zg9z9maD2DHlNNHQQM6Mia1dib8xgYYRw LMJJ32KG5vWgmtmCsQSg3blhBSDEzOVNnCyw83Nsu3L2FBaYxwxCqKYTaegzGZZhGdRZwwDo50NCyVns/scOQomWz8do1xkykgAQyA8vAFGdIGKT3vUDdv9jjKbTRGvX60kIBnWKorMSjQ8PlQWauw2z/zFG1DII4FyrYQADCUBqG5qSFfJ6WjXXeV31Zw0/ug0LS2IMFUXtauA4V7lZhwGyHLx7TvSfvXnPybhkWLJXj0ntzYUgajevMGcctBkGMJAA5PfwaZSxvpOHNyo41bwGEE3XxzBtEDCwU2Tv33SWP8JrC3eLLgyGYw0BIFTDIEDVxhYMJADZHf0SymGbcMTRrpAaTAAOFqH71wRts0BmHQYIyv 0rkPknwX6ejt2/zVBEDUcEtPIFgwkAFkdtbh9BAA81fzEbhQATSCCoN1TwaYdBz4/T6vcV5WXrDmCU79pAhHEqKrRWwTnyS0ABLI6NNEuo5v2NgTHd6pm9SSaQwCIZrVAnKs6rIlhNAQCBdEPAJBQPwJ hcYgoOgIVbEUTjMo1UxcVU0swSgCkJJFY7XOWpAGk O7sPuvIUS7Rs/BhFNDd8zkNs2SNKtx5mct0W6ydA5cC1swigBkN9X9D0c0onFiF/b/NUTTFQI0inyNTI9m1P80G5z6X1O0i4YBQItZ4YwiAE3lf4Lj2WipKWOV PyXlhBKtZsXiDPT5YAK2kAr63xC70OgzEX3njaKySclhNDEGgYwSmtIa9sa5QxK vhsOHXQjHlknaHaFcCZLwXUPr1V7TWC 1l7hJpPT/VGu8fjuQbDAEYRAGemVldSVmw6D6I/2i2QzVAAmiTq58B2nTSKvScxhGg3JJbEApARVdwUcqfIR5YWmy6JrD EaNaQzNdl7ZARw5P5Gcf MqPYexKjnS0k8yBwzCOAhiwQRgA6QATN8p7mU4Dc1NZ 4nBfxsFSnABOc6igmVNN4ghAtDazaQal/UPupcpQVYYCoDkENKwENdvCABqJKQc4jBGADhCtaiI4cB7r8UxDN4jW38aacoYjwHpAgFDtKoHwK4ToJkSPlCI9VkHc DyMLmg3K1zMbcHAAtCcexi64ROoKUffoRMapj5Rw5skCmM5hN1/3UicYYAEahMtEdXqcsz/6EXi9HrMQPCXcQYXgNQLLSOAGJ8vgQSgjvC3NsQrLowA9EO751/wS4wB1d54X4Fp0LAoDgWgkSgcjuxB36ET2vV6sOPaHMIOA1R78UbqRsLc6kQWAH9C3nLViwKgG9o1evwSY0ANRgC6oWEGyLxjAC1BwUavF9qtCmDeDFDTdzTS6kgBGzAC0JGEudVJJgCB912VTes89IYnTJs3JwTHAJIBHANoHuiV9IIQ1FpDg6agGwlkC4klAEGzXjU1S7TFhs1eJ8ybqDEcodu806rzZZiXBLKFxBKAZiPFaJUxpGk0a/TaFVUnPb53LsUSt8swHYljC0YXgOZ/Xr8jJIwA9EO7bg9 ibU0dR8ivp5iTZx acKTMLZgdAFoJSgA pFAca8pcWIEoBuJYwvGFoBW9v8BLPYYXQnSFBrO2IMiHokm1sho A0jAN1IIFswtgBEQ4g70rjJgmMAuqFdr0e7B vNRBoKgG4kji0kqmlF6ddTchL1AyYc2q3eruHUWmaiQ uWGkaiJ4FsIeH8Y/M f1obKmi2XDnSCNdkvbpaUACaQfhb1TGT20Qdr8S0JJQtGEUAYnjHiP8fGfmaLVaF1MO5ZgsvEzDbIIAam 5j4DAAATgnG2dH15zEsgWjCEBNRWybZuNtysg3ymdMYjjTrMtjmCaqG6eqtBK8gjaYBdKcxLIFo1hX5clW3LWI9pLRziifMYnRLuYF7VaaNCqHy5p7RLS3qAAjAO1JLFswinOsPKVV3JTRDlNAmqNlr8d0X9/hstbZefijMQLQgcSyBcMIQPgIIFx7jmAlvi9ldxRMlkOOA9o1emq COBIeZRNu0kChwHOy2Wmu5u6k1i2YBgBOBXzu1Z3sxwZBIcBNIUzllhhr8E51OwUULS0TeHd2mAWSEMSzhaM4hnLjmk2dA7QvhDL3zSEMUW7kxNiuhTQvjMaat6lXVAANCThbMEoAlBRoirRLt8Yyjwimkz781EANISrmjV6ouX62kbl4BnilmN/2loTGdJVw54WknC2YBTr4gzOHIll0/RVhLzuomg1XSZBLzhTtfIplJpx/EblsONkcz92Uytj1DOgI7Pjo5FakXi2YBQBAIAzh0Pdu1Z95rqDqQh53U2XSdAHpmqYUjBh97 W7SWxsvXA80gCDOiIQYAmJKItGMjAQgtARKK3kg69MAukCZxpkK1ogJpUtref0DDwGXYODgNoQiLagoEEoGSvhuMnXQdIOClQ7OGgKhp a9SsArDhqCYCUHvSK89TrdgdijmJaQsGEoCKk6xVE0IEmYzvBquTdLkIFSDGMFXWcuZbQqiB2qeeHColdRNCaCAE6TY tgdmgWJMgtqCkQyMw/FdMZfQRgPqMRSXRIoxTNEw5qWCSbv/AMABVh O1fPAIc5zU28N 6rmJEFtwUgCAHB8Z5TtsiW2kVsg4LxAMYQzxpiGHUlCTZ2nWHO4uW21GUZxUQdWgE ExY7EtQVjOcRjYSKAWMXBPTEIiB1M8Wp6fsHEEQAArD7UgjlQmqbh4Jt6YxYoZiSuLRhLAM6eYuXHm9cuI1tDwKu5BWasK9cIjbs81OQrQR4pJ/tOa9hY 3XAeYFiRuLaguGi7EMb5JYv4UIg1GrMBICXHWVbFngOFsnaLddsNiSbkymKKnu1WAGDmjv/U8uSPbRbm5jcWz/D2H2KTl0tfrdLQFOIFYlrC4Yzs0Mb5d5X2mJ4wpI9yuYFnqPbFHT9MYeKIhVFpqqq7OUxnQWFioZrmfqzeA 955JWOJSg/lBRMX1vlfjjAXT9sSdBbcFwZnb6kFpTzhwZMQh5Dm StyzwnNyPuU5toYJABTtXmap6WExKoQkhZn0CwJftJ0jJWZKbEgN3vXSvMHW1uPGYqbNqOpBwtmA4AeAcDq6XC0dZW3wGpsK 1d6tCz3lJ7DOQT IQEXBzkWmKl6uyK1xWgJ2/wEAgHFYvJtOuSj6Hkxgn19h8PU24f214n4tZxhFAkggWzCipe352esnAOEz wGbFA/ftcK7bYm3ugxdf3wglIoWG5csTJFVWQ75zTUJFbBYq445W5slAI24ZJi UfxfkVByFl1/fEgIWzCiAJw rJYdUzOjXsqRALiq PYlnp3LvZ5qTG/GH0KoIFkFyaLKMlO8vDlPSBJKTfsAcDDbTpC9p0mzlnIsc5FpRcJnG4QKN7rGNwWzCiAACHPT97B95gj2bfqjNsy0LPnpVy1MsJILpBBMkiiBZVlZnsjXKlJIpzNvnAAWZvpY OiCoIOFpBPlgrztoiaLGcANI6DGoLhhQAgH2r5AHX20nEHkxpsbplgedAkazZGpxILCAgiBIVJR5NnRwBQUQB8OPr7fT3w9XIqwHuOkXeXy3O30m1nJAYaTXGswWDCkBNBTu0QQ43fduJ3crmBZ7ibVjUnzAQACKKVBQ5UxSvHK5OjlIJIsuThVRRbvoWN7hHbta4/QqauFH/dTNIVEwVC2YFABAIBtSzy AlA75ntoY21lJ05llagQKko2MVydHJWw x CaUWCvwAQAL5kD526WtiElZ0JixFswbgCcGKvcuawmt1JAACmwt7V3i0LPc2dKAIxJg11ckzxqvXTKFIqmHYBgMisLybbS0hhLoe6yk76/hoBKzuTg/jagpCSmUMIIYQAIbVz5/j 84EDgGSNamA2VigytC8Ud3zv/X5qzd5VXncVhrlJBSGECiIVJQKEMyZIFp2f/1I8rugafwBxsAWPQgZ3YZ sFx75Wpy7TShzofdPKuJlCySva2EoG DASb275cCBc8Y5t6dl6XBNDQgiiFaClZ3mgGuy klEXJWlUQgABw5xtwWLAHYJKtx6vicSL/SzBeOmgABAVUBV0PubBOzSRsKrghfTn2ZBP1vAESQEQRCTggKAIAhiUlAAEARBTAoKAIIgiElBAUAQBDEpKAAIgiAmBQUAQRDEpKAAIAiCmBQUAARBEJOCAoAgCGJSUAAQBEFMCgoAgiCISUEBQBCchw4xKSgACIIgJgUFAEEQxKSgACAIgpgUFAAEQRCTggKAIAhiUsIJAMHKCAQBALQFJInBCABBEMSkoAAgiA8E8LEAxDygACAIgpgUFAAEQRCTggKAIIjBENqNmDTp9sH56J60Bu8wgiCxw3bB7/77ybznR e3YiRFOu/y39197YWOKh6764o5QsGNH3w17b2bOwvxvpLWIMb7AkyBJe iybdff WAgo4ZtLrkwOr501 fvr5EqXtV7HPv3L Pz23UYmXzO/fdNeMEAyCObjc89OvbL mS6T648IM3X5l/yA0AAFLBLf976 qT/3zw9/NPszh8ICRBIPbu4259aNLQPu0cSumh1Qumv/7xmqNy4F7i XfOfP3aDgG9QVY558lfPL9GCdwbgDg6DL/u2htH9D2/Y5aTespLinduXjv789lLj3iASja73eGwCgAAtNPVj//jjgvzMxwWyhVPdWlJ8Y71P834fP7qk0EX0Yh04cjB a4Nb60OLQC2Llf89dW7Oy144qb39qgNWy2D/zrn8bG2Rtnxrvzn2KeWng06PIK5BWPN63P9TVddcXHPrjkpklx1svjApjXLPv78 11VnIhWh92qWkUAAJIx5tE/PzI0L8tpEYB5aypOFO/f8OPCj2auqrNYo4ICoD208 3PP31X1r4lC2Z8VWHtdum4q /6Y1fpiTs 3FtrBNRut7Nj89/57IfS2kbIy/eUMwAA6YLbHn3kwoP/ev6DI dc 9TDj/5y78Pv7FGBtBl/99VdD819bhF6fyQCpN0Vf3jnkV5ly7986cPj1h6jfzH5yXey/3Lb34sq/D2revSH11865GjwicTZ54bbr8k/vOd4iPZFcy996qWHJnRkh9evnP3D0QqSmtuu0wX9h/b5btbSIwA16/86ZeLLXFU5ABBHTvuOGZWL33vvx1JiS81s36PfFePvenPYeX 67 X5J8P07y2FY4dkV6/54OezQTsI6eePm/zEry8vTGWHAj6q1e4Q2K45b/9vc53HVU/vcoU6fXhzC7x7mf3v Nez1xVKpzasWDbtYDlzZrfvWNBvdO8lny3dBaDs/OSWqz4HRa011TYd2rfxbnz/nRWHmSU1M6fgoqGX3/XkqH5T73rs6/0hNNQooABoDzs845VnfzyxdWdtg56z1fPBnyeOGtxj2t5tKgCA6HDYeMm6xSsWlPu3eKH9xQNyDn730hdFB9UN3nnj/zaoX 6/9xx39L/57n413/xx7h4DNywk/ojnTbr1IueOj 76y6xDKsCy1bvpP6feMOnaz9f/r9jP4/HyPUsW7qn/i6QM M2vuigb3nlrxpEgxyh0nPL0Q9e0Oz3n/5772wqfbrwoikp9c2Sq6nsIL9u64vt5x2vb9szpm5/58tFBNw5ru DLkpDdF1vvIcOzq39atiGw8 7o/fAbT07pouxYvGrPqIEW/xeJ0 Ek3gNFyxb8GCG2AIhgbv7QtqOeefq682pWvfDYa7MPeRq3iyI0fFDF/4NWHVyxcNn22m3T5/z0xJuvjL78ym7z3tzlt5uhwDEAHeCVe7bsbOjOeE8cOcmI3emoi1ZJapqTqFWVNcHNUZREkGWFAwAoXhlEQQCxyy2/GulcN31qUYgDEKQBmnXOuTlwYsvW4jr/492 ckMJ7TKgd2qk/Lx4zq33jsk5MOfvc44G y3noBtuL7QUz3nrlRX SRyl3v2LPR aNvvnv4xKDX12Xn7qjJtHeNbC1n/kwKyzRQuLagJfcR0pWjjrmd/cd dba4KDB5KSlgbVFVVNhsQRzM0X8YIbJg5NrVjw5ptzfLw/ADBFqX0P2v66DxfN uCmvNA lLtKTlVzwz9TggKgNzSn76XdaeWWzfXdApqRkUZYdt/LR40Z2KNDis Qklq8cXt1t Gj mTYsnuPGtmhYsv2kzmX3Tq5c/FnU78vQfePRIS7aqpVkpqZ0dBZZmdOn2ZCm5ys8GZPMofdOLFr1ZKPvtkdIr4Ue13cN4MfW7J4Z3My24LVnpKakpKZnddz4PinfjM8o7zoqxUnQ7tqx4VjL0kr//nHtcHpG1764/QZ3 2uVEO1fJqWlkaEDv1GXzm093ltbeE/YHhz87vkToMH5kLFmnmrg/NQ4RFEe4ozNTWtTV7n/lfc9fg17au3Lfxun3G7/4ApIL2xdrnl8TsuVje/8t9VlfUty6JWHirNu K ByZZBfCc Gnav579dFs5BwD3z/99e86LD/171o2EVW798rWpewrvfeyimkUvfLoPsz9IE/CqjUvXVQ8ZPvmhtWc WFMiO9oUDOyeTcFNwndLad746wakHp7zaYgEPABx5uemUHXPgRCxQXjEnve//8n9DVcln1jw6ocLw/RfUvoNHZJasWTp5pDp wgIony62FMw4Z7/S7EQXnNg2UdPvzov5CBAeHPzgea0b0vVA8WHm8gn V9Dh2v/M/va r84O7PutTe 22tsS0UB0BFr54nPPvfQ aVfPvv3L4obTEjd8tFTN30EQGy5PQfc9Ku7b7vzj8 cfvAPC84wAHZ69cv33PZWm5w075njlaz7ba9clbLplWmb04b84sVfDL8wj55YP/8f/5i uhTDASQIXvrta692fuqBKU/9YyIB4KzG5bURvqGsMlxzEbqOvPo8sn3qkp3h3BYBAOD vXeSOfLFt27NX/jSXR/uDqEM6qEZL/5ncSkQKqXmdB4w9qrrHn lbdYzv/18vzfw5CmXjOqXcuaHRZsDX2kS95qpt66ZCiCk5J87euIvHp5wz2vuk7e8WhT0USOZmlEADgPOBoy6DfzHjkwpWvPPDy2hA3iJUs 9vLiw4yoKI9u1Ph2Ouu/P3rf8v54x/f2GjcbC2mgPRC6nDdM8/9oV/13D8/98rqihANgrtLdv7w5rPvLqxMGTx2YJvGXppaffrE8UqZthlx38ROB2dNm0fH/umJsc5V7z385Afrc69/8cGhmUbPNCLxgZ1Z/ bv7x4z6f5bf/O7ibfccdenxYyX7t5fFiZTLvQYeWlXtnvBslDVPwDAa06ddjGhbcd8/8wJtWW0yc52iqGbIa8 smPruo1bitav/37BVy8//vz7 xx9brlmkDVwR5Lab wA 8kff9jYbP/fgFp1fNucN/72xnpv2xEjB9rC7xjW3AAAgJWeOMOEvHbtAlJE1tS2bbLSrWE qPv0jk1b1m3csrZozXezPnz0kQ/Wkq43TxqcYWDzRAHQBZI6 LdPPT5IXfTy//31pzMRBqp4zeG9J5iQkZEe M04Btw6abBr dtf7JfO73MBK5r20cqNm5f/ 6utjr59ChP6WRREW9Tqk4d37Ny3v6L9VeO60hOrluwIk8Ch7QYPaMf3Fa0MV6AJyvaNO1y048hhXaQWX45yfP8RmdjTs2wBfpFkXDz0Ytuppct2ttz/18LL9x0oB0t6prMJ1xvW3NRD6zZXQla/MX0iaEgTsNIjByq5mJ6ehgJgcmwXTnrsquxd0/76/JKTkbOntM35/TpSz9FjASVy4jnjf3t56tqPp6 s8qssCIxRESQk1g5XPfLwTe3PLvtw9qbavDZxdOjRNdenG04yCi/qSo5v2no0bA Fly2fPecoFEy879d9g7oo0UEz 43oZeFnjh2u9m 7JGPYqAutx39evKPVWXOxfb9e2VBx/EhtAijokzZeTBhzA/CsmfXNDjnnmgfuGtG2Zd0rklI4aGAWqS4 esrAT vgGIAO2C4eP6K9cmjFibyhw/PqN7KS7au3nGJCt tf U2Xwxv3FFeotpyC4eOG9xEPfDh9tV/ukmRdfte13Yu/vvO7kwygZuvGrcLkyVMGnl5tufza810b3w7XpUNMjrVdr6G9Orbvet6wUYN7Z51d9d5fnl9c /Agyb/mj58/dIFr4V8m/G1NbcWleE5Bd0HesudIJAfs2fb2C9MK/nr7HS /ecnPP/6w/XiZLKR26NdFgLBHkcxew0dfXQ6SPSUrv/uQURf3yihf9sqcTf4H0KyBY/tIR2b uL0F/l 84P6XrsvauW13STVz5PUePvqyHp4N78wt8gZ Uk805gYAAMr r/70erc3fjf2lfcLf162ev3hMg x5/TuFsFjkpQuw8eN7sYFe0p6Xrc l43olefa q/PggtaDQQKgPbQrE7tHdTac8qTj09p3Opd8vyUx773gFJ20jt4 PWD8tIkter0/q3z//Lx9Ln VXaOvjfdM9Dz3Z/m7JQBANjx755/qd3Tdz3w7s305Ia5T7AseAkVCQ1H4Tn/ttQeXxI9tXfvrY3AXLDlQ3dEarS46erOlScbS0vs6FpOXnpULF8VOeMGerw7Vr1oP37Lp20oTxFw ZfEmqlXury08dKlqxekPwc ncdfrYsbO9R979wFgKXPVUnD6xf8u3L82ZO3tjwM4kZ8jQvuLRj5e16LFZyXOyhF4y8rqxOU7Re/bYvs3/ 8uMD76vUzK/TxqFudWjHJz38m37Rtx282UjLrlywBU2orgqTh0vWr7upyPBHS75zNHjpd0u/OUj/SgB1VN1pqR4x/wPXvpy/o9HDV0GRPK6FhJCCCFASONyGLVj/XVuhQMHzhnn3J6WFb9LRZAY46osJYQQQhsbfugFYTjagraQtpPfbvUmbeds9noQqJEK2IPo9n4IEMBNEVtIUYQ/MHjy0U9i1buRe9v77gIDCCIPGFdhw2pBAOLFoRPPcQoi3Rp4A45wzDXiSZcFWWEkIJIc1MAaEtIEkCRgAIgiAmJZIAYKYTMRURGjzaApKUNCcCiDCHFIKYCrQFJCmIWgCwwSPJR132v7lHxf5CECQuRCMA2N6RpCfKRo62gCQVzUgBYdtHkowWN2m0BSQ5wCogBEEQkxJBAIjvr9jlQZKSoLr/kC0dbQFJTiJGACSg4WPLR5IM0uDcQz8B5rMj2gKSfESZAiK1BsBUQ89shyDRw1TF1/n7/xIBtAUkefh/UYJ1eyhm7isAAAAASUVORK5CYII=[/IMG]


I'm getting lots of ideas by hacking around on the command line.  Stacer looks nice but I really want something I can use easily in a script.


I've got something like this, but I'll extend it to use [FONT=courier new]/proc/meminfo[/FONT]

```
while true ; do cat /proc/swaps | grep '/swapfile' | awk ' { SWAP=$3 ; USED=$4 } END {if (USED != 0) { printf "\n%d%%", SWAP/ (USED*100) } else {printf "." } }' ; sleep 1 ; done
``` 

Would [FONT=courier new]ps[/FONT] be the best tool for viewing memory per running process in bash?  I use it a lot but it's very complex once you get past the basics..

I think top few processes sorted by [FONT=courier new]data resident set size[/FONT] might be wiw..  

The thing is, I already know what apps are consuming all my memory: firefox, firefox, firefox and firefox.   I just need to understand how the system behaves just before approaches the critical point where it gets into a swap thrashing death spiral.  It's not that obvious, since it seems somewhat nonlinear...  

Other apps (GIMP, Inkscape, vbox) seem to just slow down when memory get's low, whereas firefox seems to struggle on, then summarily swap it's entire working set to disk, even when physical of memory used is below, say, 80%.

So, I'm thinking I'll make some logs so I can get a better picture of what happens at that moment.

Also, I was wondering if I could somehow sandbox firefox's access to memory and force it to swap sooner, maybe using [FONT=courier new]systemd[/FONT]?   I tried something like this, but it didn't work as hoped...

```
systemd-run -p MemoryHigh=1G firefox 
```

---

