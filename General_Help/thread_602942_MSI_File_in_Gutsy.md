---
title: "MSI File in Gutsy"
date: 2007-11-04
forum: General Help
---

### Post by dedlycow on 2007-11-04
I have been trying to install a program called, commsecpro msi. for the last few months. My question is can it be done?
I have received assistance from a few people that helped but it still does not work. I have installed Wine,wine tools, IE6 through wine and a few other attempts with the support of others.
If anyone thinks that its possible I would be very greatful for some help.
regards Dedly

---

### Post by kbracer on 2007-11-04
An msi file is an installer package format used by Windows. Your file "commsecpro.msi" is not a binary executable, but rather is a data file that is read an interpreted by the Windows installer "msiexec.exe" in order to install the contents of the file on the machine. On a Windows machine you would run this at the command prompt...

```
msiexec /i commsecpro.msi
```

... to install the commsecpro program. On a Windows box, the msi file type is associated with msiexec so that you can just click the msi file and go, much like media file types are associated with Windows Media Player and so on.

So, WINE is not going to execute your file because it is not an executable. You may be stuck installing it via msi onto a Windows box and then moving the executable files to your Ubuntu machine.

---

### Post by dedlycow on 2007-11-04
I am not very familiar with those terms or how to do that is there somewhere I might get simple etep by step instructions. 
Dedly

---

