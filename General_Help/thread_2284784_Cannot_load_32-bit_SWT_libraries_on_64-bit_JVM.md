---
title: "Cannot load 32-bit SWT libraries on 64-bit JVM"
date: 2015-07-01
forum: General Help
---

### Post by k0tt0n on 2015-07-01
I'm trying to install a program called VirgoFTP [http://freecode.com/projects/virgoftp/?branch_id=60100&release_id=205110](http://freecode.com/projects/virgoftp/?branch_id=60100&release_id=205110), when I try to run the scriprt I get this error

user@user-X550WA:~/Downloads/virgoftp$ ./virgoftp
start the VirgoFtp
Exception in thread "main" java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
	at edu.sysu.virgoftp.gui.VirgoFTP.main(Unknown Source)

Is there a way to get around this? Can I simply use a 32 bit version of Java?


<snip>

---

