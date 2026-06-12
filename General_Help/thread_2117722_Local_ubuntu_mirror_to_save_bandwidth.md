---
title: "Local ubuntu mirror to save bandwidth"
date: 2013-02-19
forum: General Help
---

### Post by kbensch on 2013-02-19
Hi

I am trying to setup an internal ubuntu mirror. I have a lot of information, but this distro is really doing my head in in more than one way. Whats easy on CentOS is not easy on ubuntu.

Heres the issue: 

I run 

debmirror -a amd64 --no-source --md5sums --progress --passive --verbose --ignore-release-gpg --no-check-gpg -s main,multiverse,universe,restricted -h uk.archive.ubuntu.com -d precise,precise-security,precise-updates -r /ubuntu -e http /mirrors/ubuntu


And get this:

Mirroring to /mirrors/ubuntu from [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)
Arches: i386,amd64
Dists: sid,precise,precise-security,precise-updates
Sections: main,main/debian-installer,contrib,non-free,main,multiverse,universe,restricted
Pdiff mode: use
Veriftying checksums.
Not checking Release gpg signatures.
Passive mode on.
Will clean up after mirroring.
Attempting to get lock ...
Updating remote trace files (using rsync) ...
Welcome to the Ubuntu Archive mirror rsync server.

This server is located in London, United Kingdom.

If you are not an Ubuntu official country mirror, please consider
using a Ubuntu archive mirror closer to your physical location.

This server has limited resources.  A list of Ubuntu archive mirrors
which support rsync can be found here:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

If you host an Ubuntu mirror, public or private, please register your
mirror in Launchpad if you have not already done so.

Registrations can be made here:

[https://launchpad.net/ubuntu/+newmirror](https://launchpad.net/ubuntu/+newmirror)

If you require assistance with your public mirror, please contact the
Ubuntu mirror team at the following address:

[email]mirrors@ubuntu.com[/email]

--

receiving incremental file list
./
project/trace/atemoya.canonical.com
          29 100%   28.32kB/s    0:00:00 (xfer#1, to-check=6/10)
project/trace/bignay.canonical.com
          29 100%    4.72kB/s    0:00:00 (xfer#2, to-check=5/10)
project/trace/cocoplum.canonical.com
          29 100%    4.72kB/s    0:00:00 (xfer#3, to-check=4/10)
project/trace/pepo.canonical.com
          29 100%    4.72kB/s    0:00:00 (xfer#4, to-check=3/10)
project/trace/sadashbia.canonical.com
          29 100%    4.72kB/s    0:00:00 (xfer#5, to-check=2/10)
project/trace/sadashbia.canonical.com.dists-timestamps
      272638 100%   28.89MB/s    0:00:00 (xfer#6, to-check=1/10)
project/trace/ugni.canonical.com
          29 100%    3.15kB/s    0:00:00 (xfer#7, to-check=0/10)

sent 2637 bytes  received 2943 bytes  11160.00 bytes/sec
total size is 272812  speedup is 48.89
Getting meta files ...
[  0%] Getting: dists/sid/Release...     #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/sid/Release](http://uk.archive.ubuntu.com/ubuntu/dists/sid/Release) ==> 404 Not Found
failed 404 Not Found
[  0%] Getting: dists/precise/Release...         #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise/Release](http://uk.archive.ubuntu.com/ubuntu/dists/precise/Release) ==> 200 OK
ok
[  0%] Getting: dists/precise/Release.gpg...     #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg) ==> 200 OK
ok
Ubuntu Release file: using Suite (precise).
[  0%] Getting: dists/precise-security/Release...        #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise-security/Release](http://uk.archive.ubuntu.com/ubuntu/dists/precise-security/Release) ==> 200 OK
ok
[  0%] Getting: dists/precise-security/Release.gpg...    #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg) ==> 200 OK
ok
Ubuntu Release file: using Suite (precise-security).
[  0%] Getting: dists/precise-updates/Release...         #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://uk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release) ==> 200 OK
ok
[  0%] Getting: dists/precise-updates/Release.gpg...     #** GET [http://uk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg) ==> 200 OK
ok
Ubuntu Release file: using Suite (precise-updates).
Errors:
 Download of dists/sid/Release failed: 404 Not Found
Failed to download some Release or Release.gpg files!
releasing 1 pending lock... at /usr/share/perl5/vendor_perl/LockFile/Simple.pm line 206.


Why does it not work. Can anybody help please?

---

### Post by dino99 on 2013-02-19
That howto might help:
[http://lgallardo.com/en/2012/12/06/como-crear-un-mirror-de-debian-y-ubuntu-con-debmirror/](http://lgallardo.com/en/2012/12/06/como-crear-un-mirror-de-debian-y-ubuntu-con-debmirror/)

---

