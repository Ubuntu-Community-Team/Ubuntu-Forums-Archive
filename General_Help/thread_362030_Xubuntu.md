---
title: "Xubuntu"
date: 2007-02-15
forum: General Help
---

### Post by Hookj5 on 2007-02-15
I am running Ubuntu in VMware as a virtual machine and I really like it.  I read up on Kubuntu and Xubuntu and wanted to try them.  I got Xubuntu 6.061 and installed it. It runs firefox fine.  I downloaded F@H SMP version, which runs like mad in Ubuntu, but when I try to run it in the terminal, I get the same error over and over.  I unpacked the program to a folder and when I try to run it says the file doesn't exist, when I am looking right at it.  What I do in terminal is type [ cd ~/folding/fah <enter>] then [./fah5].  I get file doesn't exist.  I am new to Linux and am really getting frustrated with this error.  Please help!!

---

### Post by Hookj5 on 2007-02-15
Anyone? Please help.

---

### Post by Hookj5 on 2007-02-15
Bump:( :( :(

---

### Post by Artemis3 on 2007-02-15
You should run the version for your OS, you can't expect it to run faster inside an emulated pc.

Most likely there is a permissions problem. Type ls -l in the f@h directory, and pay attention to the owner/group and the flags of the file you intend to run. It should have Read and eXecute ( r-x ) permissions.

Use the command chmod to change them, like *chmod u+x fileblah.sh* will give the owner permission for execute the program. But if you are not the owner, then as root you could change the ownership of the file like: *sudo chmod yourlogin:yourgroup fileblah.sh*

According to the F@H page, it says:

[quote="http://folding.stanford.edu/linux.html"]To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe[/quote]

This should NOT run faster inside vmware than the version for your native os; you should pick a console version if you don't want graphics or such.

---

