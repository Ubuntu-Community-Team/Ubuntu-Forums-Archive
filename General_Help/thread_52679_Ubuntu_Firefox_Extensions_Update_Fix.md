---
title: "Ubuntu Firefox Extensions Update Fix"
date: 2005-07-28
forum: General Help
---

### Post by Psycho275 on 2005-07-28
Hello all,

After coming across the problem with Firefox not updating extensions in Ubuntu, I did a little research and found out how to fix the problem.

I've written a simple shell script to fix the problem.

Here are the commands to download and execute it:
```
$ wget http://psycho275.info/uploads/firefox_fix.sh
$ chmod +x firefox_fix.sh
$ sh firefox_fix.sh
```

The script will download the Firefox package and replace the file which is causing the problems with the Ubuntu versions. It won't overwrite any of your settings, extensions, etc, so there's no need to worry about that.

I hope it helps,
Dave

---

### Post by SynapseR on 2005-07-28
Hi,
Could you provide a little more information about this
fix ?
What exactly does it do ?

Regards,
SynapseR

---

### Post by majikstreet on 2005-07-28
[QUOTE=SynapseR]Hi,
Could you provide a little more information about this
fix ?
What exactly does it do ?

Regards,
SynapseR[/QUOTE]
 Looking at the source code, this basicly downloads a new firefox then copies toolkit.jar over from the new version to your current installation.

---

### Post by Psycho275 on 2005-07-28
[QUOTE=SynapseR]Could you provide a little more information about this
fix ?[/QUOTE]

Basically, the later versions (1.0.4 onwards) of Firefox for Ubuntu (from the repositories) have had a problem with them, which prevents the updating of extensions.

As majikstreet said, the script replaces toolkit.jar which, in the Ubuntu version, contained a file that is not correct. Replacing the file with the version included with Firefox from the official website fixes the problem.

---

