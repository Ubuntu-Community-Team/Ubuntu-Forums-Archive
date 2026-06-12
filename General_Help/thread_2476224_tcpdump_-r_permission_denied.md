---
title: "tcpdump -r permission denied"
date: 2022-06-20
forum: General Help
---

### Post by ychaouche on 2022-06-20
Dear all, 

I just learned a few minutes ago that you can't open a file in *tcpdump* unless the file extension is exactly *pcap*. 
Anything else and *Apparmor* will prevent you from running *tcpdump*. 

Anyone familiar with *Apparmor* would like to discuss this?

---

### Post by Doug S on 2022-06-20
Which version of Ubuntu? I do not seem to have your issue.

On my 20.04.4 Ubuntu test Server I ran this command for a few minutes:

```
doug@s19:~/tcpdump$ sudo tcpdump --buffer-size=16384 -w 'ext-%F-%H-%M-%S.bin' -G 61 -Z doug
```

got this:

```
doug@s19:~/tcpdump$ ls -l ext*
-rw-r--r-- 1 doug doug  38435 Jun 20 07:04 ext-2022-06-20-07-03-27.bin
-rw-r--r-- 1 doug doug  29660 Jun 20 07:05 ext-2022-06-20-07-04-28.bin
-rw-r--r-- 1 doug doug   6472 Jun 20 07:06 ext-2022-06-20-07-05-29.bin
-rw-r--r-- 1 doug doug   4751 Jun 20 07:07 ext-2022-06-20-07-06-33.bin
-rw-r--r-- 1 doug doug   4662 Jun 20 07:08 ext-2022-06-20-07-07-35.bin
-rw-r--r-- 1 doug doug  32545 Jun 20 07:09 ext-2022-06-20-07-08-56.bin
-rw-r--r-- 1 doug doug 114210 Jun 20 07:10 ext-2022-06-20-07-09-57.bin
```

and post-processed with this:

```
doug@s19:~/tcpdump$ for f in ext*.bin; do tcpdump -n -tttt -r $f >>alle.txt ; done
```

and got this:

```
doug@s19:~/tcpdump$ ls -l *.txt
-rw-rw-r-- 1 doug doug 153427 Jun 20 07:12 alle.txt
```

My apparmor status is this:

```
doug@s19:~/tcpdump$ sudo aa-status
[sudo] password for doug:
apparmor module is loaded.
16 profiles are loaded.
16 profiles are in enforce mode.
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   [COLOR="#FF0000"]/usr/sbin/tcpdump[/COLOR]
   /{,usr/}sbin/dhclient
   libvirtd
   libvirtd//qemu_bridge_helper
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   virt-aa-helper
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode.
   /usr/sbin/libvirtd (986) libvirtd
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

Could you post your "/etc/apparmor.d/usr.sbin.tcpdump" file and if you have one "/etc/apparmor.d/local/usr.sbin.tcpdump".

Or just put apparmor for tcpdump into complain mode instead of enforce mode (I think, untested):

```
sudo aa-complain /usr/sbin/tcpdump
```

EDIT: My main Debian server, where I run 2 instances of tcpdump 100% of the time has apparmor in complain mode (all I recall it that there are file access issues in enforce mode):

```
doug@s15:~/diag/history$ sudo aa-status
apparmor module is loaded.
15 profiles are loaded.
10 profiles are in enforce mode.
   /usr/bin/man
   libvirtd
   libvirtd//qemu_bridge_helper
   lsb_release
   man_filter
   man_groff
   named
   nvidia_modprobe
   nvidia_modprobe//kmod
   virt-aa-helper
[COLOR="#FF0000"]5 profiles are in complain mode.[/COLOR]
   [COLOR="#FF0000"]tcpdump[/COLOR]
   tcpdump//null-/home/doug/bin/packet_post_processor_ext
   tcpdump//null-/home/doug/bin/packet_post_processor_ext//null-/usr/bin/tcpdump
   tcpdump//null-/home/doug/bin/packet_post_processor_int
   tcpdump//null-/home/doug/bin/packet_post_processor_int//null-/usr/bin/tcpdump
