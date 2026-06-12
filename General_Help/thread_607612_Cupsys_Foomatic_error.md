---
title: "Cupsys Foomatic error"
date: 2007-11-09
forum: General Help
---

### Post by dash2tai on 2007-11-09
Good day,

I had a notebook with Feisty that I upgraded to Gutsy. This computer use the Avasys PPD for Epson AL-CX11NF which I compile and used without any problem. For further reasons I needed to reinstall the computer from scratch with Gutsy and now I can't get the printer working anymore. Symptoms:

. foomatic-gui: unable to read database
. **foomatic debug log with strace**:

[...]
read(14, "lity>\n      </driverfunctionalit"..., 1024) = 1024
read(14, "ionality>A</functionality>\n    <"..., 1024) = 1024
read(14, "/driverfunctionalityexception>\n "..., 1024) = 1024
read(14, " <driver>Postscript</driver>\n   "..., 1024) = 1024
fstat64(14, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
_llseek(14, 0, 0xbffc1a50, SEEK_CUR)    = -1 ESPIPE (Illegal seek)
mremap(0xb6510000, 1052672, 1576960, MREMAP_MAYMOVE) = 0xb6510000
read(14, "acturer>\n      <model>Lexmark Z2"..., 1024) = 1024
read(14, ">\n        <driver>Postscript</dr"..., 1024) = 1024
read(14, ">\n  <printer>\n    <id>Olympus-P-"..., 1024) = 1024
read(14, "    </driverfunctionalityexcepti"..., 1024) = 1024
[...]
brk(0x866c000)                          = 0x866c000
munmap(0xb6510000, 1105920)             = 0
write(2, "Unable to read printer database.", 32Unable to read printer database.) = 32
write(2, "\n", 1
)                       = 1
rt_sigaction(SIGINT, {SIG_DFL}, {0x80f4ee0, [], 0}, 8) = 0
futex(0x822fcf0, FUTEX_WAKE, 1)         = 0
futex(0x8230400, FUTEX_WAKE, 1)         = 0
futex(0x817bce8, FUTEX_WAKE, 1)         = 0
futex(0x816a1a0, FUTEX_WAKE, 1)         = 0
futex(0x816a1a0, FUTEX_WAKE, 1)         = 0
futex(0x816a1a0, FUTEX_WAKE, 1)         = 0
writev(13, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(13)                               = 0
writev(5, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(5)                                = 0
close(11)                               = 0
close(10)                               = 0
unlink("/tmp/orbit-thierry/linc-24bd-0-73f4f1f2c8dec") = 0
close(12)                               = 0
exit_group(0)                           = ?
Process 9405 detached

. **from cups log in debug mode**:
D [08/Nov/2007:22:46:04 +0000] [Job 11] Starting renderer
D [08/Nov/2007:22:46:04 +0000] [Job 11] JCL: <job data> 
D [08/Nov/2007:22:46:04 +0000] [Job 11] 
D [08/Nov/2007:22:46:04 +0000] [Job 11] renderer PID kid4=10814
D [08/Nov/2007:22:46:04 +0000] [Job 11] renderer command: pstoalcx11.sh  PageSize=a4 XY600=4960x7016 MediaType=normal TonerSave=false InputSlot=autoselectio
n Collate=on Copies=1 Color=color Resolution=300dpi
D [08/Nov/2007:22:46:04 +0000] [Job 11] _/bin/bash: /usr/local/bin/pstoalcx11.sh: Permission denied_
D [08/Nov/2007:22:46:04 +0000] [Job 11] r_enderer return value: 126_
D [08/Nov/2007:22:46:04 +0000] [Job 11] renderer received signal: 126
D [08/Nov/2007:22:46:04 +0000] [Job 11] Process dying with "The renderer command line returned an unrecognized error code 126.", exit stat: 1
D [08/Nov/2007:22:46:04 +0000] [Job 11] _error: Illegal seek (29)_
D [08/Nov/2007:22:46:04 +0000] [Job 11] The renderer command line returned an unrecognized error code 126.
D [08/Nov/2007:22:46:04 +0000] [Job 11] Wrote 1 pages...
D [08/Nov/2007:22:46:04 +0000] PID 10804 (/usr/lib/cups/filter/pstops) exited with no errors.

Thanks for any hint

---

