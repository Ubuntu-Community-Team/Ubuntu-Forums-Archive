---
title: "MATLAB 7.6 r2008a in WINE - Java broken again?"
date: 2008-04-26
forum: General Help
---

### Post by ifinishwhatistar on 2008-04-26
I used to have a functioning Wine install of Matlab (2006b) by following directions in the WineDB.  I'm now on Hardy 64-bit and wine .9.59 and tried the same procedure with MATLAB 2008a (the whole point here is that I only have access to the windows disks).

What I did was, I had a functioning 2008a install on my windows partition, and so I copied it from C:\Program Files\MATLAB to my wine ~/.wine/drive_c/Program Files/ (since install from DVD through wine doesn't work).  Doing this, I am able to successfully run MATLAB in Wine with the "-nojvm" option turning off Java (which gets rid of the entire matlab desktop leaving just the command prompt).

However, if I try to run it *with* JRE, it simply hangs at the Splash Screen (using an entire CPU core forever) and Wine gives no feedback in the terminal.  If I then Ctrl-C terminate it, matlab spits out a JVM-related error ```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (0xc000013a), pid=8, tid=9
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b19 mixed mode windows-x86)
# Problematic frame:
# C  [awt.dll+0xa6105]
#
# An error report file with more information is saved as:
# Z:\home\mark\hs_err_pid8.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```
An example error log file and java log file are attached.  I'm not sure if these files reflect anything other than the fact that I terminated it prematurely with Crtl-C but it can't hurt to show.

Note that a problem that was encountered in previous versions of matlab documented in some WineDB entries is that matlab would only work with *some* JRE versions.  The procedure was to replace the original JRE in Program Files/MATLAB/R2008a/sys/java/jre with another (by installing through wine and copying from Program Files/Java) and tell matlab to use that version (editing "jre.cfg").

I have tried to do this, and in particular tried more or less every JRE version from current (1.6.0_05) back down to 1.5.0_06.  None of them works.

Using 1.6.0_01 (and likely some others) produces slightly different behavior.  In this case wine gives some errors: ```
fixme:win:EnumDisplayDevicesW ((null),0,0xd293e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0xd293e4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:font:WineEngCreateFontInstance Untranslated charset 255

```
Which may or may not be meaningful, and the Splash Screen quickly vanishes (and in this case it seems like MATLAB stops churning as CPU usage goes to 0).

If anyone has had any success with 7.6 in wine, or has any advice based on what I said, it'd be much appreciated.

---

