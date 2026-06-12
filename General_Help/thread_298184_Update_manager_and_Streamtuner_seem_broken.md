---
title: "Update manager and Streamtuner seem broken"
date: 2006-11-12
forum: General Help
---

### Post by joegumbo on 2006-11-12
Hi,

     I'm running a dual boot system Ubuntu 6.10 Edgy with Windows Media Edition using Comcast Cable High speed internet service..  Yesterday, I booted into Windows to install a program.  I then booted back into Ubuntu.  

     After booting back into ubuntu, I've developed two problems..

First, when  I click on and try to install the latest avahi udates, I receive the following output:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/a/avahi/python-avahi_0.6.13-2ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/a/avahi/python-avahi_0.6.13-2ubuntu2.2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/a/avahi/avahi-discover_0.6.13-2ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/a/avahi/avahi-discover_0.6.13-2ubuntu2.2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.13-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.13-2ubuntu2.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Also,  when I try to Reload the lsit in Streamtuner, I'm notified that :
Unable to reload.  couldn't connect to host.

I've tried unplugging and plugging in my cable modem to reset it.  I still have the same issues.

However, everything else seems to work just fine.  I can surf the net, get my email, etc.

Thanks,
-Joe

---

### Post by joegumbo on 2006-11-13
I un-installed anon-proxy, then rebooted.  I can update now.

-Joe G

---

