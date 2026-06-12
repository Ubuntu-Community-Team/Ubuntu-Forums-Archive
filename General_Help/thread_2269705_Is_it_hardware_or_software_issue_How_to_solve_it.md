---
title: "Is it hardware or software issue? How to solve it?"
date: 2015-03-17
forum: General Help
---

### Post by Aleksandras_Onskul on 2015-03-17
Hello Ubuntu community,

im glad to be able to use ubuntu distribution again.
I just installed Ubuntu 14.04 on my HP Pavilion dv7 laptop and im having bad experience with GUI.. Doesnt matter which one I try, same problem with Unity and Gnome.
I captured a video few minutes ago, please take a 2minutes to watch it. In few words, my laptop keeps freezing like every 10 seconds and I cant change resolution to lower. 
Below the video im posting more details:

[https://www.youtube.com/watch?v=AfKOdOJnK6M](https://www.youtube.com/watch?v=AfKOdOJnK6M)


lspci returning:

> 01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] (rev ff)

And here is a picture, that may provide more infos:

[IMG]http://s1.postimg.org/vuwpio33j/screen_problem.png[/IMG]
I cannot change drivers, when I click on apply changes, it switches back to the most upper one.
Has it something to do with my gpu, drivers, or is just hardware bugged?

Thanks for replies and help.

---

### Post by Aleksandras_Onskul on 2016-01-24
Any ideas? Nobody?

---

### Post by deadflowr on 2016-01-24
My guess would be that because the first card, the hd 4XXX card can't be supported by the driver.
That you wouldn't be able to install said driver for the second card.
Since by installing the driver, it auto blacklists the driver needed for the first card.

If you disabled the first card, you should be able to add the driver for use by the second card.

That is my guess.

---

