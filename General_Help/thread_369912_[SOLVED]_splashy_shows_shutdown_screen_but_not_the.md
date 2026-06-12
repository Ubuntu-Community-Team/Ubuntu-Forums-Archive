---
title: "[SOLVED] splashy shows shutdown screen but not the boot up screen"
date: 2007-02-25
forum: General Help
---

### Post by unebaguettesvp on 2007-02-25
ok, so after about 4 days of screwing around with splashy,  i FINALLY get it to work. i FINALLY figured out how to compile it and then run it.

ok. now my problem is the boot up screen. when my computer shuts down or restarts, splashy does its thing. AND IT DOES IT WELL!!!

but then when it boots up, it doesn't run! my guess is that grub doesn't know to launch splashy. does anyone have any ideas? something i could try?

i set /boot/grub/menu.lst to:

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro splash vga=791 quiet

i am running edgy on amd 64 architecture. thank you in advance!!!

---

### Post by unebaguettesvp on 2007-02-25
ok. so, i took out "quiet" to see if maybe there are errors that grub will show me during boot up as to why it's not loading splashy. but the text came out too fast for me to read. is there a log file that grub creates that i can view of the last boot up?

---

### Post by unebaguettesvp on 2007-02-25
So, I fixed my splashy problem!!!! If anyone else has these problems, MAKE SURE not to overlook this:

[http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions](http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions)

That was what solved it. Currently, the code says to do to replace /etc/event.d/rcS with this:

  --- /etc/event.d/rcS 2006-09-13 18:47:27.000000000 -0400
  +++ rcS 2006-12-18 13:12:42.000000000 -0500
  @@ -14,6 +14,12 @@
   # information (we enter rc1 not rcS for maintenance). Run /etc/init.d/rc
   # without information so that it defaults to previous=N runlevel=S.
   script
  - runlevel --set S >/dev/null || true
  + set $(runlevel --set S || true)
  + if [ "$1" != "unknown" ]; then
  + PREVLEVEL=$1
  + RUNLEVEL=$2
  + export PREVLEVEL RUNLEVEL
  + fi
  +
          exec /etc/init.d/rcS
   end script

This is where I screwed up. the minus sign means take out runlevel --set S >/dev/null || true, and the plus signs mean add that section of code in. So your /etc/event.d/rcS file should now look something like this:

# rcS - runlevel compatibility
#
# This task runs the old sysv-rc startup scripts.

start on startup

stop on shutdown
stop on runlevel-2
stop on runlevel-3
stop on runlevel-4
stop on runlevel-5

# Note: there can be no previous runlevel here, if we have one it's bad
# information (we enter rc1 not rcS for maintenance).  Run /etc/init.d/rc
# without information so that it defaults to previous=N runlevel=S.
script
	set $(runlevel --set S || true)
	if [ "$1" != "unknown" ]; then
	PREVLEVEL=$1
	RUNLEVEL=$2
	export PREVLEVEL RUNLEVEL
	fi

	exec /etc/init.d/rcS
end script

I hope that helps someone!!!

---

