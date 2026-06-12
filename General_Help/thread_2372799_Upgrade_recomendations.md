---
title: "Upgrade recomendations"
date: 2017-09-28
forum: General Help
---

### Post by cee2 on 2017-09-28
I hooked up my windows 7 hdd with sisoft sandra and did a overal computer test and recomendations.
it gave me a 64 page computer report  that was greek to me with no easy conclusion or idea what the weakest point of my system is.

Im considering major upgrades since last 3 summers ive had reliability problems with screen freezing and going grey for a few seconds then usually comes back 10 secs later.
I eliminated a probly faulty ram stick and am now down to 1 4gb stick .
memtest hasnt shown this last stick to be faulty yet with 11 hr overnight test

So what in my signature seems to be the obvious weakpoint?
does lack of ram, matter in a ubuntu system used mostly for triple display video/audio on youtube? I watch tv shows, movies youtube   on 60 inch screen, youtube and surfing on 34 " and emails etc on 23 "

is my 020 kooler likely to be compatible with latest Amd mobos and cpus?

---

### Post by ian-weisser on 2017-09-28
For just browsing and YouTube, I get great performance with a mere $200 laptop with a cheesy little Atom CPU, even cheesier on-board graphics, and 4GB of RAM. And it barely warms up.
How much do you want to budget for this upgrade?

---

### Post by cee2 on 2017-09-29
yeah i do exactly that same thing with my laptop in my bed sometimes before going to sleep.
If i ever downsize to just renting a room this may become my primary computing experience but as long as i have my own place i will make use of all my big screens.
Would 500 cdn/400usd get me a new mobo and ram and cpu  with good onboard sound and still be compatible with my 750 watt antec psu, antec 920 liquid cooler?
is my cpu still used in any new mobos?

I cant believe amd has a 1400 cdn cpu which im supposing needs a new 500cdn mobo, ddr4 ram , probly new liquid cooler as well?
I cant afford a ferrari in real life so not getting that either :-(
gotta be the coolest name for a Cpu i can remember though , lol
THREAD RIPPER!

---

### Post by Impavidus on 2017-09-29
Screen freezing and going grey for a few seconds is a typical symptom of shortage of memory. The computer begins to use swap, which makes it slow. 4GB should be enough ram for most purposes, although it's not very much, and web browsers these days can fill any amount of memory if you open enough tabs. Use task manager, system monitor, top or free to monitor your ram usage (interpreting results isn't always trivial). Is it using swap? Then add more ram or use less of it.

The tasks you describe should work fine on a laptop with specs far below your computer.

---

### Post by cee2 on 2017-09-29
heres the ram and swap file info
to me it doesnt look like a ram or swap problem as i had a youtube tab running , twitter, and 8 other firefox tabs open at the time
am i right?
it was still freezing when i had 2x4gb sticks so i really wanna know what problem is before i buy 2x8gb sticks only to find i still have the same problem and now stuck with 200 bucks worth of ram that will be useless in a mobo/cpu/ram upgrade


GA-990XA-UD3:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           3.9G        2.4G        264M        104M        1.2G        1.1G
Swap:          8.0G        1.6M        8.0G
curt@curt-GA-990XA-UD3:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           395M  6.4M  389M   2% /run
/dev/sda1       103G   48G   50G  50% /
tmpfs           2.0G  1.4M  2.0G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop2      145M  145M     0 100% /snap/brave/4
/dev/loop4       82M   82M     0 100% /snap/core/2898
/dev/loop0      153M  153M     0 100% /snap/brave/5
/dev/loop3       82M   82M     0 100% /snap/core/2774
/dev/loop1      158M  158M     0 100% /snap/brave/6
/dev/loop5       82M   82M     0 100% /snap/core/2844
cgmfs           100K     0  100K   0% /run/cgmanager/fs
AFS             2.0T     0  2.0T   0% /afs
tmpfs           395M   60K  395M   1% /run/user/1000

---

### Post by cee2 on 2017-09-29
[https://www.ncix.com/detail/asrock-n68c-gs4-fx-95w-socket-40-110264.htm](https://www.ncix.com/detail/asrock-n68c-gs4-fx-95w-socket-40-110264.htm)

i guess if its a mobo problem this would be a cheap replacement?
anyone got experience with this mobo for quality and compatibility with my system?
Would the XFAST LAN and RAM  work on a ubuntu system?

---

### Post by cee2 on 2017-09-30
i now have Brave running and a similar thing happens to brave independantly of firefox, also firefox freezes as well independantly of brave.
Can anyone help me lock down if this is a faulty hardware problem, lack of hardware as in ram or cpu power, maybe psu power?
or is it a ubuntu problem fixable with a reinstall.
Im skeptical its ubuntu as i think ive reinstalled since this started happening a couple yrs ago

---

### Post by cee2 on 2017-09-30
ok i figured out how to do a swap file enlargement.

---

