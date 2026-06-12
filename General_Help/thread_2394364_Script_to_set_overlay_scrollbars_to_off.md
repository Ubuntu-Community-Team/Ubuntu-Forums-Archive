---
title: "Script to set overlay scrollbars to off"
date: 2018-06-15
forum: General Help
---

### Post by red_hax0r on 2018-06-15
The following script will set overlay scrollbars to off in both gtk+2 and gtk+3 system-wide:

```
#!/bin/bash

echo "This will add the necessary lines to eliminate" 
echo "overlay scrollbars for both Gtk+2 and Gtk+3"
echo
echo "-------------------------------------------"
echo "Please do not execute if these have already been added"
echo "as this is unnecessary."
echo "-------------------------------------------"
echo "Need root permission."
sudo -u root bash << EOF

echo >> /etc/profile
echo "GTK_OVERLAY_SCROLLING=0" >> /etc/profile
echo "LIBOVERLAY_SCROLLBAR=0" >> /etc/profile

echo
echo "Overlay scrollbars now set"
EOF
```

**Please use with caution and do not modify.  **

---

