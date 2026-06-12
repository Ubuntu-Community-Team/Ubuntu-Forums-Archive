---
title: "rebuilding deb with &quot;dpkg -b&quot; not working anymore"
date: 2016-01-25
forum: General Help
---

### Post by monkeybrain20122 on 2016-01-25
There are occasions when I would want to rebuild a .deb file (e.g fixing google-earth before) by changing the debian control file. 

The procedure is to open the .deb with file roller, edit the control file and then rebuild with the command "dpkg -b", but this doesn't work any more. There appears to be some changes in the way .debs are packaged and now there is no longer a DEBIAN folder which contains the control file, instead there is a tar.gz archive which contains the control file and a few other items. If I extract the tar.gz and edit the control file, then make a tar.gz again to replace the original and then use dpkg -b, it complains that there is no DEBIAN folder. If I add manually a DEBIAN folder with the control file and other contents of the tar.gz in  it, the .deb builds but if install it all the components are missing (just a few doc files are installed)

So what is the new procedure to rebuild a deb if one needs to? Thanks.

---

### Post by mc4man on 2016-01-25
Are you using 15.10?
If so file-roller extracts differently, likely a way around though won't have a linux install avail. till later or manana  to ck.
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1502652](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1502652)

---

### Post by mc4man on 2016-01-25
Just remembered I had some flash drives on me which had a script I've used for this stuff in the past. Attached
So extract, put in a bin folder in $PATH & mark script as executable.

To use - in terminal, 
editdeb /path/to/fullnameof.deb

That should open the control file in gedit. Make your edit, save, then close gedit. As soon as gedit closes it will produce a new .deb with modified added to name so will be seen as a minor upgrade, ect.

You can also read the script & if need be alter to suit.
(or use the other way to extract a .deb as used in script, dpkg-deb -x

---

### Post by monkeybrain20122 on 2016-01-26
> **mc4man said:**
> Are you using 15.10?
If so file-roller extracts differently, likely a way around though won't have a linux install avail. till later or manana  to ck.
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1502652](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1502652)

Yes, that is exactly what I am seeing. Added an affected me too to the bug. Thanks for the script!

---

