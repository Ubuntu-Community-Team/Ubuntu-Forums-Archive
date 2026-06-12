---
title: "help installing Brother 2170N (network printer)"
date: 2006-11-11
forum: General Help
---

### Post by syxbit on 2006-11-11
the printer is connected to my router.
i click add the new printer.
i choose "network printer"
i choose "CUPS printer IPP"
I put in the hostname
there's no driver built in to Ubuntu, but on the brother website there's a .deb, so i install that first.
it installs some files here
/usr/local/Brother
but none are accepted as drivers
i followed this guide
[http://ubuntuforums.org/showthread.php?t=123539&page=3](http://ubuntuforums.org/showthread.php?t=123539&page=3)
but when i install the "cups" driver i get this error
```
(Reading database ... 103930 files and directories currently installed.)
Preparing to replace cupswrapperhl2070n 1.0.0-1 (using cupswrapperhl2070n_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
Unpacking replacement cupswrapperhl2070n ...
Setting up cupswrapperhl2070n (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperHL2070N
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!
```

but the last step of doing the localhost and adding is vague, and i don't know what kind of printer to add, and even then, i need to install the drivers, which i don't have

---

