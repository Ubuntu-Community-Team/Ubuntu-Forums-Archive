---
title: "Can't open chrome as a root"
date: 2015-05-25
forum: General Help
---

### Post by tuese on 2015-05-25
[COLOR=#111111][FONT=Ubuntu]Was trying to open chrome ([/FONT][/COLOR][COLOR=#303942][FONT=Droid Sans]Version 43.0.2357.65[/FONT][/COLOR][COLOR=#303942][FONT=Droid Sans])[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] with [/FONT][/COLOR]```
sudo google-chrome-stable --user-data-dir
``` [COLOR=#111111][FONT=Ubuntu]and got [/FONT][/COLOR]```
[0525/190656:ERROR:nss_util.cc(94)] Failed to create /home/username/.pki/nssdb directory.
```[COLOR=#111111][FONT=Ubuntu] and one process "chrome" but chrome won't open. With [/FONT][/COLOR]```
gksu google-chrome-stable
```[COLOR=#111111][FONT=Ubuntu] it tells me to open with [/FONT][/COLOR]```
--user-data-dir
```[COLOR=#111111][FONT=Ubuntu], trying with  and got [/FONT][/COLOR]```
gksu: unrecognized option '--user-data-dir'
```[COLOR=#111111][FONT=Ubuntu] I searched but could not solve the problem. Chrome as root [/FONT][/COLOR]necessary[COLOR=#111111][FONT=Ubuntu] because of the XAMPP. Help please! P.S.: sorry for english, it's not my native.[/FONT][/COLOR]

---

### Post by slickymaster on 2015-05-25
See this: [http://stackoverflow.com/questions/12258086/how-do-i-run-google-chrome-as-root](http://stackoverflow.com/questions/12258086/how-do-i-run-google-chrome-as-root)

---

### Post by tuese on 2015-05-26
> **slickymaster said:**
> [COLOR=#000000]See this: [/COLOR][http://stackoverflow.com/questions/1...chrome-as-root]("http://stackoverflow.com/questions/12258086/how-do-i-run-google-chrome-as-root")
Nothing works. It's ```
[COLOR=#000000][FONT=Ubuntu Mono][0525/190656:ERROR:nss_util.cc(94)] Failed to create /home/username/.pki/nssdb directory.[/FONT][/COLOR]
```
or nothing opens.

---

### Post by slickymaster on 2015-05-26
Other than stating that you should never run a web browser as root, certainly not permanently, all I can do is to point you to this thread; [http://ubuntuforums.org/showthread.php?t=1743565](http://ubuntuforums.org/showthread.php?t=1743565)

---

