---
title: "OpenOffice not starting"
date: 2006-10-23
forum: General Help
---

### Post by kvonb on 2006-10-23
I don't know when this started, I don't use it very often, but this is the error I get when trying to start OpenOffice word processor:

(I started it from the term so that I could see the errors)

```
kev@kev:~$ ooffice -writer


Fatal exception: Signal 8
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0xb750051f]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb750083f]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb75008dd]
[0xffffe420]
/usr/lib/openoffice/program/libvclplug_gen680li.so[0xb3d4260b]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay4InitEmP6Visualb+0x169)[0xb3d40d33]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb41c3e1c]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb41c51a4]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb41c5572]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(create_SalInstance+0xef)[0xb41c6293]
/usr/lib/openoffice/program/libvcl680li.so[0xb7f18369]
/usr/lib/openoffice/program/libvcl680li.so[0xb7f1846a]
/usr/lib/openoffice/program/libvcl680li.so(_Z7InitVCLRKN3com3sun4star3uno9ReferenceINS1_4lang20XMultiServiceFactoryEEE+0xb7)[0xb7d7bad3]
/usr/lib/openoffice/program/libvcl680li.so[0xb7d7bc31]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0xb7d7bcf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2)[0xb6f1bea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233:  5370 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:5357): WARNING **: Unknown error forking main binary / abnormal early exit ...
kev@kev:~$
```

Any ideas?

Regards,  Kev :)

---

### Post by Mark76 on 2006-10-24
"oowriter" works for me. :)

Or you could try clicking on the icon in Applications/Office

---

### Post by kvonb on 2006-10-25
OK, finally figured it out!

It was the ATI 8.28.8 video driver, I switched back to 8.27.10 and all is well, even Google Earth works properly now.

---

