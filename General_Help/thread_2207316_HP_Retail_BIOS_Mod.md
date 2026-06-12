---
title: "HP Retail BIOS Mod"
date: 2014-02-23
forum: General Help
---

### Post by Jesse_Jones on 2014-02-23
[COLOR=#000000][FONT=arial]Anybody know of a tool I can use to mod an HP retail BIOS? I want to OC my laptop, it has really good cooling (my CPU is usually 20-30 degrees C). I'm nt afraid to brick this laptop as I know somebody who could reprogram the eeprom, but I'm looking for a tool to do it myself on either Win7 or Ubuntu (preferably Ubuntu). It's an HP NC6400 notebook, BIOS ver F.0B
[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-02-23
Do some research on your specific CPU.  Some CPU's are hardwired for a given front side bus speed and multiplier, so changing them in BIOS has no effect.  Otherwise, you would need to collect some pieces:  A flasher tool provided by HP which is either DOS-based or Windows-based.  Some newer BIOS to use as a reflash option.  Then back up the existing BIOS using the flasher tool.  Install *hexedit* or some other byte-level tool and browse through the BIOS to see if anything CPU-related jumps out.  With your research, determine what the current multiplier is (say 14X). If you find a clock multiplier setting (example a string with "14X"), then you can try changing it (a small amount say 16X) and reflash.  Run benchmarks to see if there is any performance difference.

This is a tedious, hands-on process and breakage is guaranteed.

According to my research, you have an early Intel Core Duo, which is not a bad processor, but may have limited overclocking, due to the new design.  [http://www.cnet.com/4520-6022_1-6410042-1.html](http://www.cnet.com/4520-6022_1-6410042-1.html)

Overclocking works best on CPU's that have been around a while and are near the end of their production life--before the new stuff comes out.

---

### Post by Jesse_Jones on 2014-02-23
That's exactly what I have, an Intel t2400. And I have yet to find what I'm looking for on the internet, but thanks! I'll try that

---

### Post by tgalati4 on 2014-02-23
Start your search on the overclocking forums and see if others have had luck with the T2400 and the stability with overclocking it.  If you can't find any, then that would be your first clue.

---

