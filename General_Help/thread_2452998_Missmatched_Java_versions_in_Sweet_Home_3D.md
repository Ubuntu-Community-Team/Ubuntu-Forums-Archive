---
title: "Missmatched Java versions in Sweet Home 3D"
date: 2020-11-01
forum: General Help
---

### Post by jicha on 2020-11-01
Hello,

I'm not able to run Sweet Home 3D. It requests a Java version which I don't have installed and which doesn't exist in repository.

This is what I get when trying to run sweethome3d from konsole:
```
[FONT=monospace][COLOR=#000000][warning] /usr/bin/sweethome3d: Unable to locate freehep-util in /usr/share/java [/COLOR]
[warning] /usr/bin/sweethome3d: Unable to locate freehep-xml in /usr/share/java 
/usr/bin/sweethome3d: 304: exec: /usr/lib/jvm/java-14-oracle/bin/java: not found[/FONT]
```

But my installed java version is OpenJDK 11. Running **[FONT=monospace][COLOR=#000000]readlink -f $(which java)[/COLOR][/FONT]**[FONT=monospace][COLOR=#000000] shows it correctly:
```
/[FONT=monospace][COLOR=#000000]usr/lib/jvm/java-11-openjdk-amd64/bin/java[/COLOR][/FONT]
```

What could be the problem and hot to fix it? Thank you.
[/COLOR][/FONT]

---

### Post by HermanAB on 2020-11-01
My brute force solution to these issues is usually to make a virtual machine with the correct version of whatever Linux distribution is required to run an obstreperous program.  This is a bit like using a hammer to swat a fly, but it is a very easy solution, since installing a virtual machine takes only a few minutes.

---

