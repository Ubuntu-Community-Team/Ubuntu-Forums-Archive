---
title: "Ubuntu 12.10/64bit failing to load"
date: 2012-11-06
forum: General Help
---

### Post by gmseed on 2012-11-06
Hi

I've been using Ubuntu 12.10/64bit for a couple of weeks and it's been ok. 

When I boot up now I just get a purple screen.

I'm sure this is a direct result of doing an update yesterday.

The problem started earlier today when I tried to run the Chromium Broswer by clicking on the icon on the left-hand-side panel, which was installed using the "Ubuntu Software Centre".

If I opened a terminal windows and typed:

$chromium-browser

I got:

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 460: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

That was the last time I booted, and now I just get a purple screen.

Graham

PS. I wish I'd never installed the 12.10/64bit on the laptop but the Samsung Chronos Series7 refused to boot up from the CD and after trying for 2+hours and failing to get it to boot up from the CD I opted for the Windows installer. Only after completing the installation did I realise that it installed 12.10/64bit. I do think the Windows installer should give a user the option of installing 12.04LTS/32bit, which would probably be the recommended download when downloading the install CD.

---

