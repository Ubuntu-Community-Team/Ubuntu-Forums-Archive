---
title: "bios error after feisty fawn update"
date: 2007-05-26
forum: General Help
---

### Post by bradmayne on 2007-05-26
Whats up?  I've been working out the kinks after the feisty update with the help from you guys here in the forum.  The last problem I've got is this: when I boot into feisty from GRUB ( i have a dual boot going with vista  on a Toshiba Satellite a135 s4527 with an intel pentium dual core 1.73 GHZ dual core.  The BIOS is phoenix.  I'm receiving a BIOS error message that appears very quickly then disappears and Ubuntu then proceeds to boot as it should with absolutely no other errors or problems.  It's pretty weird.  Does anyone have any idea where I should start? Or has anyone else had this problem?  Any ideas would be greatly appreciated.

---

### Post by mbradlcu on 2007-05-27
on my laptop I see a kernel warning that looks pretty cryptic, something about not being able to allocate resorce at 100100 something. type 'dmesg' and see if what you're seeing is there.. the fix however is WAY above my skill level.

---

### Post by hardyn on 2007-05-27
i don't believe the feisty update could have affected your bios, although it is possible; very highly unlikey...

are you sure its actully bios related, and not grub, or the kernel?

---

### Post by bradmayne on 2007-05-28
hey i appreciate you guys who took the time to respond back to me i did the "dmesg" command here are the messages received if one of you guys or girls has the time to look...


[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983732
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983733
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983734
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983735
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983736
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983737
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983738
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983739
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983740
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983741
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983742
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983743
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983737
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983738
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983739
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983740
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983741
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983742
[ 1139.944000] mmcblk0: error 1 sending read/write command
[ 1139.944000] end_request: I/O error, dev mmcblk0, sector 1983743
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.948000] mmcblk0: error 1 sending read/write command
[ 1139.948000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.952000] mmcblk0: error 1 sending read/write command
[ 1139.952000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.956000] mmcblk0: error 1 sending read/write command
[ 1139.956000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.956000] mmcblk0: error 1 sending read/write command
[ 1139.956000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.956000] mmcblk0: error 1 sending read/write command
[ 1139.956000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.956000] mmcblk0: error 1 sending read/write command
[ 1139.956000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.956000] mmcblk0: error 1 sending read/write command
[ 1139.956000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 249
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 250
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 251
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 252
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 253
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 254
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 255
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 256
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 0
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 8
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 16
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 24
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 0
[ 1139.976000] mmcblk0: error 1 sending read/write command
[ 1139.976000] end_request: I/O error, dev mmcblk0, sector 0
[ 1140.892000] tifm_7xx1: sd card detected in socket 1
brad@brad-laptop:~$ 

thanks again for those who have tried to help so far!!!

---

### Post by mbradlcu on 2007-05-29
cool, thanks for the info,,
I just googled the results, the interesting this is that this seems to be an issue with an SD card,, I'm not saying that's really the problem,, or that I have a fix : ( but check out the results,, O and do you have an SD card on your system?
[http://www.google.com/search?q=mmcblk0%3A+error+1+sending+read%2Fwrite+command&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=mmcblk0%3A+error+1+sending+read%2Fwrite+command&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by bradmayne on 2007-05-29
yes i do have a SD card on my system that is I use in Vista (its a dual boot). I know I know i still use winblows but i need it for work.  Anyways microsoft uses a readyboost feature that they introduced 
in Vista that supposedly speeds up your system as it takes from flash based memory before the HD to speed up memory.  I will be upgrading to 2 gigs of memory this coming month.  Hopefully that will solve my problems however i already thought of that and took out the SD card before boot 
and still received a BIOS bug error but i could still boot into ubuntu or viista as needed.  I updated last night to the newer kernel, header, image, etc. and i still receive the bios bug update however now i can "see" the SD card on my desktop when the SD card is inserted into my notebook.

---

### Post by bradmayne on 2007-06-04
i went back to edgy! Now i don't receive anymore BIOS bug error messages!  Now I can say with certainty that the feisty was causing the BIOS bug error message!  I think I will stay with edgy as I don't think feisty is stable.

---

### Post by nerdman978 on 2007-06-04
I have two theories about your problem.

1) I have heard that Vista doesn't run well with ubuntu sometimes
2) Maybe the update screwed up somehow? Have you tried merely re-installing with the feisty CD?

---

### Post by bradmayne on 2007-06-25
yeah i did a re-install of feisty fawn and i still get the BIOS error. I dunno its weird. I can boot into ubu and vista fine i just wanna know why im gettin this BIOS error ya know? It's definetly not the SD issue that was described above as i don't have the card in my pc.  anyone with ideas let me know!!

---

