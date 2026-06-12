---
title: "Ubuntu Dapper intermits frequently... RAM problem?"
date: 2007-01-29
forum: General Help
---

### Post by altonbr on 2007-01-29
My sister has an old Hewlett-Packard with 256MB of DDR 2700 RAM and a Celeron. I've told her I will go out and buy her more RAM because of how her computer can't handle the multi-tasking, but she doesn't want to spend the money.

Now it seems to shutdown every so often. I'm guessing that the OS is running out of RAM and it has no other choice but to shut down... although, logically I would assume that it would just freeze. 

She seems to listen to music on Rhythmbox, use Firefox for her course, Gaim to talk to classmates and OpenOffice for her work. She's in her post-grad Teacher's College, so I'm her work is really important, but she doesn't seem to mind the intermittent shutdowns. I think that's rather silly and would like to help her out.

My father has the same type of machine, except I replaced his RAM with 2 new 512MB DDR 3200 sticks. Never had a problem since. 

I've ran Memtest86+ a couple times, and no errors ever show up.

Also, she doesn't have to reset the breaker at the back of her power supply ever, so I don't think it's the power...

Many thanks!:)

---

### Post by bettlebrox on 2007-01-29
How much swap space is there?

---

### Post by altonbr on 2007-01-29
1GB. Neither the RAM nor the Swap is ever full though.

---

### Post by bettlebrox on 2007-01-29
Could be a hardware problem, such as it's overheating or a drive is failing?

---

### Post by altonbr on 2007-01-29
Any ideas on how I can test this? I've never had a computer overheat, and I only know as much as the problems I've already solved.

---

### Post by bettlebrox on 2007-01-30
You can check the logs to see if there are errors message about the drive(s). You can use smartmontools to check and monitor the drives for errors.

---

### Post by Ramses de Norre on 2007-01-30
If the cpu's heatsink feels very hot while running it is probably overheating. Your mobo shouldn't feel really hot neither, but a little warm shouldn't be a problem.

---

