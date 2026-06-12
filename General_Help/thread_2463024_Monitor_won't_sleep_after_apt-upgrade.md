---
title: "Monitor won't sleep after apt-upgrade"
date: 2021-06-01
forum: General Help
---

### Post by jergau on 2021-06-01
Hello,

I noticed yesterday that my monitor doesn't go to sleep anymore. Whether I force it with "xset dpms force suspend" or just wait for the timeout it goes black as it should but after a few seconds (at the moment I should see the "no signal, entering power saving mode" message) it turns on again. It's like something is waking it up every time it tries to turn off. It was working just fine a few days ago and I think it started to do that after I did an apt-upgrade during the weekend.

I know it's not my monitor neither my computer since I tried with CentOS 8 that is also installed on the same machine and it's working fine so it's related to Ubuntu. I also created a new account from scratch and logged in with it (just to make sure the problem is not caused by a setting on my regular account) and it does the exact same thing. I am using a Ryzen 3 3200G cpu on this computer (with the HDMI motherboard output) so my guess would be that the Vega 8 graphics driver got messed up during the last apt update. Is it a likely explanation? Is there anything I can do beside hoping that a further update will fix the issue?  Thank you very much for any advice!

---

