---
title: "Conky and network correct drive space"
date: 2015-09-19
forum: General Help
---

### Post by alain.roger on 2015-09-19
Hi,

I have a NAS with 4 TB HDD and i would like to know the respective size for some shared directories.

e.g. /perso and /work have different size GB used) however my conky script return the same size for both.
       [FONT=monospace][COLOR=#000000]${color #ffc000}/storage ${color #888888}$alignr${fs_used /media/work} [/COLOR]
${color white}${fs_bar 6 /media/work} 
${color #ffc000}/perso ${color #888888}$alignr${fs_used /media/perso} 
${color white}${fs_bar 6 /media/perso}

both /media/work and /media/perso are mounted at the boot session automatically.

So why is my mistake ? How can i get to correct size of space used by each directory ?

thx[/FONT]

---

### Post by deadflowr on 2015-09-19
Duplicate post.
See
[http://ubuntuforums.org/showthread.php?t=2293880&p=13352283#post13352283](http://ubuntuforums.org/showthread.php?t=2293880&p=13352283#post13352283)

Thread closed

---

