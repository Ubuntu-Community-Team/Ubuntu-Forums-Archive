---
title: "How to keep more than 2 kernel versions back in 22.04?"
date: 2022-04-23
forum: General Help
---

### Post by &amp;KyT$0P# on 2022-04-23
In 20.04 I had edited [FONT=Courier New]/etc/kernel/postinst.d/apt-auto-removal[/FONT] to keep 3 kernel versions back instead of the standard 2.  I've had multiple cases where that third kernel was needed.

In 22.04, this file is gone.  And as far as I can tell, its replacement is some C code that's built into apt at compile time?

Is there a *supported* way to make the new method of preserving kernels retain 3 kernel versions back?

If not, is there some other non-drastic way to preserve a third kernel?  For example, could it be done by using the old method of preserving kernels in parallel to the new method?  Looking at the apt source code, it looks like they've also added code to actively remove the old method, so not sure I can trust dropping in the modified script from my 20.04 backup.

---

### Post by &amp;KyT$0P# on 2022-04-25
bump

---

### Post by ameinild on 2022-04-26
This seems like a really stupid design decision, if your suspicion is right. I'm interested to hear more about this from someone who knows - sorry I can't really help though. ;)

---

### Post by &amp;KyT$0P# on 2022-04-27
bump

---

### Post by kevdog on 2022-04-28
I don't see any apt-auto-removal file in that directory after I upgraded.   Do you have a copy of the file.

---

### Post by &amp;KyT$0P# on 2022-04-28
> **kevdog said:**
> I don't see any apt-auto-removal file in that directory after I upgraded.   Do you have a copy of the file.

Yes, but currently my copies of this file are not on my 22.04 system either.  I have my modified version in backup of my 20.04 system, and it looks like the latest unmodified version is the one in [apt for impish .deb]("https://packages.ubuntu.com/impish/apt").  Which are you looking to see?

---

### Post by &amp;KyT$0P# on 2022-05-01
bump

---

### Post by &amp;KyT$0P# on 2022-05-04
bump

---

### Post by #&amp;thj^% on 2022-05-04
is this what your looking for?
```
**cat /etc/kernel/postinst.d/xx-update-initrd-links**
#!/bin/sh
set -e

# installkernel script calls postinst.d without any DEB_MAINT_PARAMS set
# linux-image-* postinst calls postinst.d with DEB_MAINT_PARAMS set
# do nothing in case linux-image-* calls this, as it already calls `linux-update-symlinks`
[ -z "$DEB_MAINT_PARAMS" ] || exit 0

# installkernel must call postinst.d with two args, version & image_path
version="$1"
image_path="$2"

[ -n "$version" ] || exit 0
[ -n "$image_path" ] || exit 0

# call linux-update-symlinks in install mode, which will correctly
# update vmlinuz & initrd.img symlinks. Even if initrd.img does not
# exist yet, or has already been created by the initramfs-update
# postinst.d hook. It will also honor kernel_img.conf settings to
# link_in_boot yes/no. Thus matching behaviour of linux-image-*
# postinst call to linux-update-symlinks.
linux-update-symlinks install $version $image_path

exit 0

```

---

### Post by &amp;KyT$0P# on 2022-05-04
Sorry, apparently I didn't explain the problem well enough.  This isn't about those symlinks.  It's about apt.

apt automatically "protects" the latest 2 installed kernels from being auto-removed.  I would like the third-latest installed kernel to be likewise protected also.

In previous Ubuntu versions, I could achieve this by modifying [FONT=Courier New]/etc/kernel/postinst.d/apt-auto-removal[/FONT] .  But as noted in the first post, 22.04 apt changed how kernel protection is done.  And looking at code of 22.04 apt, seems it might actively remove the [FONT=Courier New]/etc/kernel/postinst.d/apt-auto-removal[/FONT] method of protecting kernels?

Hope this helps clarify the first post.

---

