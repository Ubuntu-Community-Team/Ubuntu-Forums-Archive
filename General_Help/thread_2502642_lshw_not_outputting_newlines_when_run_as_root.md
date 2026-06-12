---
title: "lshw not outputting newlines when run as root"
date: 2024-11-22
forum: General Help
---

### Post by stevenwheel on 2024-11-22
I can run lshw as myself and other than complaining that it should be run as root, it works fine.
When I run sudo lshw, the only thing I see are the headers overwriting each other on the line just below the command I typed. 
It's as if its putting out carriage returns, but no newlines.

I have tried for a couple of hours now to figure it out and I am at a complete loss.
Any help is appreciated.

Thanks

---

### Post by Rubi1200 on 2024-11-23
If you are using a standard terminal without any customizations, try this:

Redirect the output to a file and then check formatting:

```
sudo lshw > lshw_output.txt
cat lshw_output.txt

```
Any improvement?

---

