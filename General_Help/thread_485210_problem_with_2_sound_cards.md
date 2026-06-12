---
title: "problem with 2 sound cards"
date: 2007-06-26
forum: General Help
---

### Post by Michalxo on 2007-06-26
Hello! Iam using feisty. I have 2 soundcards. Integrated AC'97 and additional sound blaster 5.1 live! 24bit. Feisty won't recognize my SB 5.1 and I dont know, where's the problem. In dapper everything worked well, in feisty not :(     and 2nd problem, computer refuse to shutdown ! :)  it doesnt want to shutdown (ATX power). I haven't seen this yet :)   feisty is very nice :)) 
 Can anyone help me?! please

here's some info:
[http://pastebin.ca/589114](http://pastebin.ca/589114)

---

### Post by awakatanka on 2007-07-01
> **Michalxo said:**
> Hello! Iam using feisty. I have 2 soundcards. Integrated AC'97 and additional sound blaster 5.1 live! 24bit. Feisty won't recognize my SB 5.1 and I dont know, where's the problem. In dapper everything worked well, in feisty not :(     and 2nd problem, computer refuse to shutdown ! :)  it doesnt want to shutdown (ATX power). I haven't seen this yet :)   feisty is very nice :)) 
 Can anyone help me?! please

here's some info:
[http://pastebin.ca/589114](http://pastebin.ca/589114)Here is what solved sound for me : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard)

---

### Post by crispy_420 on 2007-07-01
Why not just disable the AC97 card in bios? There is no need for two sound cards.

---

### Post by awakatanka on 2007-07-02
> **crispy_420 said:**
> Why not just disable the AC97 card in bios? There is no need for two sound cards.
On some boards they sometimes still show in the OS even when they are disabled in the bios. I had one board where that was the case.

---

### Post by Michalxo on 2007-07-04
> **crispy_420 said:**
> Why not just disable the AC97 card in bios? There is no need for two sound cards.

nope, it aint working, AC works even when its banned in bios :) ...and  FF cant detect my SB :((

 sudo asoundconf list
Names of available sound cards:
V8237
:(

---

