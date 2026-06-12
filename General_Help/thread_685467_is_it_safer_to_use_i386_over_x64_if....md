---
title: "is it safer to use i386 over x64 if..."
date: 2008-02-02
forum: General Help
---

### Post by jarthel on 2008-02-02
I need to a software that isn´t available in the repository. I am thinking of using X64 but I´m wary I might encounter problems. I was speaking to someone in IRC recently and he mentioned to stay away from x86 when usin x64.

Any ideas?

thank you very much

---

### Post by ~LoKe on 2008-02-02
No problems. **Most** 32bit apps will run in a 64bit environment.

---

### Post by SpiderGorilla on 2008-02-02
Speaking as a veteran 64-bit user (because my week of use counts as ten years of 32-bit with all I've had to do), I can say this for certain:

64-bit Ubuntu is awesome. But you're going to have problems (like with any 64-bit OS) with the following:

Drivers -- Printer, scanner
Plugins -- DVD, MP3, Flash

They CAN be made to work, but they'll require some work. I keep hearing rumors that 8.04 is going to have drastically improved 64-bit support. I'd say go ahead and throw the 64-bit on your system and give 8.04 a try when it comes out. If it works, great! If not, well, you can always reformat...

---

### Post by ~LoKe on 2008-02-02
> **SpiderGorilla said:**
> 64-bit Ubuntu is awesome. But you're going to have problems (like with any 64-bit OS) with the following:

Plugins -- DVD, MP3, Flash

I had no problem whatsoever with these.  I got the w64codec, libdvdcss2, and flash installed with any problem.

---

### Post by jarthel on 2008-02-02
> **SpiderGorilla said:**
> 
Plugins -- DVD, MP3, Flash


any suggestion or maybe a link on how to get dvd/mp3 to work?

thank you :)

---

### Post by PmDematagoda on 2008-02-02
```
Plugins -- DVD, MP3, Flash
```

I did not face any problem, just installed the right packages from the repositories then I was good to go:).

```
Drivers -- Printer, scanner
```
Actually, I did not face any issues with my HP OfficeJet 4255 since HPLIP contained the drivers, so if you have a similar printer then you should not face issues at all.

---

### Post by PmDematagoda on 2008-02-02
> **jarthel said:**
> any suggestion or maybe a link on how to get dvd/mp3 to work?

thank you :)

For DVD's, add the Medibuntu repositories by following the instructions given [here]("https://help.ubuntu.com/community/Medibuntu"). And then execute:-
```
sudo apt-get update
```
and
```
sudo apt-get install libdvdcss2
```

Concerning your mp3 support, just open an mp3 file in Totem(Not sure about another player) and install the packages that are suggested.

---

### Post by SpiderGorilla on 2008-02-02
Oh yeah, once I figured out WHICH were the correct packages, I got it all running swimmingly. It was figuring it all out that made me try to stab my forehead with a drafting compass...

Frankly, all-in-all, 64-bit is exceedingly awesome, far more stable and very handy. I couldn't get my scanner to work, because it's a PIXMA MP130, which is like the ONLY unsupported Canon printer/scanner combo in the whole of the world that Linux doesn't support. It was just my bad luck, really.

---

