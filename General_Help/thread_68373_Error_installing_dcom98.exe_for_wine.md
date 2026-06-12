---
title: "Error installing dcom98.exe for wine"
date: 2005-09-22
forum: General Help
---

### Post by linuxNewb on 2005-09-22
I'm trying to install dcom98.exe with wine using:

WINEDLLOVERRIDES="ole32=n" wine c:\\dcom98.exe

(dcom98.exe is on my fake c drive; I've also tried installing it from my home folder)

I keep getting the following errors:

err:setupapi:SetupDefaultQueueCallbackA copy error 5 "X:\\IXP000.TMP\\install.exe" -> "C:\\Windows\\System\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "X:\\IXP000.TMP\\dcom98.inf" -> "C:\\Windows\\System\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "X:\\IXP000.TMP\\eula98.txt" -> "C:\\Windows\\System\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "X:\\IXP000.TMP\\relnt98.txt" -> "C:\\Windows\\System\\dcom98\\relnotes.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "X:\\IXP000.TMP\\dcom98.inf" -> "C:\\Windows\\inf\\dcom98.inf"

I've googled these errors, but found nothing useful. I've found suggestions to use winetools or sidenet, but these want to create a new config, and I already have a bunch of programs working on my current config. Any suggestions? Thanks in advance.

---

### Post by skoal on 2005-09-22
Check [here](http://www.ubuntuforums.org/showthread.php?t=65190&highlight=dcom98), this might get ya runnin'...

\\//_

---

