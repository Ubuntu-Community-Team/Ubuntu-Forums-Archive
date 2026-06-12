---
title: "Insane Memory Usage from Nautilus, Rhythmbox, Evince"
date: 2019-04-13
forum: General Help
---

### Post by el Arm on 2019-04-13
About a year ago I started getting memory problems on 16.04, mostly with the Nautilus file manager using huge amounts of RAM (20-30GB). When this happens the desktop is almost unusable and I have to open a terminal and kill the process. Running top -o VIRT;

[ATTACH=CONFIG]283018[/ATTACH]

Notes;
[LIST]
[*]Rhythmbox has a similar but benign problem, it always reports ~100GB on startup but this memory does not appear to be actively used and doesn't stress the computer. I do not know if this started happening with the nautilus problem.
[*]Evince will also use lots of RAM and make the desktop unusable if I open a PDF file with more than a couple of pages. I've switched to qpdfview with no problems.
[*]Nautilus does not always misbehave, but is 99% likely to do it on folders with lots of images, like my photos area. Sometimes it will happen on my home folder, but usually not. If it does, after killing I restart it to get the desktop icons then immediately close the file browser window when it appears to avoid the RAM issue.
[*]Running free -m shows that physical RAM is maxed but swap is not, but I assume the desktop problems are from constant swapping. E.g.
```
              total        used        free      shared  buff/cache   available
Mem:          15919       15009         143         514         767          75
Swap:         16383        2219       14164

```
[/LIST]

Any ideas on how to solve this, or analysis that can be done to find out why it uses this memory?

My guess is a bug in one of the kernel updates at the time or a library used by both Nautilus and Evince. I suppose a hardware issue would be possible too.

I plan to upgrade to 20.04 next year and hope it goes away. Could test a fresh 16.04 or 18.04 boot USB stick, but I suspect this would be fine and wouldn't be a helpful test given the amount of extra software I have installed.

Thanks

---

### Post by Rubi1200 on 2019-04-13
Hi,

A couple of questions:

1. do you have clamscan installed?

2. do you normally have a lot of windows open with files, say pictures or other potentially heavy content?

Thanks.

---

### Post by el Arm on 2019-04-13
> **Rubi1200 said:**
> 
1. do you have clamscan installed?

2. do you normally have a lot of windows open with files, say pictures or other potentially heavy content?

Hi, no, clamscan (or any AV) is not installed and I don't do a lot of file management on this computer, usually only 2 windows open when I do (although often media files like podcast mp3s which can have their own images). This problem can happen after a fresh reboot with nothing else open.

Just ran a strace on evince opening a 3MB PDF with ~200 pages (a breadmaker manual). After 8000 lines of output we have this;

```

[COLOR="#FF8C00"]open("/usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg", O_RDONLY) = 16[/COLOR]
fstat(16, {st_mode=S_IFREG|0644, st_size=67117056, ...}) = 0
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
brk(0x5608b084d000)                     = 0x5608b084d000
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192

```

This continues for 1.2 millions lines before I killed it - blocks of up to a couple of hundred of the same read(16...zeros) line interspersed with the occasional brk, remap, mremap and periods where it seems to genuinely read from the file, close it and reopen.

```

read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
mremap(0x7f69cdffe000, 67112960, 134221824, MREMAP_MAYMOVE) = 0x7f69c5ffd000
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192
read(16, "<?xml version=\"1.0\" encoding=\"UT"..., 8192) = 8192
read(16, "", 8192)                      = 0
close(16)                               = 0
open("/usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg", O_RDONLY) = 16
fstat(16, {st_mode=S_IFREG|0644, st_size=67117056, ...}) = 0
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 65536) = 65536
close(16)                               = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\n\0\10\0\340\1m\1\0\0\6\0\0\0 s\363\377\4\0\0\0\0\0\0\0\0\0\0\0"..., 3796}, {NULL, 0}, {"", 0}], 3) = 3796
recvmsg(3, 0x7ffc465d8380, 0)           = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}, {fd=4, events=POLLIN}, {fd=9, events=POLLIN}], 3, 0) = 2 ([{fd=3, revents=POLLIN}, {fd=4, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"\34\0\254\4\10\0\340\1m\1\0\0004\33'\2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096}], msg_controllen=0, msg_flags=0}, 0) = 32
recvmsg(3, 0x7ffc465d83a0, 0)           = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0x7ffc465d8250, 0)           = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0x7ffc465d8380, 0)           = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}, {fd=4, events=POLLIN}, {fd=9, events=POLLIN}], 3, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\2\0\0\0\0\0\0\0", 16)         = 8
[COLOR="#FF8C00"]open("/usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg", O_RDONLY) = 16[/COLOR]
fstat(16, {st_mode=S_IFREG|0644, st_size=67117056, ...}) = 0
read(16, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 8192) = 8192

```

