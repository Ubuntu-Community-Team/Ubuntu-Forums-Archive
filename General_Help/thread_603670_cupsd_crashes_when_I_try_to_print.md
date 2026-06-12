---
title: "cupsd crashes when I try to print"
date: 2007-11-05
forum: General Help
---

### Post by WebDrake on 2007-11-05
I'm using Kubuntu Gutsy on a Lenovo ThinkPad R61 and am having serious problems with the print system.  If I try to print I get an error message along the following lines:

```

A print error occurred. Error message received from system:

cupsdoprint -P 'tmpprinter_Ww8Smnlp' -J 'KDE Print Test' -H '/var/run/cups/cups.sock:631' -U 'myusername' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
server-error-service-unavailable

```

(This is from an attempt at printing a test page but the same happens if I add the printer without testing it and then attempt to print at a later time.)

From checking before and after it seems that cupsd crashes but I don't know why.  The printer in question is a network printer added with IPP, a HP LaserJet 2430, but I have had similar experiences trying to add other printers.

Can anyone advise what is wrong and how to go about fixing it?

Many thanks,
 
     -- Joe

---

