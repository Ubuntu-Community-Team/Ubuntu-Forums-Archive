---
title: "Curious process .."
date: 2020-12-19
forum: General Help
---

### Post by yapidumoac on 2020-12-19
I installed Mailspring and now get the following strange process. What exactly does addr2line do?

$lubuntu  19578  2239  0 11:14 ? 00:00:00 sh -c addr2line -f -i -C -s -p -e /usr/share/mailspring/resources/app.asar.unpacked/mailsync.bin 0xf5f803 0x65f803 0xf4dfe2 0x64dfe2 0xf4f020 0x64f020 0x7f0f90752840 0x37840 0x7f0f907527ee 0x377ee 0x7f0f9073d535 0x22535 0x7f0f9073d40f 0x2240f 0x7f0f9074e102 0x30102 0x967f41 0x567f41 0x9647e5 0x5647e5 0x82e397 0x42e397 0x829562 0x429562 0x822ff7 0x422ff7 0x81e282 0x41e282 0x810ffe 0x410ffe 0x8088fe 0x4088fe 0x7fee6d 0x3fee6d 0x7f3f63 0x3f3f63 0x7d0ef9 0x3d0ef9 0x7f0f9073f09e 0x2409e 0x7dff65 0x3dff65 2>&1

---

### Post by Holger_Gehrke on 2020-12-19
addr2line is part of the Gnu binutils. It is used to translate (hexadecimal) addresses in a binary executable into line numbers in the source code. It's might be called after a bad crash to generate part of the crash report. For more details on what all the switches do check the manual page for addr2line ('man addr2line' in a terminal).

Holger

---

### Post by yapidumoac on 2020-12-19
Thanking you ..

---

