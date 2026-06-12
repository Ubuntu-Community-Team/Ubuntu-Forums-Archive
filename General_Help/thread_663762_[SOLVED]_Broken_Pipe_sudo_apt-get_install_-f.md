---
title: "[SOLVED] Broken Pipe???? sudo apt-get install -f"
date: 2008-01-10
forum: General Help
---

### Post by aonegodman on 2008-01-10
):P  Following copy from Terminal:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
cdda2wav libswscalecvs0 libavformatcvs51 ogmtools ffmpeg libmjpegtools0c2a
mpgtx mkvtoolnix libimlib2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
20 not fully installed or removed.
Need to get 0B/209kB of archives.
After unpacking 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140119 files and directories currently installed.)
[B]Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

I have ran:

sudo apt-get clean
sudo apt-get update - found a double entry in sources.list that I corrected. Ran again.
sudo apt-get -f install

Still get same error above and need to find a solution. Thanks!

---

### Post by umuro on 2008-01-11
Try this

cd /var/cache/apt/archieves
ls

If your *.deb file is not there redownload it

sudo aptitude download libmjpegtools0

The FORCE an installation
sudo dpkg -i --force-all libmjpegtools*.deb

-------------------

For any package, you can use "dpkg -i --force-all" when ever you meet an "dpkg error processing .... (Broken pipe)". The package will install. And the complaints will be silenced. And you will be ok if the new package is working!

---