Since that busy icon is used and expected as it's processing the file for display I don't know if that's the problem, but the repetition seems odd. The other two file descriptors are;
  3 = /usr/lib/x86_64-linux-gnu/libunity-gtk3-parser.so.0
  4 = ~/.Xauthority

Another path for me to Google anyhow, thank you.

---

### Post by Rubi1200 on 2019-04-13
After more searching I was not able to find a definitive answer. There are posts about users with similar issues but some seem to be triggered even when Nautilus is idle, others report high usage but no solutions other than to kill the process.

What you could try is removing Evince and Rhythmbox and replacing them with something else. For example, I prefer VLC for media and for PDF I have heard that qpdfview is light on resources though I have never tested it.

One suggestion I do have is to add Nautilus to Startup Applications and then monitor usage. If needs be you can always remove it if there is no improvement.

---

### Post by el Arm on 2019-04-14
Happy to report I've figured it out. Short answer: corrupt and over-large file */usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg*. Programs using this icon during busy times (nautilus and evince) would blow out memory. This is likely particular to my installation and not something anyone else will encounter.

*Long answer:*

I ran strace on nautilus this time and noticed the same reads of many blocks of 0s. Checking the file size, it was 67MB whereas every other file under icons was barely 10k. A stat on the file shows it was not modified recently, but for corrupt files that's not necessarily relevant;

```
  File: '/usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg'
  Size: **67117056**  	Blocks: 16         IO Block: 4096   regular file
Device: 803h/2051d	Inode: 2246027     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2019-04-14 07:53:14.842947346 +0800
Modify: 2016-05-18 10:21:46.000000000 +0800
Change: 2016-05-31 21:45:31.285436610 +0800
```

Searching around I found the debsums utility which will calculate the checksums of all installed files and compare to the expected from the package installation;

```
%> sudo debsums_init
%> sudo debsums -cs
         /usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/__init__.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/config.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/cupshelpers.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/installdriver.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/openprinting.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/ppds.cpython-35.pyc
         /usr/lib/python3/dist-packages/cupshelpers/__pycache__/xmldriverprefs.cpython-35.pyc
         /usr/lib/ruby/1.8/rr_lib.rb
```

Ignoring the python files, since they seem to be caches, and also rubyripper since I compiled from source after installing the official package. Next dpkg shows which package the icon comes from;

```
%> dpkg -S /usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg
**adwaita-icon-theme**: /usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg
```

Then reinstall the package;

```
%> sudo apt install --reinstall adwaita-icon-theme
%> stat /usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg 
          File: '/usr/share/icons/Adwaita/scalable-up-to-32/status/process-working-symbolic.svg'
          Size: **4756**      	Blocks: 16         IO Block: 4096   regular file
        Device: 803h/2051d	Inode: 2233197     Links: 1
        Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
        Access: 2019-04-14 16:49:00.000000000 +0800
        Modify: 2016-05-18 10:21:46.000000000 +0800
        Change: 2019-04-14 16:49:01.125761136 +0800
```

Much better, now a 5k file. Nautilus now uses very little memory even opening many windows in high file-count directories, and same with Evince opening my large PDF. Rhythmbox continues to use 97GB when it starts, but as mentioned before this doesn't cause a problem. If it ever does I'll switch to Foobar 2000.

Thanks Rubi1200 for your suggestions. Very glad this longstanding annoyance is gone!

---

### Post by Rubi1200 on 2019-04-14
Very interesting detective work. Well done to figuring it out, I am impressed :-)

Please mark this thread Solved using the Thread Tools at the top of the first post.

Good luck!

---