### Post by #&amp;thj^% on 2022-05-04
No you was clear enough ;) but why wouldn't something like this work:
```
sudo apt-mark auto ^linux-image-
[sudo] password for me: 
linux-image-extra-virtual-hwe-20.04 can not be marked as it is not installed.
linux-image-azure can not be marked as it is not installed.
linux-image-5.15.0-27-lowlatency can not be marked as it is not installed.
linux-image-aws can not be marked as it is not installed.
linux-image-lowlatency can not be marked as it is not installed.
linux-image-5.15.0-1004-intel-iotg can not be marked as it is not installed.
linux-image-lowlatency-hwe-22.04 can not be marked as it is not installed.
linux-image-gke-5.15 can not be marked as it is not installed.
linux-image-gcp can not be marked as it is not installed.
linux-image-gke can not be marked as it is not installed.
linux-image-ibm can not be marked as it is not installed.
linux-image-generic-hwe-20.04-edge can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1004-intel-iotg can not be marked as it is not installed.
linux-image-kvm can not be marked as it is not installed.
linux-image-generic-hwe-22.04-edge can not be marked as it is not installed.
linux-image-unsigned-5.15.0-24-lowlatency can not be marked as it is not installed.
linux-image-oem-22.04a can not be marked as it is not installed.
linux-image-unsigned-5.15.0-27-lowlatency can not be marked as it is not installed.
linux-image-intel-iotg can not be marked as it is not installed.
linux-image-5.15.0-1003-oracle can not be marked as it is not installed.
linux-image-extra-virtual-hwe-20.04-edge can not be marked as it is not installed.
linux-image-5.15.0-1002-gke can not be marked as it is not installed.
linux-image-extra-virtual-hwe-22.04-edge can not be marked as it is not installed.
linux-image-5.15.0-1002-ibm can not be marked as it is not installed.
linux-image-virtual-hwe-22.04 can not be marked as it is not installed.
linux-image-5.15.0-1003-gcp can not be marked as it is not installed.
linux-image-5.15.0-1003-gke can not be marked as it is not installed.
linux-image-5.15.0-1004-aws can not be marked as it is not installed.
linux-image-5.15.0-1003-ibm can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1002-oracle can not be marked as it is not installed.
linux-image-5.15.0-1004-gcp can not be marked as it is not installed.
linux-image-5.15.0-1005-aws can not be marked as it is not installed.
linux-image-2.6-rt can not be marked as it is not installed.
linux-image-5.15.0-1004-kvm can not be marked as it is not installed.
linux-image-5.17.0-1003-oem can not be marked as it is not installed.
linux-image-unsigned-5.15.0-25-generic can not be marked as it is not installed.
linux-image-5.15.0-1005-kvm can not be marked as it is not installed.
linux-image-unsigned-5.15.0-27-generic can not be marked as it is not installed.
linux-image-generic-hwe-22.04 was already set to automatically installed.
linux-image-virtual can not be marked as it is not installed.
linux-image-lowlatency-hwe-20.04-edge can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1002-gke can not be marked as it is not installed.
linux-image-lowlatency-hwe-22.04-edge can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1002-ibm can not be marked as it is not installed.
linux-image-extra-virtual-hwe-22.04 can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1003-azure can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1003-gcp can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1003-gke can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1004-aws can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1003-ibm can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1004-gcp can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1005-aws can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1004-kvm can not be marked as it is not installed.
linux-image-5.15.0-25-generic was already set to automatically installed.
linux-image-unsigned-5.17.0-1003-oem can not be marked as it is not installed.
linux-image-5.15.0-27-generic was already set to automatically installed.
linux-image-unsigned-5.15.0-1005-kvm can not be marked as it is not installed.
linux-image-oracle can not be marked as it is not installed.
linux-image-extra-virtual can not be marked as it is not installed.
linux-image-amd64 can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1003-oracle can not be marked as it is not installed.
linux-image-5.15.0-1003-azure can not be marked as it is not installed.
linux-image-oem-20.04 can not be marked as it is not installed.
linux-image-virtual-hwe-20.04-edge can not be marked as it is not installed.
linux-image-virtual-hwe-22.04-edge can not be marked as it is not installed.
linux-image-generic can not be marked as it is not installed.
linux-image-lowlatency-hwe-20.04 can not be marked as it is not installed.
linux-image-5.15.0-24-lowlatency can not be marked as it is not installed.
linux-image-unsigned-5.15.0-1005-azure can not be marked as it is not installed.
linux-image-virtual-hwe-20.04 can not be marked as it is not installed.
linux-image-5.15.0-1002-oracle can not be marked as it is not installed.
linux-image-oem-22.04 can not be marked as it is not installed.
linux-image-5.15.0-1005-azure can not be marked as it is not installed.
linux-image-generic-hwe-20.04 can not be marked as it is not installed.
```
keep in mind Not every answer is perfect, and it may not work for everyone. 

