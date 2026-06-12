---
title: "vmware left for dead by edgy"
date: 2006-10-27
forum: General Help
---

### Post by evilhomer on 2006-10-27
ok, title's a little dramatic, but u gotta get people to read, right? :)

had vmserver installed and working fine in dapper.  upgraded to edgy, some minor issues, nothing major, went fine.  did vmware-config.pl and it worked perfectly w/new kernel.  goto start vmware and goes to 100% processor load and sits there.  never starts.

uninstall/reinstall then run vmware-config.pl again, and it looks but, but same thing, never starts.

i dunno what to do after that.  any ideas?

---

### Post by nix4me on 2006-10-27
i installed vmware server on my edgy box just fine.  I didn't upgrade but installed from scratch.

nix4me

---

### Post by ~LoKe on 2006-10-27
Installed it on the Edgy RC, works ever since.

---

### Post by evilhomer on 2006-10-28
removed vmserver, then installed vmplayer from the repos.  it won't start either! (but it's not running still - proc not @100%)  any advice??

---

### Post by evilhomer on 2006-10-28
well, removing vmplayer and then reinstalling vmserver worked on both my comps.  go figure!

vmserver no longer fits the theme, but it works.  hope this can help somebody.

---

### Post by matt91 on 2006-10-28
does the same here, i uninstalled and reinstalled and is still the same. i tried starting from console and this is what i get:
> 
root@ubuntu-pc2:/usr/local/vmware/bin# ./vmware
/usr/local/vmware/lib/bin/vmware: /usr/local/vmware/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


---

### Post by mikeyrb on 2006-10-28
I've been using the following command to start the console:

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware

---

### Post by Bo Rosén on 2006-10-28
I found this answer on the [VMware forum]("http://www.vmware.com/community/thread.jspa?threadID=59112&tstart=0") that solved the problem for me.

> 
The problem is with libdbus library. If it has two versions installed, namely libdbus-1.so.2 and libdbus-1.so.3, vmware will not work. Remove the package: 

root@random:~# apt-get remove libdbus-1-2                      


---

### Post by evilhomer on 2006-10-28
good find!  thanks for the additional info.

but now I have another issue.  I see my vmware-player wasn't actually removed.  It's status is 'broken'  The kernel modules removed, but the player's still there.  I can't remove it, no matter what I do, and I can't install it properly either.

i get something like this when using apt-get now:
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1

i'm stumped (again) ](*,)

---

### Post by evilhomer on 2006-10-29
fixed it (sheesh!)  uninstalled server, then installed the tar'd version of vmplayer from vmware.com, then removed vmplayer using apt-get, then uninstalled the tar'd version of vmplayer, then installed vmserver.  my work here is done... hahah

---

### Post by chewie124 on 2006-10-29
Removing libdbus-1-2 solved the issue for me too with vmware-workstation!  Thanks for the tip.

Incidentally, it also removed libnautilus-burn3 - is that going to screw up my capability to burn CD's?

---

### Post by Bo Rosén on 2006-10-30
I'm glad the tip helped people. 
I don't think you need libnautilus-burn3, Edgy seems to include libnautilus-burn4 and I have no problems burning.

---

### Post by deba on 2006-11-08
I to have had the same problem after upgrading to edgy, but my systems says libdbus-1-2 is not installed? wot to do now?

---

### Post by neversfelde on 2007-02-03
Same here.

---

