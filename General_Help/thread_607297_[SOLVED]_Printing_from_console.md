---
title: "[SOLVED] Printing from console"
date: 2007-11-08
forum: General Help
---

### Post by vasiliymeshko on 2007-11-08
Sorry if the answer is something really obvious, I want to print (say, a text file) from command line. How can I do this?

---

### Post by llamakc on 2007-11-08
If you have a flat file (not a binary) you can use pipe | 

```

cat file.txt | lp

```

---

### Post by vasiliymeshko on 2007-11-08
When I try I get this responce:

```
lp: Error - no default destination available.
```

The printer is hooked up and ready, I even succesfully tried printing from Kate

---

### Post by ubuntology on 2007-11-08
Try setting your default printer. It's under System -> Preferences in gnome; no idea where it is in KDE.
What's the output of: lpstat -t

---

### Post by vasiliymeshko on 2007-11-08
The default printer is set to  PSC_1500_series

Output from lpstat -t gives:
```
scheduler is running
system default destination: PSC_1500_series
device for PSC_1500_series: hp:/usb/PSC_1500_series?serial=MY5B8D31BG0498
PSC_1500_series accepting requests since &#1089;&#1088;, 07-&#1083;&#1080;&#1089;-2007 16:14:17 -0500
printer PSC_1500_series is idle.  enabled since &#1089;&#1088;, 07-&#1083;&#1080;&#1089;-2007 16:14:17 -0500
```

---

### Post by vasiliymeshko on 2007-11-08
Ok finally figured it out. Had to do:

```
cat nameOfFile | lpr
```

That made it work. Appreciate the help.

---

