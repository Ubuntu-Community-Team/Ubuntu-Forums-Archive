---
title: "Problem with &quot;CW trainer ALDO&quot;"
date: 2014-08-12
forum: General Help
---

### Post by Avondster on 2014-08-12
I have a problem with the ALDO program. If I select option 2 (koch) I get the following error. Anyone have any idea what goes wrong.

marc@marc-MS-7621:~$ aldo
Aldo 0.7.6 Main Menu
    1: Blocks method
    2: Koch method
    3: Read from file
    4: Callsigns
    5: Setup
    6: Exit
Your choice: 2

Keying speed: 20 wpm
About to start keying. Get ready...
Letters in lesson: k m r s u a p t l o w i . n j e f 0 y , v g 5 / q 9 z h 3 8 b ? 4 2 7 c 1 d 6 x 
Segmentatiefout (geheugendump gemaakt)
marc@marc-MS-7621:~$

Marc

---

### Post by oldos2er on 2014-08-12
Moved to General Help.

---

### Post by steeldriver on 2014-08-12
There is an outstanding bug against the 64-bit version (although fwiw I downloaded the 32 bit version and that does the same - it also segfaulted when I tried the 'from file' option)

[https://bugs.launchpad.net/ubuntu/+source/aldo](https://bugs.launchpad.net/ubuntu/+source/aldo)

Just seems to be generally flaky unfortunately

---

