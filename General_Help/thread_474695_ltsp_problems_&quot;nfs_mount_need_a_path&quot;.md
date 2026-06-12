---
title: "ltsp problems &quot;nfs mount: need a path&quot;"
date: 2007-06-15
forum: General Help
---

### Post by mopey on 2007-06-15
I am running a Feisty 64 server and am setting up i386 thin clients using ltsp.

I followed the wiki here (very short and straight forward): [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

except that instead of

```
sudo ltsp-build-client
```

I used

```
sudo ltsp-build-client --arch i386
```

At this point, dhcp seems to be working.  When I netboot the client, it receives an address.

Also, TFTPD seems to be working.  The client is booting a Linux kernel.  It gets to an Ubuntu splash screen, and when I press ctrl+alt+F1, flashing across the screen is "nfs mount: need a path" along with some IP-Config messages.

Here is my /etc/ltsp/dhcpd.conf
```

$ cat /etc/ltsp/dhcpd.conf 

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "stupid.university.edu";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}

```

I have played a little with the 'option root-path "/opt/ltsp/i386";' line.  I tried things like taking out the /opt (there is a -s, and that's how the other stuff is mounted so it was worth  a shot in the dard), adding a trailing /, but no luck.    

portmap, nfsd, and mountd are all running

```
$ ps -e |grep portmap
 5639 ?        00:00:00 portmap

$ ps -e |grep nfsd

 6673 ?        00:00:00 nfsd4
 6674 ?        00:00:00 nfsd
 6675 ?        00:00:00 nfsd
 6676 ?        00:00:00 nfsd
 6677 ?        00:00:00 nfsd
 6678 ?        00:00:00 nfsd
 6679 ?        00:00:00 nfsd
 6680 ?        00:00:00 nfsd
 6681 ?        00:00:00 nfsd

$ ps -e |grep mountd
 6685 ?        00:00:00 rpc.mountd

```

I'm not sure what to even try next.  Any ideas?  Thanks.

---

### Post by mopey on 2007-06-15
Progress:

Sure enough, it is a bad option: root-path line in the dhcpd.conf file.  I tested by putting a bogus one in there.  "/blah" and I get the same crap.

I'll keep playing around with that to see if I can get it working.

The default one _seems_ like it should be right though.  

My root is actually located at '/opt/ltsp/i386'.  

```

$ls /opt/ltsp/i386
bin   dev  home    lib    mnt  proc  sbin  sys  usr
boot  etc  initrd  media  opt  root  srv   tmp  var

```

hmmm.

---

### Post by mopey on 2007-06-15
I've tried junk like 

```

option root-path "192.168.0.1:/opt/ltsp/i386";

```

and variations on that with no luck.

Anyone?  Am I missing something?

---

### Post by mopey on 2007-06-15
Ok, I finally figured it out.  This was a frustrating freaking problem to say the least.

For some reason, although my dhcpd.conf file was as above, the clients were getting ips in the 192.168.1 range.  Weird.

Anyway, I changed all the IPs to match with what the clients were getting (I changed all the 192.168.0s to 192.168.1s), and it worked.  It's weird because nothing as far as I can tell was configured to be 192.168.1 in the first place.

Oh well.  I'm glad it works.

---

