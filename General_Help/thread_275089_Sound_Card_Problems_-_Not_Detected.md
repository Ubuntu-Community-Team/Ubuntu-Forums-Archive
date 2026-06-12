---
title: "Sound Card Problems - Not Detected"
date: 2006-10-10
forum: General Help
---

### Post by TigerWolf on 2006-10-10
Ok - i made a mistake and i was trying to install  the oss from [http://www.opensound.com/](http://www.opensound.com/) to play around with the virtual mixer. It didnt work so i uninstalled it using its uninstall script. Now no sound works at all. I DESPERATELY! need some help.

Its detecting the sound card (as per below commands) but there is no /proc/modules/asound directory at all. Any idea on a way to fix it?

tigerwolf@tigerwolf-desktop:~$ lspci | grep audio
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
tigerwolf@tigerwolf-desktop:~$ sudo modprobe snd-ck804
Password:
FATAL: Module snd_ck804 not found.

---

### Post by TigerWolf on 2006-10-10
Whenever i launch a program I get this

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM default
```

---

### Post by Phlosten on 2006-10-11
Have you perhaps tried reinstalling alsa-base?

---

### Post by TigerWolf on 2006-10-11
That didnt seem to work. Ive reinstalled alot of things and nothing has solved it.

Tried some other commands and they came out with these errors:

$ sudo modprobe snd-ac97-codec
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-27-k7/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_ac97_codec (/lib/modules/2.6.15-27-k7/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)


tigerwolf@tigerwolf-desktop:~$ dmesg

[17197153.564000] snd_pcm: disagrees about version of symbol snd_timer_notify
[17197153.564000] snd_pcm: Unknown symbol snd_timer_notify
[17197153.564000] snd_pcm: disagrees about version of symbol snd_timer_interrupt[17197153.564000] snd_pcm: Unknown symbol snd_timer_interrupt
[17197153.564000] snd_pcm: disagrees about version of symbol snd_timer_new
[17197153.564000] snd_pcm: Unknown symbol snd_timer_new
[17197153.564000] snd_ac97_codec: Unknown symbol snd_interval_refine
[17197153.564000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add

---

### Post by TigerWolf on 2006-10-11
Ive tried everything and nothing works. Im pleading for help. Ive even comipled me kernel and this didnt fix it.

This is the script that killed everything that i regret running. Nearly as bad as  rm -rf /

```
#!/bin/sh

if test -f /etc/oss.conf
then
  . /etc/oss.conf
else
  echo "Error: /etc/oss.conf not found - don't know where OSS is installed!"
  exit -1
fi

$OSSLIBDIR/bin/soundoff

rm -f /usr/local/bin/soundon
rm -f /usr/local/bin/soundoff
rm -f /usr/local/bin/soundconf
rm -f /usr/lib/libOSSlib.so /usr/lib64/libOSSlib.so
rm -f /etc/drums.sb /etc/drums.o3 /etc/std.sb /etc/std.o3
if test "`/sbin/chkconfig --help 2>&1 |grep level` " != " "
then
/sbin/chkconfig --level 2345 oss off >> /dev/null 2>&1
else
/sbin/chkconfig --set oss off >> /dev/null 2>&1
fi
/sbin/chkconfig --del oss >> /dev/null 2>&1
rm -f /etc/rc.d/init.d/oss /etc/rc*.d/S99oss
rm -rf $OSSLIBDIR
rm -f /dev/dsp_ac3 /dev/dsp_multich

rm -f /dev/dsp
ln -s /dev/dsp0 /dev/dsp

for n in /etc/modules.conf /etc/modprobe.conf /etc/modprobe.conf.dist /etc/hotplug/blacklist
do
  if test -f $n
  then
    rm -f /tmp/uninst.tmp
    cp $n /tmp/uninst.tmp

    grep -v ADDED_BY_OSS /tmp/uninst.tmp|sed 's/^# \(.*\) #\tREMOVED_BY_OSS/\1/' > $n
    rm -f /tmp/uninst.tmp
  fi
done

if test -f /lib/modules/`uname -r`/sound-preoss.tar.bz2
then
	(cd /lib/modules/`uname -r`;tar xfj /lib/modules/`uname -r`/sound-preoss.tar.bz2)
fi

rm -f /usr/lib/libasound.so.2 /lib/libasound.so.2 >> /dev/null 2>&1

ldconfig -v >> /dev/null 2>&1

```

HELP!

---

### Post by TigerWolf on 2006-10-11
All fixed. Upgraded to edgy and it worked.

---

