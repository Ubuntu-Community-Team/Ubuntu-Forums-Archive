---
title: "FIND command help"
date: 2007-02-23
forum: General Help
---

### Post by telovoyagarcar on 2007-02-23
Im having problems with the syntax even after reading stuff in many places.

My IPCOP box is screwed up, and i need to find the file where  i did set the spoofed MAC address so the cable modem will let ipcop access the internet.

The expression would be something like this:

**find any file in the disk containing the string ¨(mac address number)¨ inside the file**

I have no clue what file i had to modify so when the machine starts gets the MAC changed... If i find it, i will be able to format the box and start from scratch with a fresh installation.

Thanks guys

---

### Post by ofek on 2007-02-23
I prefer locate or slocate on find when possible.
write "sudo locate -u" in terminal and when it finishes write "locate [mac_address]"
without the brackets of course and it should probably work. 

EDIT: Oops. im probably very tired u wanted to search within the file and not within the filename. 

EDIT2: If u still want to use find rather than locate like chalex suggested, u could try this:  find [dir_to_start_search_from] -exec grep "[mac_addres]" '{}' \; -print 
although this command might take a while to be run. ( no brackets again =-] )

---

### Post by chalex on 2007-02-23
The locate command is an easy way to search for filenames in your system.  The find command has many more advanced options, but it also looks only at filenames.  You seem to be looking for a particular string inside a file.  You probably want to use the command grep.

Try 
```
grep "(mac address number)" /etc/*
```

Also, most cable modems will only talk to the first MAC address they see after they power on.  Are you sure you need to spoof the MAC address and not just power cycle the modem?

---

### Post by telovoyagarcar on 2007-02-23
Yes... im REALLY sure... the last time i had to call them and give some BS like i got a new computer and wanted to register the new MAC with them so their crappy cable modem would get me online... then i set up IPCOP and need to spoof the MAC because the mac i registered was from an onboard NIC.

Thanks for the help... ill try with grep now.

---

