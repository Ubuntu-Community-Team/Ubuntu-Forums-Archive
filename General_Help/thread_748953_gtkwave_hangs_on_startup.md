---
title: "gtkwave hangs on startup"
date: 2008-04-07
forum: General Help
---

### Post by rabidfruitbat on 2008-04-07
Hi all,

just to preface my post, I'm not a newbie at this and have been using verilog simulators and wave form viewers including gtkwave for a _very_ long time.

I'm running on a dual core system and using VNC as my display. The first time I fired up gtkwave there was a very brief message displayed in a window about some random font errors and then nothing. I;ve uninstalled gtkwave, reinstalled using yum, uninstalled and built from source. All to no avail.  This is reproduced on an older P4 system using VNC as my display.

When ever I run gtkwave I get nothing on the display:
- top shows nothing is being a resource hog.
- strace gtkwave -v <my vcd file> shows that gtkwave is wating for a read from the command line:

[ stuff before this deleted for brevity ]
open("/home/thomasd/.gtkwaverc", O_RDONLY|O_LARGEFILE) = 5
fstat64(5, {st_mode=S_IFREG|0666, st_size=6140, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f77000
read(5, "#\n# sample rc file\n#\nsplash_disa"..., 4096) = 4096
read(5, "el \"/Search/Pattern Search\" (nul"..., 4096) = 2044
read(5, "", 4096) = 0
close(5) = 0
munmap(0xb7f77000, 4096) = 0
write(2, "\nGTKWave Analyzer v3.1.8 (w)1999"..., 43
GTKWave Analyzer v3.1.8 (w)1999-2008 BSI

) = 43
mmap2(NULL, 2002944, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b73000
fstat64(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 2), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b72000
read(0,
[ end of trace ]

pressing enter here or typing into the console just returns the string and the program returns to the read() line.

This is driving me crazy! if anyone can help, please reply.

---

### Post by rabidfruitbat on 2008-04-07
I can reproduce this problem on an FC7 P4 system and an FC8 P4 system all running VNC as my display.  All the machines have different graphics cards.

---

### Post by rabidfruitbat on 2008-04-07
I can also confirm that this problem persists when you use the systems normal display and keyboard etc..  i.e. it is not specific to using VNC as the display.

---

### Post by rabidfruitbat on 2008-04-08
The only odd thing that may be a problem is that I've recently named all these machines so they are not all called localhost anymore.  Could this be an issue?

---

### Post by rabidfruitbat on 2008-04-08
OK, this was an RTFM bug or pilot error on my part (doh!). the -v switch means suck vcd data from stdin hence strace hanging at the read function.

So the fix is to use the -f <file name> swtch adn not the -v <file name> switch.

I guess it had to be pilot error as gtkwave is stable software and I had it not working across a number of systems and and distributions.  sigh.  sorry for the waste of bandwidth.

Thomas D.
--

---

