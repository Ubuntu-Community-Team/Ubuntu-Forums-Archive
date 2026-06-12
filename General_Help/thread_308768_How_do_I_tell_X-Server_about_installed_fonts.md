---
title: "How do I tell X-Server about installed fonts?"
date: 2006-11-28
forum: General Help
---

### Post by elektronaut on 2006-11-28
Hi,

I've installed some additional fonts using Synaptic. They are all in /usr/share/fonts/truetype/[subdirectory/]. I called ```
sudo fc-cache -f -v
```I restarted the X-Server, I rebooted... but xlsfonts never lists me those fonts. They are there, Debian Font Manager recognizes them, the permissions are also o.k. I'd really like to use some fonts with emacs, but emacs only works with fonts which are found by xlsfonts. What can I do?

---

### Post by ~LoKe on 2006-11-28
Perhaps they need to be in the list in /etc/X11/xorg.conf
> Section "Files"
        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

---

### Post by elektronaut on 2006-11-28
Thank you for your answer! Unfortunately it didn't work. I also found [this thread](http://ubuntuforums.org/showthread.php?t=96785) and tried the advice in the [third post](http://ubuntuforums.org/showpost.php?p=530774&postcount=3). This is now in /etc/X11/xorg.conf:
```
FontPath        "/usr/local/share/fonts"
```
and this in the directory:
```
$ ls -la /usr/local/share/fonts/
insgesamt 980
drwxrwsr-x 2 root staff  4096 2006-11-28 22:58 .
drwxr-xr-x 8 root root   4096 2006-11-28 10:33 ..
-rw-r--r-- 1 root staff  8530 2006-11-28 23:01 fonts.cache-1
-rw-r--r-- 1 root staff 69872 2006-11-28 22:58 luximbi.ttf
-rw-r--r-- 1 root staff 74076 2006-11-28 22:58 luximb.ttf
-rw-r--r-- 1 root staff 69496 2006-11-28 22:58 luximri.ttf
-rw-r--r-- 1 root staff 71784 2006-11-28 22:58 luximr.ttf
-rw-r--r-- 1 root staff 85756 2006-11-28 22:58 luxirbi.ttf
-rw-r--r-- 1 root staff 87160 2006-11-28 22:58 luxirb.ttf
-rw-r--r-- 1 root staff 86396 2006-11-28 22:58 luxirri.ttf
-rw-r--r-- 1 root staff 88732 2006-11-28 22:58 luxirr.ttf
-rw-r--r-- 1 root staff 65568 2006-11-28 22:58 luxisbi.ttf
-rw-r--r-- 1 root staff 69972 2006-11-28 22:58 luxisb.ttf
-rw-r--r-- 1 root staff 66372 2006-11-28 22:58 luxisri.ttf
-rw-r--r-- 1 root staff 67548 2006-11-28 22:58 luxisr.ttf
```
'sudo mkfontcache .', didn't run, so I just ran sudo fc-cache -f -v, mentioned in [post 5](http://ubuntuforums.org/showpost.php?p=535805&postcount=5), and restarted the X-Server. Still, the fonts are not found by xlsfonts. :-?

---

### Post by zeizad on 2006-11-29
I had a similar problem when I upgraded from dapper to edgy. I had all my truetype fonts installed but xlsfonts couldn't see any of them even though the directory entry for my font directory existed in xorg.conf. So this is what I did. I changed to the directory to where the fonts are installed and ran mkfontdir.
```

sudo mkfontdir

```
Then I set up X using xset.
```

xset +fp my_font_dir
xset fp rehash

```
See if this works for you.

---

