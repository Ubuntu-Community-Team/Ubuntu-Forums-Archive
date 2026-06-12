---
title: "Error: Can't read MAC address on interface /dev/net/tapN"
date: 2004-11-30
forum: General Help
---

### Post by karih on 2004-11-30
Not having a clue where to post this so feel free to move it.

I have an error at boot time, which prints something like this:
```
Error: Can't read MAC address on interface `/dev/net/tap7' : No such device
Interface name is `eth0' at line 2, can't be mapped reliably.
```This message is repeated 15 times, with the only difference being the number after tap (tapN) changing.

*This error doesn't seem to have any noticable effect, at least I see nothing missing or anything going wrong*, but still I would like to know what the heck this is.

After some rebooting I found that this message is coming from the script /etc/init.d/udev and seems to be coming from one of these lines:```

      $UDEVSTART
    make_extra_nodes
```
The function make_extra_nodes is as follows:```

make_extra_nodes () {
  grep '^[^#]' /etc/udev/links.conf | \
  while read type name arg1; do
    [ "$type" -a "$name" -a ! -e "/dev/$name" -a ! -L "/dev/$name" ] ||continue
    case "$type" in
    L)
      ln -s $arg1 /dev/$name
      ;;
    D)
      mkdir -p /dev/$name
      ;;
    M)
      mknod --mode=600 /dev/$name $arg1
      ;;
    *)
      log_warning_msg "Unparseable line ($type $name $arg1)"
      ;;
    esac
  done
}
```
What seems strange to me is that there is no mention of tap or net in the file /etc/udev/links.conf and I can't exactly see why and how it is printing out.
Doing grep tap * | grep net in /etc/udev outputted:
```
devfs.rules:KERNEL="tap*",              NAME="net/%k"
udev.rules:KERNEL="tap*",               NAME="net/%k"
```...and these files make little sens to me.  I've now totally lost it, why and how this error is coming.  Running kernel 2.6.8.1 (compiled my own).  
Any help is as always apprecited.  Thanks in advance!

---

