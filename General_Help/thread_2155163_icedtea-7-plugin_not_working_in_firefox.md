---
title: "icedtea-7-plugin not working in firefox"
date: 2013-06-17
forum: General Help
---

### Post by donsy on 2013-06-17
When trying to display a website with applets I get the following error:
```
icedteanp plugin error: Failed to run /usr/lib/jvm/java-7-openjdk-amd64/bin/java.  For more detail rerun "firefox -g" in a terminal window.
```

In Firefox Tools->Add-ons->Plugins, IcedTea shows up as:
```
IcedTea-Web Plugin (using IcedTea-Web 1.2.3 (1.2.3-0ubuntu0.12.04.2))
```

Other info:
~$ java -version
```
java version "1.7.0_21"
OpenJDK Runtime Environment (IcedTea 2.3.9) (7u21-2.3.9-0ubuntu0.12.04.1)
OpenJDK 64-Bit Server VM (build 23.7-b01, mixed mode)
```

~$ update-java-alternatives -l
```
java-1.7.0-openjdk-amd64 1051 /usr/lib/jvm/java-1.7.0-openjdk-amd64
```

~$ dpkg -l icedtea-7-plugin
```
ii  icedtea-7-plugin   1.2.3-0ubuntu0.12.04.2  web browser plugin based on OpenJDK and IcedTea to execute Java applets

```

---

### Post by donsy on 2013-06-18
Bump?

---

### Post by donsy on 2013-06-19
Another bump.

---

### Post by Jim_Bryan on 2013-09-21
Fix is listed here:  [http://www.maketecheasier.com/install-java-runtime-in-ubuntu/2012/05/14](http://www.maketecheasier.com/install-java-runtime-in-ubuntu/2012/05/14)
Basically:
[COLOR=#000000][FONT=Bitstream Charter]sudo apt-get install openjdk-7-jre[/FONT][/COLOR][TABLE="width: 276"]
		[TR]
		[TD="width: 276, bgcolor: #eeeeee"]			[COLOR=#000000][FONT=Bitstream Charter, serif]sudo apt-get install icedtea-7-plugin[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[TABLE="width: 538"]
		[TR]
		[TD="width: 538, bgcolor: #eeeeee"]			[COLOR=#000000][FONT=Bitstream Charter, serif]mkdir ~/.mozilla/plugins[/FONT][/COLOR]
[COLOR=#000000][FONT=Bitstream Charter, serif]ln -s /usr/lib/jvm/jdk1.7.0_04/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugin[/FONT][/COLOR]		[/TD]
	[/TR]
[/TABLE]
[COLOR=#000000][FONT=Bitstream Charter, serif]Done.IcedTea in Firefox now works. [/FONT][/COLOR]

---

### Post by adv0cat3 on 2014-08-19
> **Jim_Bryan said:**
> Fix is listed here:  [http://www.maketecheasier.com/install-java-runtime-in-ubuntu/2012/05/14](http://www.maketecheasier.com/install-java-runtime-in-ubuntu/2012/05/14)
Basically:
[COLOR=#000000][FONT=Bitstream Charter]sudo apt-get install openjdk-7-jre[/FONT][/COLOR][TABLE="width: 276"]
[TR]
[TD="width: 276, bgcolor: #eeeeee"]            [COLOR=#000000][FONT=Bitstream Charter]sudo apt-get install icedtea-7-plugin[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[TABLE="width: 538"]
[TR]
[TD="width: 538, bgcolor: #eeeeee"]            [COLOR=#000000][FONT=Bitstream Charter]mkdir ~/.mozilla/plugins[/FONT][/COLOR]
[COLOR=#000000][FONT=Bitstream Charter]ln -s /usr/lib/jvm/jdk1.7.0_04/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugin[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Bitstream Charter]Done.IcedTea in Firefox now works. [/FONT][/COLOR]

This is NOT the solution. If you read the article you yourself linked you can see that the sim link is required only for Oracle java installations but OP has clearly stated he has OpenJDK.

My personal issue is that I have Open JDK 7 and IcedTea7 both installed on FireFox 24.7 and Java applets are not loading.

---

### Post by QIII on 2014-08-19
And this very old thread, discussing versions of FF and OpenJDK that are very old, is in need of a nap.

Rather than raising the dead, it would be best to begin a new thread.

---

