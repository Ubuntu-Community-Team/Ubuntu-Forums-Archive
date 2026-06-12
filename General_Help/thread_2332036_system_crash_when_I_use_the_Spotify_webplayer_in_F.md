---
title: "system crash when I use the Spotify webplayer in Firefox"
date: 2016-07-27
forum: General Help
---

### Post by ayup on 2016-07-27
Hi, 

I am running Ubuntu 14.04 on a HP ProBook. I encountered a system freeze twice, when suddenly everything started to be very slow, then unresponsive, and after a few minutes I couldn't even move the mouse any more and had to do a hard reset. After that, everything fine again. Both times I was using the Spotify Web Player in Firefox, which I only did on these two occasions, which makes me think that the problem must have something to do with this. Otherwise I wasn't doing anything out of the ordinary - LibreOffice, some PDFs.

Might be of relevance (though I'm not sure): When I installed Ubuntu on the Probook, the sound didn't work and I fixed it by editing into /etc/modprobe.d/alsa-base.conf as described here [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1536948](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1536948). 

But any other occasion where I use sound on the computer (watching movies etc etc) everything's fine.

Do you have any ideas what could have caused the freeze and where I could look for a solution? Thanks.

I'm a newbie so please be patient.

Best, T

---

### Post by TheFu on 2016-07-28
Check the log files. Any issues should be shown in those.  Then you can correct them.

The only time I've seen a working system without any issues reported in log files lock up is when RAM was used up completely and the swap completely used too. This tends to happen on low RAM systems with small swap partitions ... or when using one of the bloated web browsers with lots of tabs open which can easily suck up 4G of RAM.  Watch the RAM usage going forward.

---

### Post by ayup on 2016-07-28
Thanks for the feedback!

The log files don't help me much, unfortunately because I can't locate the problem, but if it happens again I'll make sure to look into them immediately.

I did have a lot of tabs open, though. What makes a webbrowser bloated?

---

### Post by TheFu on 2016-07-28
I doubt the logs were removed within a day of a crash. The data is in there, if there is any.  Look for error or warning inside all the file in and below /var/log/ .

Bloated programs are those that the programmer/architect has decided to use RAM for unnecessary things and doesn't free that RAM again when it isn't needed anymore.  Browsers tend to use RAM for addons, plugins, pre-loading pages that haven't been requested, all to make the browser more like a desktop, more interactive, and to make page loading appear faster. Being inefficient with internal data structures is another issue, but we can't usually see that as end-users. 
Web designers are to blame too. The average size of a webpage has ballooned over the years from less than 2Kb to 50-200Kb.  So, if we load 20 tabs with 200Kb pages, that really isn't too much, but the RAM use will be much larger. We might expect it to be 20 x 200Kb (about 4MB), but that isn't what happens. It will probably be 1GB or more.

Everyone knows that current browsers are bloated, but they have to be to do all the things that web designers and average users demand.  Many browsers are doing other things that we don't want.  Some have been caught sending data back to their creators without our permission.  A few weeks ago, a browser made in China was caught sending data back even if the users had checked the "Don't send data" box. 

OTOH, anyone can claim that any program is bloated and from that perspective, it is true. For example, I'm using Firefox to view this page now and have 20+ tabs open.  The RAM used by it is 2.7GB.  I am not on any video sites, so what is using all that RAM?  text, images, javascript, ads, and other dynamic content.  Firefox is/was known to leak memory thanks to different addons not cleaning up properly too.  Since I don't reboot more than once a week, firefox will always use more and more RAM day after day until the reboot.  Any browser that isn't lynx is bloated, by my definition, though dillo might not be. Dillo is barely a browser by the standards today and it is far from perfect. Definitely do not use it for anything secure or private.

If you'd like to be really paranoid about browsers, just search for "browser issues privacy"

---

### Post by ayup on 2016-07-28
Okay, now I understand better. Thanks for the info!

I've looked into the log files again and I think I've found the crash. 

In /var/log/kern.log, it seems to start with this:

```
i915 0000:00:02.0: Direct firmware load for i915/skl_dmc_ver1.bin failed with error -2
[drm:i915_firmware_load_error_print [i915]] *ERROR* failed to load firmware i915/skl_dmc_ver1.bin (0)
```

And then there are a couple of times when this error occurred:

```
[drm:skl_set_power_well [i915]] *ERROR* CSR firmware not ready
```

And there's also this warning:

```
WARNING: CPU: 0 PID: 198 at /build/linux-lts-wily-Ejb_ce/linux-lts-wily-4.2.0/drivers/gpu/drm/i915/intel_csr.c:465 assert_csr_loaded+0xdb/0x100 [i915]()

```

And then I think this is when it crashed:

```
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.558053] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff8800a10af240 (20150619/exresop-590)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.558066] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20150619/dswexec-461)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.558075] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WVPO] (Node ffff88014b8ab3e8), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.558088] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WMPV] (Node ffff88014b8ab438), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.559575] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff8800a10af6c0 (20150619/exresop-590)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.559583] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20150619/dswexec-461)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.559591] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WVPO] (Node ffff88014b8ab3e8), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.559602] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WMPV] (Node ffff88014b8ab438), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.561061] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff8800a10af360 (20150619/exresop-590)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.561068] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20150619/dswexec-461)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.561076] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WVPO] (Node ffff88014b8ab3e8), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.561087] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WMPV] (Node ffff88014b8ab438), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.561225] input: HP WMI hotkeys as /devices/virtual/input/input14
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563437] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff8800a10af4c8 (20150619/exresop-590)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563447] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20150619/dswexec-461)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563455] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WVPO] (Node ffff88014b8ab3e8), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563467] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WMPV] (Node ffff88014b8ab438), AE_AML_OPERAND_TYPE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563701] ACPI Error: Attempt to CreateField of length zero (20150619/dsopcode-168)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563708] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WVPI] (Node ffff88014b8ab398), AE_AML_OPERAND_VALUE (20150619/psparse-536)
Jul 26 11:47:30 tina-HP-ProBook-430-G3 kernel: [   53.563722] ACPI Error: Method parse/execution failed [\_SB_.WMIV.WMPV] (Node ffff88014b8ab438), AE_AML_OPERAND_VALUE (20150619/psparse-536)
```


And again, I'm not 100% positive that I am reading these files correctly, but this is what I found. Can anyone make sense of that?

---

