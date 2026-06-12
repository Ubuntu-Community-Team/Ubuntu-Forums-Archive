---
title: "random freeze in 6.10 and 7.04"
date: 2007-02-26
forum: General Help
---

### Post by hoyaabc on 2007-02-26
I used 6.10, but I got freeze many times,
so I upgraded 7.04.
same happened.
symptom is randomly, freeze(step by step whatever program)
if I push button Ctrl,Alt and Backspace, it showing

Ata1: port failed the respond
Ata1.00: revalidation failed(errno=-2)

after rebooting by push the power button, it showing error

checking file systems.
fsck ~~~~~~
replaying journal
ata1.00:execpting Emask 0x0 SAct 0x0 serr 0x0 acting 0x2 frozen

my understanding is hard drive is going crazy randomly.
and can't fix it easily.
my mount drive is sda1. why it talking about ata1?

My computer is Dell XPS m140(laptop).

hard drive is Samsung mp0603h(ATA) 60g


I read my computer spec again, but I couldn't find any sata, or scsi
I am not sure my computer using sata, scsi

my ubuntu hardware infomation showing
my computer using sata controller, and scsi hard drive. is it correct?

I searched same symptom, I found a lot. but mostly no solution.
I don't want to leave ubuntu. somebody help! plz.

---

### Post by EriktheUnready on 2007-02-27
I have had the same sort of issue.(with centos4.3) however it turned out to be my drive that started failing.
replace the sata cable & drive & see what happens.

hope this helps.

---

### Post by hoyaabc on 2007-02-27
Thank you for helping.
but my computer is laptop, so I can't do much with hardware.
I belive my hard drive is good condition, I check fsck, and several test by others.
leptop is just came from Dell,
Ubuntu is very attractive system, but this is really big deal. I had to format several times.
it is not only me but many people in this forums.

yesterday, auto updated some application. and now, if I trying start fire-fox, always freezing.
good thing is it is not randomly now.

I am doing test ubuntu. without firefox, Will be alright, or not.
my computer has only ubuntu, and I install just basic programs.
so I will figure out soon. I hope.

---

### Post by bulldog on 2007-02-27
Try the stable 6.06 instead of 7.04,which isn't even a Beta yet.

Edgy should do it too,but to be sure,install Dapper Drake 6.06.

---

### Post by hoyaabc on 2007-02-27
I am almost give up 7.04, 6.10
so if my last test(without firefox) gonna fail, then I will go 6.06.
so far about 10hours past without freeze.
problem was firefox???

---

