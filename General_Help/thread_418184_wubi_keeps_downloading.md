---
title: "wubi keeps downloading"
date: 2007-04-22
forum: General Help
---

### Post by slipperhead on 2007-04-22
i just downloaded wubi and after 1 and a half hours it finished downloading the iso.
then it started redownloading all over again!
i checked the wubi folder in c drive and it says partial file (the 2nd download is at 60mb) despite having allready downloaded it

any ideas?

---

### Post by Michi05 on 2007-04-22
well, I have the same problem, but I can't help... It seems to be a problem with the hash since that is the last thing that is done before the message: "Retrying in 5...". Maybe something can be made with the "config.ini" file... but I don't really have any idea of what to do or how (at least without ruin it...). Guess that to simply deactivate the hash check (don't know f it can be done) isn't a great idea, right? :P

---

### Post by Antimethod on 2007-04-22
Yes it is  a great idea and i think it works...at least it worked for me
edit C:\wubi\config.ini
delete the line that begins with "ddlsha1"
hope it works ;)

---

### Post by slipperhead on 2007-04-22
thanks, will give it a go with editing the config file and hopefully it will work this time

---

### Post by ecology2007 on 2007-04-22
> **Antimethod said:**
> Yes it is  a great idea and i think it works...at least it worked for me
edit C:\wubi\config.ini
delete the line that begins with "ddlsha1"
hope it works ;)

That's a nice try again. It should do the job for today. There will be a new exe later today or tomorow.

---

### Post by Michi05 on 2007-04-22
thx a lot Antimethod!!! it worked perfectly. I thought that if hash didnt match,  there was something wrong, but everything seemed to went fine.
2 out of 2... your turn slipperhead, hope that it'll work to you too, byeee :)

---

### Post by slipperhead on 2007-04-22
i,m having to redownload again (i lost the bap and deleted it all!)

so in about an hour and a half i'll post back if it works!

ive deleted the line in the config file so heres hoping!

edit : or 3 hours as download speed has dropped to 59kb :(

---

### Post by slipperhead on 2007-04-22
well, no luck. the download and reboot went ok until i got the error "could not load cd installer components"

alt/f4 give the error "cannot access tty, job control turned off"

so for now i'm stumped.any ideas?

---

