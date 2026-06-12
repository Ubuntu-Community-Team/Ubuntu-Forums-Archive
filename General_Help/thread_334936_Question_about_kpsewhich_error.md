---
title: "Question about kpsewhich error"
date: 2007-01-09
forum: General Help
---

### Post by nshiau on 2007-01-09
I have a problem during installing tetex-bin. Basically the problem is kpsewhich command cannot recognize option '-var-value'. I did install the latest libkpathsea4 package. Does anyone know what is the possible cause?

> kpsewhich: unrecognized option `-var-value'


The followings are the output during the installation if tetex-bin:

> 
Unpacking tetex-bin (from tetex-bin_3.0-13ubuntu6_i386.deb) ...
Setting up tetex-bin (3.0-13ubuntu6) ...

Creating config file /etc/texmf/fmt.d/01tetex.cnf with new version
/usr/local/bin/mktexlsr: line 97: access: command not found
mktexlsr: /var/lib/texmf/ls-R: no write permission. Skipping...
/usr/local/bin/mktexlsr: line 97: access: command not found
mktexlsr: /var/lib/texmf/ls-R-TEXMFMAIN: no write permission. Skipping...
/usr/local/bin/mktexlsr: line 97: access: command not found
mktexlsr: /var/cache/fonts/ls-R: no write permission. Skipping...
mktexlsr: /var/lib/texmf/ls-R-TEXMFDIST-TETEX lacks magic string. Skipping...
Running fmtutil-sys. This may take some time. ...
kpsewhich: unrecognized option `-var-value'
kpsewhich: unrecognized option `-var-value'
kpsewhich: unrecognized option `--var-value=TEXMFMAIN'
/usr/bin/fmtutil: line 378: /texconfig/tcfmgr: No such file or directory
fmtutil: config file `fmtutil.cnf' not found.

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXxvb25k
Please include this file if you report a bug.
dpkg: error processing tetex-bin (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tetex-bin

---

