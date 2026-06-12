---
title: "CrushFTP - Start Script can NOT find JAVA"
date: 2020-04-24
forum: General Help
---

### Post by locbtran on 2020-04-24
I'm using Ubuntu 19.10.  I've installed CrushFTP but I'm getting an error when I try to run it 
```
root@osboxes:/home/CrushFTP9# ./crushftp_init.sh start
No Java runtime found. Please install Java then try again. Exiting ...

```

I already have JAVA installed
```
root@osboxes:/home/CrushFTP9# java -version
openjdk version "1.8.0_252"
OpenJDK Runtime Environment (build 1.8.0_252-8u252-b09-1~19.10-b09)
OpenJDK 64-Bit Server VM (build 25.252-b09, mixed mode)


root@osboxes:/home/CrushFTP9# whereis java
java: /usr/bin/java /usr/share/java /home/jre1.8.0_241/bin/java /usr/share/man/man1/java.1.gz

```


From the documentation, it says "to specify the full path to the java binary"
[https://www.crushftp.com/crush9wiki/Wiki.jsp?page=Linux%20Install](https://www.crushftp.com/crush9wiki/Wiki.jsp?page=Linux%20Install)


I checked the crushftp_init.sh and I have no idea where to make my modification so that the file, crushftp_init.sh can see the java.
I`ve uploaded the attachment, if anyone cares.

Has anyone ever encounter this problem before?




thanks

---

### Post by ActionParsnip on 2020-04-24
Does it require Oracle Java instead? Is there no scope to use SFTP? FTP is absolutely awful and not secure. If you have openssh-server installed and running then you have an SFTP server as well. Nautilus and other decent file managers can connect to this easily. Windows needs 3rd party assistance but can work.

---

### Post by ActionParsnip on 2020-04-24
Seems the Java check in the script is just for the SYSINFO variable if you look in the script.

(Make a backup of the script before making changes)

You could just comment out the check below ( Lines 215 - 218 )

```

	if [ ! "${JAVAVER:0:1}" ] ; then
	  echo "No Java runtime found. Please install Java then try again. Exiting ..."
	  exit 1
	fi

```

becomes

```

#	if [ ! "${JAVAVER:0:1}" ] ; then
#	  echo "No Java runtime found. Please install Java then try again. Exiting ..."
#	  exit 1
#	fi

```

then change line 213:

```

JAVAVER=$($JAVA -version 2>&1 | head -n 1 | awk -F '"' '{print $2}')

```

to:
```

JAVAVER="1.8.0_252"


```

---

