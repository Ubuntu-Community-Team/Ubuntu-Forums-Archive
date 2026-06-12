---
title: "vmware won't uninstall"
date: 2006-10-17
forum: General Help
---

### Post by EnderTheThird on 2006-10-17
Somehow, I think trying to install qtorrent borked my vmware-player installation.  When installing qtorrent (or maybe some related dependencies), it overwrote some of the vmware files.  But now I can't remove vmware-player.  When I try, I get the following:

```

Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

And that's all it shows before putting me back into the CLI.  The problem is that I can't install any other software without fixing that one broken package.  I installed vmware-player via Automatix2, and I believe it installed fine because I'm able to start it up (even now) without any problems.  Any ideas?  If you need any more information, let me know.

Edit:  This is on Edgy Beta with the latest updates.

---

