---
title: "boot faster from USB hard drive"
date: 2006-11-25
forum: General Help
---

### Post by mjumbewu on 2006-11-25
i have recently been compelled to move my laptop hard drive (two partitions, one home, one root, both reiserfs, running edgy) to an external USB enclosure and boot from there.  unfortunately, this has caused my boot time to consistently be over three minutes.  i have tried a couple of optimizations (namely those listed [here]("http://www.ubuntuforums.org/showthread.php?t=254263&highlight=boot+edgy+faster+profile")), but nothing has seemed to work.  reprofiling seems to have made the boot slower, in fact.

i will post my different bootcharts below.

any ideas will be greatly appreciated.  thank you,

- mjumbe

---

### Post by mjumbewu on 2006-11-25
after reprofiling, with readahead running in background

---

### Post by mjumbewu on 2006-11-25
after reprofiling with readahead running in foreground

---

### Post by mjumbewu on 2006-11-25
before reprofiling

---

### Post by mjumbewu on 2006-11-27
since i got no replies, i went ahead and started experimenting with things.  so, i've so far shaved about a minute off of my boot time.  my new, most recent bootchart is attached.

the first thing i did was stopped my computer from loading the readahead list.  i did this like so: ```
cd /etc/init.d
sudo chmod -x readahead
``` this shaved the first 40 or so seconds off.  having that list did my configuration no extra good; since my hard drive is connected by USB anyway, [i assume] seeking to and loading boot files is not my bottleneck.  (EDIT: [this]("http://www.ubuntuforums.org/showpost.php?p=1482765&postcount=9") seems like a better, more correct way to get rid of the readahead list; thanks to jdong)

next, i disabled the linux-restricted-modules from linking at boot.  i did this by editing /etc/default/linux-restricted-modules-common as root.  I changed the line: ```
DISABLED_MODULES=""
``` to: ```
DISABLED_MODULES="fc nv ltm ath_hal fglrx"
``` ld_static used to consume about 15 seconds of my boot time.  now, i have that time back.  of course, this only works if your computer doesn't use those drivers.  if it does use some of them, then you can still pick and choose and disable the rest.

i have a long way to go before i'm satisfied, but this is a start.  maybe it'll help someone else.

- mjumbe

---