4 processes have profiles defined.
2 processes are in enforce mode.
   /usr/sbin/libvirtd (570) libvirtd
   /usr/sbin/named (510) named
[COLOR="#FF0000"]2 processes are in complain mode.
   /usr/bin/tcpdump (72827) tcpdump
   /usr/bin/tcpdump (72835) tcpdump[/COLOR]
0 processes are unconfined but have a profile defined.
```

---

### Post by ychaouche on 2022-06-21
Hello @DougS.

Here's my apparmor file

```
ychaouche#ychaouche-PC 10:43:02 ~ $ pretty.remove.blanks+comments.nl /etc/apparmor.d/usr.sbin.tcpdump                
     1  /usr/sbin/tcpdump {
     2    capability net_raw,
     3    capability setuid,
     4    capability setgid,
     5    capability dac_override,
     6    network raw,
     7    network packet,
     8    capability sys_module,
     9    @{PROC}/bus/usb/ r,
    10    @{PROC}/bus/usb/** r,
    11    @{PROC}/[0-9]*/net/dev r,
    12    /sys/bus/usb/devices/ r,
    13    /sys/class/net/ r,
    14    /sys/devices/**/net/* r,
    15    capability net_admin,
    16    /dev/usbmon* r,
    17    /dev/bus/usb/ r,
    18    /dev/bus/usb/** r,
    19    /etc/ethers r,
    20    /dev/bus/usb/**/[0-9]* w,
    21    /{usr/,}bin/gzip ixr,
    22    /{usr/,}bin/bzip2 ixr,
    23    audit deny @{HOME}/.* mrwkl,
    24    audit deny @{HOME}/.*/ rw,
    25    audit deny @{HOME}/.*/** mrwkl,
    26    audit deny @{HOME}/bin/ rw,
    27    audit deny @{HOME}/bin/** mrwkl,
    28    owner @{HOME}/ r,
    29    owner @{HOME}/** rw,
    30    /**.[pP][cC][aA][pP] rw,
    31    /var/log/snort/*log* r,
    32    /usr/sbin/tcpdump mr,
    33  }
ychaouche#ychaouche-PC 10:43:28 ~ $ 

```

```

ychaouche#ychaouche-PC 10:43:28 ~ $ nl /etc/apparmor.d/usr.sbin.tcpdump              
     1  # vim:syntax=apparmor
     2  # Last Modified: Wed Feb  3 07:58:30 2009
     3  # Author: Jamie Strandboge <jamie@canonical.com>
     4  #include <tunables/global>

     5  /usr/sbin/tcpdump {
     6    #include <abstractions/base>
     7    #include <abstractions/nameservice>
     8    #include <abstractions/user-tmp>

     9    capability net_raw,
    10    capability setuid,
    11    capability setgid,
    12    capability dac_override,
    13    network raw,
    14    network packet,

    15    # for -D
    16    capability sys_module,
    17    @{PROC}/bus/usb/ r,
    18    @{PROC}/bus/usb/** r,

    19    # for finding an interface
    20    @{PROC}/[0-9]*/net/dev r,
    21    /sys/bus/usb/devices/ r,
    22    /sys/class/net/ r,
    23    /sys/devices/**/net/* r,

    24    # for -j
    25    capability net_admin,

    26    # for tracing USB bus, which libpcap supports
    27    /dev/usbmon* r,
    28    /dev/bus/usb/ r,
    29    /dev/bus/usb/** r,

    30    # for init_etherarray(), with -e
    31    /etc/ethers r,

    32    # for USB probing (see libpcap-1.1.x/pcap-usb-linux.c:probe_devices())
    33    /dev/bus/usb/**/[0-9]* w,

    34    # for -z
    35    /{usr/,}bin/gzip ixr,
    36    /{usr/,}bin/bzip2 ixr,

    37    # for -F and -w
    38    audit deny @{HOME}/.* mrwkl,
    39    audit deny @{HOME}/.*/ rw,
    40    audit deny @{HOME}/.*/** mrwkl,
    41    audit deny @{HOME}/bin/ rw,
    42    audit deny @{HOME}/bin/** mrwkl,
    43    owner @{HOME}/ r,
    44    owner @{HOME}/** rw,

    45    # for -r, -F and -w
    46    /**.[pP][cC][aA][pP] rw,

    47    # for convenience with -r (ie, read pcap files from other sources)
    48    /var/log/snort/*log* r,

    49    /usr/sbin/tcpdump mr,

    50    # Site-specific additions and overrides. See local/README for details.
    51    #include <local/usr.sbin.tcpdump>
    52  }
ychaouche#ychaouche-PC 10:43:36 ~ $
```

My distro is linux mint based off Trusty Tahr -14.04-

```

ychaouche#ychaouche-PC 10:46:44 ~ $ cat /etc/os-release
NAME="Ubuntu"
VERSION="14.04.6 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.6 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
ychaouche#ychaouche-PC 10:46:47 ~ $

```

I'd like to emphasis that this is not a support question, rather a discussion about why AppArmor cares about file extensions
and do file extensions represent any security threats that AppArmor is trying to counter. 

I just changed my filename to filename.pcap and moved on, but I'm curious and open to discussion.

---

### Post by ychaouche on 2022-06-21
The local file is empty
```

ychaouche#ychaouche-PC 11:29:02 ~ $ cat /etc/apparmor.d/local/usr.sbin.tcpdump # Site-specific additions and overrides for usr.sbin.tcpdump.
# For more details, please see /etc/apparmor.d/local/README.
ychaouche#ychaouche-PC 11:29:35 ~ $

```

---

### Post by Doug S on 2022-06-21
If I change the command I was using for my examples, then I do get your issue, and I observe the same apparmor requirement in the file:

```
    45    # for -r, -F and -w
    46    /**.[pP][cC][aA][pP] rw,

```

and actually the 2nd attempt to create the output file for per time mode fails:

```
doug@s19:~/tcpdump$ sudo tcpdump -w 'ext-%F-%H-%M-%S.pcap' -G 61
tcpdump: listening on enp3s0, link-type EN10MB (Ethernet), capture size 262144 bytes
tcpdump: ext-2022-06-21-08-15-40.pcap: Permission denied
```
whereas the first file was fine:

```
doug@s19:~/tcpdump$ ls -l
total 54820
-rw-r--r-- 1 tcpdump tcpdump    33843 Jun 21 07:58 ext-2022-06-21-07-58-13.bin
-rw-r--r-- 1 tcpdump tcpdump 28421037 Jun 21 08:00 ext-2022-06-21-07-59-06.bin
-rw-r--r-- 1 tcpdump tcpdump    13818 Jun 21 08:01 ext-2022-06-21-08-00-39.bin
[COLOR="#FF0000"]-rw-r--r-- 1 tcpdump tcpdump 27660173 Jun 21 08:15 ext-2022-06-21-08-14-39.pcap[/COLOR]
```

I can see why when I use the change the owner of the file method it works, as that is specifically allowed in the apparmor file:

```
doug@s19:~/tcpdump$ sudo tcpdump -w 'ext-%F-%H-%M-%S.pcap' -G 61 [COLOR="#FF0000"]-Z doug[/COLOR]
tcpdump: listening on enp3s0, link-type EN10MB (Ethernet), capture size 262144 bytes
```

gives:
```
doug@s19:~/tcpdump$ ls -l
total 27060
-rw-r--r-- 1 tcpdump tcpdump 27660173 Jun 21 08:15 ext-2022-06-21-08-14-39.pcap
-rw-r--r-- 1 doug    doug       24724 Jun 21 08:30 ext-2022-06-21-08-29-22.pcap
-rw-r--r-- 1 doug    doug       15472 Jun 21 08:31 ext-2022-06-21-08-30-23.pcap
-rw-r--r-- 1 doug    doug        4096 Jun 21 08:31 ext-2022-06-21-08-31-24.pcap
```

Anyway, moving on to your actual questions: I don't know, but I can not see why it matters what extension is used. Sometimes I find apparmor overly restrictive and just put it into complain mode.

---

