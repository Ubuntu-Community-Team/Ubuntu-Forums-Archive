---
title: "1300 MHz CPU only at 600 MHz"
date: 2007-03-18
forum: General Help
---

### Post by leupi on 2007-03-18
I have a Dell D600 laptop with a 1300 MHz Intel processor and I noticed in KInfoCenter that the CPU is listed as only 600 MHz. I also noticed on the Power Manager that it is listed at 600 also, although I have seen it as 1300 at times. What is the reason for this discrepency?

Thanks,
Todd

---

### Post by scxtt on 2007-03-18
there are tools that regulate how much "horsepower" your CPU uses when under any type of load ... there is a simple command that will get it to run @ 1300 all the time, can't remember what it is off the top of my head ...

---

### Post by leupi on 2007-03-18
I guess that my main concern was that I had not artificially limited my CPU. I don't care if it drops to 50% if that is all that is required, I was just concerned that I had done something so that the OS only was able to use half of the CPU. I am using VMware and I set it up to use x memory and x amount of CPU and I thought that maybe it locked Linux into what was left even when VMware was not running. Does this make any sense?

Thanks for the response,
Todd

---

### Post by scxtt on 2007-03-18
i know the feeling ;)

i don't have a laptop and was under the impression that that kinda CPU-limiting stuff was basically for them ... then i installed Sabayon and apparently they turn that on by default ... so that's how i learned about it, as i saw my 2.4Ghz P4 going down to 300Mhz when it wasn't doing anything :p

did a little research and found a command to make it stay @ 2.4Ghz ...

---

