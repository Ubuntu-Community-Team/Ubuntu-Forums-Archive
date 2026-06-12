---
title: "DVD not working"
date: 2013-01-03
forum: General Help
---

### Post by mosquetero on 2013-01-03
Hi!

I am trying to play a DVD for the first time in my life in Ubuntu. I am using VLC but it is not working.I get the next output in the VLC logs:

```
main debug: processing request item: sr0, node: Playlist, skip: 0
main debug: resyncing on sr0
main debug: sr0 is at 4
main debug: starting playback of the new playlist item
main debug: resyncing on sr0
main debug: sr0 is at 4
main debug: creating new input thread
main debug: Creating an input for 'sr0'
main debug: TIMER input launching for 'sr0' : 23560.758 ms - Total 23560.758 ms / 1 intvls (Avg 23560.757 ms)
qt4 debug: IM: Setting an input
main debug: using timeshift granularity of 50 MiB, in path '/tmp'
main debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
main debug: creating demux: access='dvd' demux='' location='/dev/sr0' file='/dev/sr0'
main debug: looking for access_demux module: 2 candidates
dvdnav warning: cannot open DVD (/dev/sr0)
dvdread error: DVDRead cannot open source: /dev/sr0
main debug: no access_demux module matching "dvd" could be loaded
main debug: TIMER module_need() : 10.073 ms - Total 10.073 ms / 1 intvls (Avg 10.073 ms)
main debug: creating access 'dvd' location='/dev/sr0', path='/dev/sr0'
main debug: looking for access module: 0 candidates
main debug: no access module matched "dvd"
main debug: TIMER module_need() : 0.117 ms - Total 0.117 ms / 1 intvls (Avg 0.117 ms)
main error: open of `dvd:///dev/sr0' failed
main debug: finished input
main debug: dead input
main debug: changing item without a request (current 4/5)
main debug: nothing to play
qt4 debug: IM: Deleting the input
```

I used disk utility to find the CD/DRIVE file and the I can see that the CD/DVD file is /dev/sr0.

What can I do?

Thanks :D

---

### Post by TheFu on 2013-01-03
Have you loaded the "restricted DVD" modules? Here's a howto:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

**DRM sucks.**

---

### Post by mosquetero on 2013-01-03
Thanks!!! It worked :D

---

### Post by coldcritter64 on 2013-01-03
> **mosquetero said:**
> Thanks!!! It worked :D

Could you mark the thread "solved", please? You can use the "thread tools" drop down menu in your browser window to do so. Cheers.

---