This one shows all kernels on the system minus the current running kernel.
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'

linux-generic-hwe-22.04
linux-headers-5.15.0-25
linux-headers-5.15.0-25-generic
linux-headers-generic-hwe-22.04
linux-image-5.15.0-25-generic
linux-image-generic-hwe-22.04
linux-modules-5.15.0-25-generic
linux-modules-extra-5.15.0-25-generic

```
Also what's different here from 20.04
```
cat /etc/apt/apt.conf.d/01autoremove
APT
{
  NeverAutoRemove
  {
	"^firmware-linux.*";
	"^linux-firmware$";
	"^linux-image-[a-z0-9]*$";
	"^linux-image-[a-z0-9]*-[a-z0-9]*$";
  };

  VersionedKernelPackages
  {
	# kernels
	"linux-.*";
	"kfreebsd-.*";
	"gnumach-.*";
	# (out-of-tree) modules
	".*-modules";
	".*-kernel";
  };

  Never-MarkAuto-Sections
  {
	"metapackages";
	"contrib/metapackages";
	"non-free/metapackages";
	"restricted/metapackages";
	"universe/metapackages";
	"multiverse/metapackages";
  };

  Move-Autobit-Sections
  {
	"oldlibs";
	"contrib/oldlibs";
	"non-free/oldlibs";
	"restricted/oldlibs";
	"universe/oldlibs";
	"multiverse/oldlibs";
  };
};
```

---

### Post by &amp;KyT$0P# on 2022-05-04
> **1fallen said:**
> why wouldn't something like this work:

[FONT=Courier New]apt-mark[/FONT] could work as a stopgap, but long term it would add more complexity to system maintenance compared to the set-and-forget nature of the previous tweak.

> keep in mind Not every answer is perfect, and it may not work for everyone.

I know.  My apologies for misinterpreting.

> Also what's different here from 20.04

That file is identical in 20.04 and 22.04.  Which I take as good news, since it means the "NeverAutoRemove" option - what the old way of protecting kernels used - still exists, so solving this might just be a matter of circumventing apt's active deletion of the old way of protecting kernels (if I'm reading right that there is such active deletion?).

Is that "NeverAutoRemove" option documented somewhere?  All I could find was a passing reference in [FONT=Courier New]/usr/share/doc/apt/examples/configure-index[/FONT] .  I would like to make sure it's not deprecated nor slated for removal.

---

### Post by #&amp;thj^% on 2022-05-04
@h2 I like your post's/threads they make me think past the normal.:KS
```
dpkg --get-selections | grep linux
console-setup-linux				install
libselinux1:amd64				install
linux-base					install
linux-firmware					install
linux-generic-hwe-22.04				install
linux-headers-5.15.0-25				install
linux-headers-5.15.0-25-generic			install
linux-headers-5.15.0-27				install
linux-headers-5.15.0-27-generic			install
linux-headers-generic-hwe-22.04			install
linux-image-5.15.0-25-generic			install
linux-image-5.15.0-27-generic			install
linux-image-generic-hwe-22.04			install
linux-modules-5.15.0-25-generic			install
linux-modules-5.15.0-27-generic			install
linux-modules-extra-5.15.0-25-generic		install
linux-modules-extra-5.15.0-27-generic		install
linux-sound-base				install
pptp-linux					install
util-linux					install

```

hold one
```
echo linux-generic-hwe-22.04 hold | sudo dpkg --set-selections
```
check:
```
dpkg --get-selections | grep linux-generic-hwe-22.04 
**linux-generic-hwe-22.04				hold**

```
The Apt::NeverAutoRemove is poorly documented in "apt.conf"

---

### Post by &amp;KyT$0P# on 2022-05-04
> **1fallen said:**
> hold one

So close.  If I do this manually, it works.  But if I try to do it in a script in [FONT=Courier New]/etc/kernel/postinst.d[/FONT] I get this error :(
```
dpkg: error: dpkg database lock was locked by another process with pid 2425
Note: removing the lock file is always wrong, and can end up damaging the
locked area and the entire system. See <https://wiki.debian.org/Teams/Dpkg/FAQ>.
E: Sub-process dpkg --set-selections returned an error code (2)
E: Executing dpkg failed. Are you root?
```

---

### Post by #&amp;thj^% on 2022-05-04
Goodness you would think I knew your script. :P
suggest only look at:
```
lsof /var/lib/dpkg/lock
```
Then make sure that process isn't running:

```
ps cax | grep PID
```
if it's runing kill
```
kill PID
#wait
kill -9 PID
```
Make sure process is done:
```

