---
title: "Live CD x86 problem"
date: 2005-05-06
forum: General Help
---

### Post by Goz on 2005-05-06
Hello, I've just received my pressed Ubuntu CD's and I've got a little problem. The Live CD's seem to have a bad package called casper-udeb. The packages don't pass the verifying. I've tried with different live cd's and drives. What seems to be the problem ?

---

### Post by dwight on 2005-05-07
I've got the same problem. This morning I received my nice and shiny cd's, but I cannot boot from any of them (live cd's). It complains about casper-udeb not passing the verification test. I was hoping to deal out most of these cd's to my friends so they could try out linux, but if it won't even boot then i'm stuck with a bunch of coasters. Hope the cd's for installing are ok.

UPDATE: I did some md5sum tests and none of the live cd's passed. It doesn't say that verification has failed, the discs are simply unreadable from a certain point onward. Well, at least the installation cd's pass the test.

---

### Post by DVSoftware on 2005-05-07
[QUOTE=dwight]I've got the same problem. This morning I received my nice and shiny cd's, but I cannot boot from any of them (live cd's). It complains about casper-udeb not passing the verification test. I was hoping to deal out most of these cd's to my friends so they could try out linux, but if it won't even boot then i'm stuck with a bunch of coasters. Hope the cd's for installing are ok.

UPDATE: I did some md5sum tests and none of the live cd's passed. It doesn't say that verification has failed, the discs are simply unreadable from a certain point onward. Well, at least the installation cd's pass the test.[/QUOTE]
 same problem here 
i've received my cd-s yesterday and tried to boot and all seemed to be fine, but suddenly casper-udeb corrupted.
tried second cd, same problem. i pressed "NO" on retry question and messed with options and managed to boot it. 
I've rebooted then, and, very strange - CD works without problems. Can somebody from Ubuntu explain this?

i'm afraid to try another cd now, i will rather wait for an answer from Ubuntu.

---

### Post by dwight on 2005-05-07
[QUOTE=DVSoftware]i pressed "NO" on retry question and messed with options and managed to boot it. 
I've rebooted then, and, very strange - CD works without problems. [/QUOTE]
So you got the live cd to work eventually? What options did you use for that? I only tried acpi=off because i thought that the problem was with loading some acpi modules, but that didn't help anything. On a side note, My cd drive makes very strange sounds when it gets stuck with the live cd. Never heard it do anything like this, though i've had my share of unreadable cd's. Anyaway, what options did you use?

---

### Post by DVSoftware on 2005-05-07
[QUOTE=dwight]So you got the live cd to work eventually? What options did you use for that? I only tried acpi=off because i thought that the problem was with loading some acpi modules, but that didn't help anything. On a side note, My cd drive makes very strange sounds when it gets stuck with the live cd. Never heard it do anything like this, though i've had my share of unreadable cd's. Anyaway, what options did you use?[/QUOTE]

well hard to say,
when it stucks, it asks if you want to retry. You answer No, and you have many options. I have tried all of them, and then there was something like empty RAM, and something like Enter Preinstalled System. When i clicked that, system booted, but i can't remember what was before that, and i can't repeat the process because it's booting correctly now  :roll:

btw, what cd rom drive you have
mine is LG DVD RAM, and it also make strange sound, and stop spinning.

---

### Post by dwight on 2005-05-07
I have a Samsung dual DVD-CDRW drive, and I have never heard sounds like the ones it did this morning. Once a cd was shattered to pieces in an older cd drive of mine, but ubuntu's  live cd sounded even more ominous than that. So you say everything is fine now. What happens if you do a md5sum test on one of the cd's . 
For example if you type 
```

md5sum -c md5sum.txt

```
in the directory where the live cd is mounted. Does it pass the test?

---

### Post by DVSoftware on 2005-05-07
./pool/main/c/casper/casper-check_0.62_all.udeb: OK
./pool/main/c/casper/casper-udeb_0.62_all.udeb: OK
./casper/filesystem.cloop: OK
./casper/filesystem.manifest: OK

it passes the test
i've taken another cd, not the one that worked

---

