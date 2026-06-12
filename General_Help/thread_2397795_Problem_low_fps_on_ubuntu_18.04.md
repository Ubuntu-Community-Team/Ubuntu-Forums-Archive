---
title: "Problem low fps on ubuntu 18.04"
date: 2018-08-03
forum: General Help
---

### Post by levanius on 2018-08-03
hi,

I just installed Ubuntu 18.04. Just say this is my first contact with Linux OS. The installation is done well buy i have one problem: i have very low fps. I configure Nvidia driver and select it. I read lot about Nvidia driver configuration and I think everything is configured well but still can't get fps.
Please help.

ty

---

### Post by Autodave on 2018-08-03
What Nvidia driver did you load and where did you get it from?

Some specs on your machine would also be helpful.

Lastly, what game/program are you seeing the low FPS on?

---

### Post by levanius on 2018-08-04
> **Autodave said:**
> What Nvidia driver did you load and where did you get it from? driver 390.

Some specs on your machine would also be helpful. MSI GL62 6QF. Graphics: Nvidia GTX960M and intel HD 530.

Lastly, what game/program are you seeing the low FPS on? I only try on CSGO but also I can see my desktop is not smooth.

---

### Post by twily2018 on 2018-08-04
Run: ```
lshw -c video
```

Tell us which driver it is. There will be a line with "driver=yourdriver"
With Nvidia you might need to use the proprietary driver.

---

### Post by Notsgnik on 2019-02-04
we are lot of people having this problem, in ubuntu 16.04 everything was working smoudly.
nvidia driver 415 with modeset on 
cs:go and other games are doing the same fps up and down slope :/

---

### Post by Autodave on 2019-02-04
Where did you get the driver from?  We need to know that!  And we are still waiting for some specs on your machine, especially the Nvidia card.

---

### Post by coffeecat on 2019-02-04
@Notsgnik, you have your own thread open about your problem. 

Since the OP has not logged in since the day after they started this thread 6 months ago, it seems unlikely they will be back. @levanius, if you do come back and want this thread re-opened, please use the report post button in your own post to send a request to the staff area.

In the meantime - thread closed.

---

