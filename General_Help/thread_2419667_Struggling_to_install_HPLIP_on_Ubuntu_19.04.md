---
title: "Struggling to install HPLIP on Ubuntu 19.04"
date: 2019-05-24
forum: General Help
---

### Post by jonathanbossenger on 2019-05-24
Hi folks

I'm struggling to install HPLIP on my new Ubuntu 19.04 install. 

Steps I've followed

Downloaded 

hplip-3.19.5-plugin.run
hplip-3.19.5-plugin.run.asc
hplip-3.19.5.run

To a folder called hplip. Within that folder I run the hplip-3.19.5.run file

```

chmod +x hplip-3.19.5.run
./hplip-3.19.5.run

```

We get to the step to install the plugin, I select the download option, and it fails

```

-------------------
| DOWNLOAD PLUGIN |
-------------------


Checking for network connection...
Downloading plug-in from: 
Downloading plug-in: [\                                                                                                                                                                      ] 0% Receiving digital keys: /usr/bin/gpg --homedir /home/jonathan/.hplip/.gnupg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0x4ABA2F66DBD5A95894910E0673D770CDA59047B9
()
error: Unable to recieve key from keyserver

```

So then I try the manual install option

```

Enter option (d=download*, p=specify path, q=quit) ? p
Enter the path to the 'hplip-3.19.5-plugin.run' file (q=quit) : /home/jonathan/Downloads/hplip/hplip-3.19.5-plugin.run


---------------
| COPY PLUGIN |
---------------


Downloading plug-in from: file:///home/jonathan/Downloads/hplip/hplip-3.19.5-plugin.run
Downloading plug-in: [\                                                                                                                                                                      ] 0%  1100%Receiving digital keys: /usr/bin/gpg --homedir /home/jonathan/.hplip/.gnupg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0x4ABA2F66DBD5A95894910E0673D770CDA59047B9
()
error: Unable to recieve key from keyserver
Do you still want to install the plug-in? (y=yes, n=no*, q=quit) ? y


----------------------
| INSTALLING PLUG-IN |
----------------------


Creating directory plugin_tmp
Verifying archive integrity... All good.
Uncompressing HPLIP 3.19.5 Plugin Self Extracting ArchiveExtraction failed.
.Terminated
error: Python gobject/dbus may be not installed
\
gzip: stdout: Broken pipe
 
Done.

```

Anyone have any ideas why I can't install the plugin?

---

### Post by Frogs Hair on 2019-05-24
Hello:

I am running Budgie 19.04 and I downloaded the run file per this [instruction]("http://ubuntuhandbook.org/index.php/2019/05/hplip-3-19-5-released-with-ubuntu-19-04-64-bit-support/"). The file was then made executable and run it in the terminal. I followed the instructions in the terminal. You may want to remove/purge the current version of HPLIP first or you will be prompted to do so during the installation. This takes some time to complete.

---

### Post by CatKiller on 2019-05-25
Why not just use the version in the repositories?

---

### Post by Frogs Hair on 2019-05-25
The new version of HPLIP supports some of the latest printers.
 ```
**Added support for the following new Printers:**
-HP LaserJet Enterprise M507n 
-HP LaserJet Enterprise M507dn
-HP LaserJet Enterprise M507x
-HP LaserJet Enterprise M507dng
-HP LaserJet Managed E50145dn
-HP LaserJet Managed E50145x
-HP LaserJet Enterprise MFP M528dn
-HP LaserJet Enterprise MFP M528f
-HP LaserJet Enterprise Flow MFP M528c
-HP LaserJet Enterprise Flow MFP M528z
-HP LaserJet Managed MFP E52645dn
-HP LaserJet Managed Flow MFP E52645c
-HP Color LaserJet Managed E75245dn
-HP Color LaserJet Enterprise M751n 
-HP Color LaserJet Enterprise M751dn
-HP PageWide XL 3900PS MFP
-HP OfficeJet Pro 8030 All-in-One Printer series
-HP OfficeJet Pro 8020 All-in-One Printer series
-HP OfficeJet 8020 All-in-One Printer Series
-HP OfficeJet 8010 All-in-One Printer series

 **Added support for following new Distro's:**
-Debian 9.8(64-bit)
-Ubuntu 19.04(64-bit)
-Fedora 30(64-bit)


```

---

### Post by jonathanbossenger on 2019-05-27
> **CatKiller said:**
> Why not just use the version in the repositories?

I tried that and it wasnt working, hence trying to install the latest version.

---

### Post by jonathanbossenger on 2019-05-27
> **Frogs Hair said:**
> Hello:

I am running Budgie 19.04 and I downloaded the run file per this [instruction]("http://ubuntuhandbook.org/index.php/2019/05/hplip-3-19-5-released-with-ubuntu-19-04-64-bit-support/"). The file was then made executable and run it in the terminal. I followed the instructions in the terminal. You may want to remove/purge the current version of HPLIP first or you will be prompted to do so during the installation. This takes some time to complete.

This is exactly what I did, only via the command line. I get stuck at installing the plugin every time.

---

