---
title: "Cannot get Java to install via webupd8 PPA"
date: 2015-10-12
forum: General Help
---

### Post by uberamd2 on 2015-10-12
When installing Java 8 (jdk-8u60-linux-x64) via webupd8 PPA I'm getting a sha256sum mismatch error. This is AFTER doing an apt-get update. The file is downloading successful from Oracles servers.

Here is the output:

```
[TABLE]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]168960K ........ ........ ........ ........ ........ ........ 97%  104K 43s[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]172032K ........ ........ ........ ........ ........ ........ 98% 99.2K 16s[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]175104K ........ ........ ........ .....                     100% 96.8K=25m50s[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"][/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]2015-10-12 12:47:40 (114 KB/s) - ?jdk-8u60-linux-x64.tar.gz? saved [181238643/181238643][/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"][/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]Download done.[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]Removing outdated cached downloads...[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]sha256sum mismatch jdk-8u60-linux-x64.tar.gz[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]Oracle JDK 8 is NOT installed.[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]dpkg: error processing package oracle-java8-installer (--configure):[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"] subprocess installed post-installation script returned error exit status 1[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]Errors were encountered while processing:[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"] oracle-java8-installer[/TD]
[/TR]
[TR]
[TD="class: time"]12-Oct-2015 07:47:43[/TD]
[TD="class: buildOutputLog"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/TD]
[/TR]
[/TABLE]

```

Anyone have ideas? I've tried multiple methods of obtaining the .tar.gz file but keep getting the same result. This has been happening since Friday and continues through today on multiple systems.

Any assistance is greatly appreciated!


[HR][/HR]
EDIT: Looks like it's fixed somewhere along the chain. After doing an apt-get purge oracle-java8-installer, apt-get clean, and apt-get update I was able to successfully perform an apt-get install oracle-java8-installer on all the systems that were experiencing issues starting Friday.

---

### Post by QIII on 2015-10-12
Hello!

Please mark your thread solved.  :)

---