ps cax | grep PID
```

Then remove the lock file:

```
sudo rm /var/lib/dpkg/lock
```
is the proper way, not sure how you could script that.

To lookie loo's
This comes with a very Strong recommend, **Never remove a lockfile without killing all processes that have open file descriptors to it**.
Lock files are just metadata that prevent processes from running over each other or overwriting each other.

---

### Post by &amp;KyT$0P# on 2022-05-04
I think I got it now: it works if I invoke it from a file in [FONT=Courier New]/etc/apt/apt.conf.d/[/FONT] , like this -
```
DPkg::Post-Invoke {
  "if /usr/bin/test -x [COLOR="#FF0000"]/path/to/hold-third-latest-kernel[/COLOR];then [COLOR="#FF0000"]/path/to/hold-third-latest-kernel[/COLOR];else /bin/true;fi";
}
```

But that will run every time apt does *anything*, not just when a kernel is installed/removed.  So I put a script in both [FONT=Courier New]/etc/kernel/postinst.d[/FONT] and [FONT=Courier New]/etc/kernel/postrm.d[/FONT] to flag when this might need done -
```
#!/bin/sh
touch /run/update-third-kernel-hold-needed

```

Then I make the [FONT=Courier New]hold-third-latest-kernel[/FONT] script do nothing unless that file is present.

I still need to polish some details of the actual "determine and hold the third-latest kernel" script, but I'm sure enough that this method will work that I'm marking this solved.  Will post the script when I get it to the point I would try it in a production environment.

Thank you for your help 1fallen! :KS

---

### Post by #&amp;thj^% on 2022-05-04
Looking Great! Nicely done thus far. :D
Looking forward to final.

---

### Post by &amp;KyT$0P# on 2022-05-05
Here is the script that does the actual work of determining the third-latest installed kernel version and setting it on hold.  Based partially on 20.04 version of [FONT=Courier New]/etc/kernel/postinst.d/apt-auto-removal[/FONT] .  Thanks again 1fallen for the idea of using hold.
```
#!/bin/sh

# Hold the third-latest installed kernel version (as determined by debian version number)
# to mark it as not for autoremoval.
# apt already protects the latest and second-latest kernels, this is only needed for third-latest

if test $(id -u) -ne 0;then
  echo 'This script must be run as root' >&2
  exit 1
fi

runflagfile=/run/update-third-kernel-hold-needed
if test x"$1" != x'--force';then
  # Do not run if no kernels were changed
  # we must explicitly exit 0 here to avoid false indication of failure
  test -f "$runflagfile" || exit 0
fi

set -e

eval $(apt-config shell DPKG Dir::bin::dpkg/f)
test -n "$DPKG" || DPKG="/usr/bin/dpkg"

list="$("${DPKG}" -l | awk '/^[ih][^nc][ ]+linux-image-[0-9]+\./ && $2 !~ /-dbg(:.*)?$/ && $2 !~ /-dbgsym(:.*)?$/ { print $2,$3; }' \
   | sed -e 's#^linux-image-##' -e 's#:[^:]\+ # #')"
debverlist="$(echo "$list" | cut -d' ' -f 1 | sort --unique --reverse --version-sort)"

third_version="$(echo "$debverlist" | sed -n 3p)"

# grep exits with status 1 if no matches, don't stop the script for that here
set +e
for ver in $debverlist;do
  # only print changes
  apt-mark unhold "linux*${ver}*" | grep -F Cancel
done
set -e

if test -n "$third_version";then
  apt-mark hold $("${DPKG}" -l | awk '/^[ih][^nc][ ]+linux-[^ ]*'"$(echo "$third_version" | sed 's/\./\\./g')"'/ && $2 !~ /-dbg(:.*)?$/ && $2 !~ /-dbgsym(:.*)?$/ { print $2; }')
fi

# Clean the flag
rm -f "$runflagfile"
```

---

### Post by #&amp;thj^% on 2022-05-05
as your already aware, I make a lot of suggestions some favorable some not.
**Credit goes to you halogen2** for thinking past a mild frustration. <(Not every answer is perfect, and it may not work for everyone.)>
This finished script looks good, can't wait to test it myself.
Great Work, honsetly.

---

