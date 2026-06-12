---
title: "/usr/local/lib is not in the path anymore"
date: 2021-04-17
forum: General Help
---

### Post by hk42 on 2021-04-17
I solved the problem with symlinks to /usr/lib but sure there is a better way.
IIRC  it was working before .
There is very few things in my /usr/local/lib and they are not from Ubuntu.
Mainly drivers for an SDRplay USB device.

---

### Post by TheFu on 2021-04-17
/usr/local/lib has never been in the PATH.   PATH is for executable programs.

/usr/local/lib would be used by shared libraries - .so files.  Where to look for those is controlled by the LD_LIBRARY_PATH and by some config files in /etc/ld.so.conf.d/*.conf.  I see /usr/local/lib/ in a config file in there.

```
$ more libc.conf 
# libc default configuration
/usr/local/lib
```

---

### Post by hk42 on 2021-04-20
Thanks for your answer
Yes I know I was wrong with path but could not remember the LD_LIBRARY_PATH term.
In fact the 2 programs that don't find their libraries are in the app-image format and on a NAS drive
Since I made the symlinks all is OK.

---

### Post by TheFu on 2021-04-20
> **hk42 said:**
> Thanks for your answer
Yes I know I was wrong with path but could not remember the LD_LIBRARY_PATH term.
In fact the 2 programs that don't find their libraries are in the app-image format and on a NAS drive
Since I made the symlinks all is OK.

Is the NAS location mounted?  or using autofs?

I've never gotten AppImages to work based on symlinks.  The way the AppImage unpacks includes some overly simplified efforts to figure out the location of the binary and that fails.

I put all AppImages in /usr/local/appimages/
```
$ ls  -F /usr/local/appimages/
roku-remote-tool-linux64.AppImage*
```

When I create a symlink
```
cd ~/bin/
ln -s /usr/local/appimages/roku-remote-tool-linux64.AppImage

```
Running roku-remote-tool-linux64.AppImage fails.  ~/bin/ is in my PATH.  Running ~/bin/roku-remote-tool-linux64.AppImage fails too.  It thinks everything is in ~/bin/ by mistake.  I've looked at this problem for some of my own programs/scripts and there are a number of clear, 1-line, answers which almost always work ... unless symbolic links are used.  ;(  When symlinks are involved, the solution gets ugly.

Were you trying to accomplish something similar? Would love a 1-liner to determine the true target location for a program that doesn't get confused.

---

### Post by hk42 on 2021-05-01
Hi sorry for the late reply.
Yes the NAS location is mounted.
The strange thing in my case is that the SDRplay hardware was found and used sometimes before I added 
the symlinks.But mostly I got an "Hardware or driver not found" message from the Qt_DAB App-image.

---

