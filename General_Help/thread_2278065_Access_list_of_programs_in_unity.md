---
title: "Access list of programs in unity"
date: 2015-05-13
forum: General Help
---

### Post by Revolutionary101 on 2015-05-13
Hello there everyone,

I have been a long time user of Ubuntu and usually I can troubleshoot my way out of a problem but today I ran into an odd issue. Yesterday, I had been using a program called scalpel for some file recovery on a 4 GB flash drive. It was my first time using it, and it seemed to cause my SSD to run out of space. Anyways, I gave up on scalpel.

Today, I found out that my root partition was full (I have a partition for home and for /) after using this program. Before I used it I had about 8 GB free on the / partition. With this happening, I can no longer search for any applications in Unity. I would use terminal to launch programs to help clear space on / but I can't since terminal isn't in my Unity bar. Is there any way I can for Ubuntu to show an application list or launch commands without using terminal? Thanks!

---

### Post by deadflowr on 2015-05-13
ctrl + alt + T  
should launch a terminal.

Alternatively, if you can open Files/Home Folder,(aka nautilus), you can go to the applications folder in 
/usr/share/applications
and launch whichever app you want from there.

---

### Post by Revolutionary101 on 2015-05-14
Thank you for the help!

For some reason ctrl + alt + T didn't launch a terminal. I instead was able to open a terminal from nautilus by using the "open in terminal" option. From there, I was able to solve my issue and free up space on my / partition.

---

