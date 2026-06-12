---
title: "boot up speed help :D"
date: 2006-10-30
forum: General Help
---

### Post by louistan3 on 2006-10-30
hey guys.. can u guys give some suggestions on how to lessen my boot up time? ive done some stuff but its still not enough to get me on the low 20's

here's my bootchart

i have a sony vaio sz laptop

its an intel core duo.. thanks in advance! :D

---

### Post by iamhugeinjapan on 2006-10-30
Are you able to give yourself a static ip? Also comment out the interfaces you don't have in your /etc/network/interfaces  file. For instance I had wireless interfaces when I don't have wireless.

What have you done so far?

---

### Post by louistan3 on 2006-10-31
hmm.. ive done a CFQ thing.. lol dont knw wat its called.. and noatime, writeback.. uhmm.. turn off some services with sysv-rc-conf..
i thnk thats pretty much it... i really want a boot time on the low 20's

pls. help :D

---

### Post by Tempurite on 2006-10-31
31 seconds!!!

I have to wait to wait 2+ minutes until Ubuntu boot,

and you want to speed up your boot up...

---

### Post by louistan3 on 2006-10-31
well.. its coz i saw some people that have like 20s boot times..

and my laptop is fairly new.. so i expect more out of it.. :D

---

### Post by iamhugeinjapan on 2006-10-31
Disabling the boot splash should also save a couple of seconds. Took 3 seconds off my boot. Got me to 20 seconds exactly.

Good advice about reprofiling your readahead list in this thread.
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by louistan3 on 2006-10-31
wow! 26S!!! WOOH! thanks iamhugeinjapan! i thnk.. lol.. i did what u said and erased the other interfaces in /etc/network/interfaces and it shaved off 5s.. 

im goin to try that reprofiling thing.. thanks! :D

---

### Post by louistan3 on 2006-10-31
heres my new bootchart btw..

---

### Post by iamhugeinjapan on 2006-10-31
Good stuff!

---

### Post by louistan3 on 2006-10-31
i need more! i want it to be below 25s hahaha... help people! help me.. :D

---

### Post by dcstar on 2006-10-31
> **louistan3 said:**
> i need more! i want it to be below 25s hahaha... help people! help me.. :D

If you really know what you are doing, you can compile your own kernel turning off all the options (and hardware) that you don't need.

A kernel "tuned" to your specific needs will load faster than the generic ones that are full of code (and detection tasks) for things that your particular environment doesn't have.

And as a good side-effect, the kernel uses less memory.

You do have the issue that adding/changing hardware also requires a recompiled kernel to suit the changes.......

---

