---
title: "LFTP tries to open 10 segmented transfers but Filezilla Server doesn't care"
date: 2014-06-07
forum: General Help
---

### Post by Rsxhawk on 2014-06-07
I recently installed LFTP to test out its multi-segmented (if thats the right verbage) file transfers but upon initiating a file transfer with the "pget -n 10 <filename>" command it only ends up being allowed one connection, I can see the ftp server log populate with multiple connection attempts but only one stream is allowed.  A buddy of mine told me I needed to use "pget -n=10 <filename>" but that does not work, it errors out saying its expecting a number.  I did some light research on the filezilla forums and from what I can tell, segmented downloads aren't supported.  They obviously allow more than one file to be downloaded at the same time, but as for splitting up 1 large file into several different connections, it doesn't look like it.  

Getting connected isn't a problem, I use FTPS and the server is accessible locally and externally via port forwarding.

Topology:

Ubuntu 12.04 Host operating system running command line LFTP client -------> Windows 7 virtual machine running Filezilla Server (hosted on the Ubuntu Desktop via vmware workstation 9)

With that said, is there another ftp server you all would recommend that would allow for such transfers?  What do you use with LFTP?

---

