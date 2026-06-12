---
title: "Dell Photo AIO 924 under Hardy with wine problem."
date: 2008-05-15
forum: General Help
---

### Post by Gerlads Mod on 2008-05-15
I have been trying to get my Dell AIO 924 printer to work under Hardy and it just won't. I used to use VMplayer but now it is unsupported because of the Hardy update.

I have also tried installing the drivers with wine. The application opens fine, but when I click install drivers it outputs a small window with the following text:
```

INS Res dll not loaded.
        [Okay]

```
Then I click okay and it makes another small window that says:
```

C:\Temp\{9F5FBC24-EFE2-4f90-B498-ECOFB7D47D15}\dlcc\DLCCADERROR
                               [Okay]

```
Then every time I click okay it opens another one of those windows until I click okay like 15 times, then it opens the first window again, then I click okay and then it finally exits.

When I type the command in terminal it outputs:
```

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```
It never goes back to the prompt.

Thanks if anyone knows how to help.

---

