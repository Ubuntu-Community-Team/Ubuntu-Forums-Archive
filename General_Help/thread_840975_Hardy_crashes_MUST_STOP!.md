---
title: "Hardy crashes MUST STOP!"
date: 2008-06-25
forum: General Help
---

### Post by lost09 on 2008-06-25
I've got a Toshiba laptop running Hardy, which has crashed 7 times in the past hour. From what I've read, many Hardy users are suffering from similar inexplicable crashes. I have far more than way too much work to do, and thanks to Hardy's apparent instability, I am dangerously behind schedule... if this continues, I may be forced to switch back to Gutsy. Please help!

---

### Post by ajmorris on 2008-06-26
hi there,
Can you post the ouput of sudo dmesg
and the contents of /var/log/syslog.


AJ

---

### Post by jimv on 2008-06-26
Try switching to the RT kernel (only if you're using the 32 bit Ubuntu).

sudo apt-get install linux-rt

---

### Post by spen25 on 2008-06-26
I'm running Hardy on a Toshiba Laptop and it's been rock solid. Not sure if you're running Compiz, cause I was getting lockups under compiz till I changed my Nvidia PowerMizer state to 2.

---

### Post by snkiz on 2008-06-26
How do you change the powermiser option? I can't even install Nvidia-settings for some reason and when i used it before i didn't have the option to change powermiser. I was having the crash sickness to, i ended up downgrading to gutsy and declocking my board to solve the issue

---

### Post by kevdog on 2008-06-26
The rt kernel didnt work in my case -- this is still an open bug in launchpad -- go back to Gutsy for time being.

---

