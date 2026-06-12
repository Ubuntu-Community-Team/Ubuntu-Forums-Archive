---
title: "Grub menu making a return on Ubuntu 24.04"
date: 2024-05-06
forum: General Help
---

### Post by laserburn2 on 2024-05-06
So many previous versions of Ubuntu were not showing grub menu, but it came back on 24.04, with 30 seconds timeout.

From /boot/grub/grub.cfg:

```

terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30

```

That condition seems to be active because of this part here:

```

function recordfail {
  set recordfail=1
  # GRUB lacks write support for zfs, so recordfail support is disabled.
}

```

The source of this timeout setting appears to be /etc/grub.d/00_header [ATTACH]293735[/ATTACH], but code there gets complicated. I'm wondering how I could reduce the timeout counter or possibly boot without displaying the grub menu.

---

### Post by laserburn2 on 2024-05-06
I thing that this should be some sort of protection for systems with zfs and uefi to force grub menu to appear. But my earlier Ubuntu also used zfs and had hidden boot. I wonder if it has something to do with it having zsys. :-k

Anyway, what seems to be most obvious is altering GRUB_RECORDFAIL_TIMEOUT, but I'm curious why it has value -30? I think -1 should mean wait forever, 0 is for don't wait.

---

### Post by laserburn2 on 2024-05-18
To answer myself, I had to change this part in /etc/grub.d/00_header to reduce the timeout to 5 seconds:

if [ \$grub_platform = efi ]; then
  set timeout=${GRUB_RECORDFAIL_TIMEOUT:-5}

Don't ask me why it's negative 5, I have no idea. Changing GRUB_RECORDFAIL_TIMEOUT value in other parts of the file will change the default timeout value is boot.cfg, but the part where the efi boot is mentioned is the one that will be active.

---

### Post by MAFoElffen on 2024-05-18
What?

Mine (without comments and blank lines):
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep -v '^\s*$\|^\s*\#' /etc/default/grub 
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=show
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash kvm-intel.nested=1 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank intel_iommu=on systemd.unified_cgroup_hiercharchy=0 intremap=no_x2apic_optout nox2apic"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1280x1024x32
GFX_PAYLOAD=KEEP
GRUB_DISABLE_OS_PROBER=false
mafoelffen@Mikes-ThinkPad-T520:~$ sudo zpool list
NAME      SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
backups  1.46T   224G  1.24T        -         -     0%    14%  1.00x    ONLINE  -
bpool    1.88G   767M  1.13G        -         -     1%    39%  1.00x    ONLINE  -
dpool     856G  2.70M   856G        -         -     0%     0%  1.00x    ONLINE  -
hpool     396G  64.9G   331G        -         -    13%    16%  1.00x    ONLINE  -
kpool     992G   495G   497G        -         -     1%    49%  1.00x    ONLINE  -
rpool     496G  29.1G   467G        -         -     2%     5%  1.00x    ONLINE  -

```
Another of mine:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=show
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on iommu=pt i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0 systemd.unified_cgroup_hierarchy=0 libata.force=noncq"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
mafoelffen@Mikes-B460M:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   306M  1.58G        -         -     1%    15%  1.00x    ONLINE  -
datapool  9.09T  2.37T  6.72T        -         -     7%    26%  1.00x    ONLINE  -
kpool     7.27T  3.40T  3.87T        -         -     0%    46%  1.00x    ONLINE  -
rpool      920G  19.5G   901G        -         -     1%     2%  1.00x    ONLINE  -

```
Am I missing something you are trying to point out (related to Grub2 and ZFS-On-Root)?

---

