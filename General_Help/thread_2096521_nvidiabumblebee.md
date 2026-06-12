---
title: "nvidia/bumblebee"
date: 2012-12-20
forum: General Help
---

### Post by IIMOW on 2012-12-20
I've spent the better part of the last couple of hours swimming around using the search tool but I just can't seem to solve my issue. I have a newly purchased HP Envy DV6 with an nvidia gt 630M which I slapped 12.10 on, so using the help of these forums I've fixed the main issues (Beats audio not working, wireless issues, brightness issues) but I just haven't been able to figure out what's going wrong here in regards to the hybrid graphics.

It seems the most common solution to the first error I get,

[ 2112.319456] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 2112.319535] [ERROR]Aborting because fallback start is disabled.

is to go into etc/bumblebee/bumblebee.conf and do the two following things:

1) Replace Driver with Driver=nvidia

2) Replace KernelDriver=nvidia-current with KernelDriver=nvidia

This seems to work for some people.  For myself however, I wind up with a new error:

[ 2959.099341] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 2959.099390] [ERROR]Could not connect to bumblebee daemon - is it running?

I'm at a total loss as to what to do next. I've un-installed and re-installed, did every update under the sun and I just wind up going in a huge circle. If somebody could kindly point out the proper topic (because I assume this has to have been at least answered once, I just can't find it) it would be very much appreciated.  Or, otherwise, if you need more information to help me out, I'll gladly provide it.

Thanks so much.

---

