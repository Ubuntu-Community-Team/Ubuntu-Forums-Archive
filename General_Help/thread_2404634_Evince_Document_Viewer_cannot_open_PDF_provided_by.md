---
title: "Evince Document Viewer cannot open PDF provided by Thunderbird"
date: 2018-10-26
forum: General Help
---

### Post by jj.wauters on 2018-10-26
I cannot open an attached pdf file provided by Thunderbird. 
When opening I get an error message like : "Error opening file /tmp/mozilla_username0/filename.PDF: No such file or directory".
There is no problem when opening attached files stored in the same directory by other apps with extensions like docx, jpg, etc.
It seems that Evince Document Viewer can only read files in the HOME directory and not if they are stored elswhere. 
Are there settings where I can force Evince Document Viewer to look elsewhere?

Environment : Ubuntu 16.04 /  Evince Document Viewer 3.30.0  / Thunderbird 60.2.1

---

### Post by Holger_Gehrke on 2018-10-26
That's a newer version of evince than I have on 18.04. Did you perhaps install it from a snap ? Programs installed through snap are restricted from accessing most of the system through apparmor profiles.

To find out if your evince comes from a snap enter 'snap list' in a terminal.

Holger

---

### Post by jj.wauters on 2018-10-26
I don't remember how I installed Evince. But as after years of having no troubles with Thunderbird/Document Viewer I googled for a 
solution and I ended up with Evince.
The snap output :
Name               Version    Rev   Tracking  Publisher    Notes
core               16-2.35.4  5662  stable    canonical&#10003;   core
evince             3.30.0     46    stable    ken-vandine  -
gnome-3-26-1604    3.26.0     74    stable    canonical&#10003;   -
gtk-common-themes  0.1        701   stable    canonical&#10003;   -
inkscape           0.92.3     4274  stable    inkscape&#10003;    -

---

