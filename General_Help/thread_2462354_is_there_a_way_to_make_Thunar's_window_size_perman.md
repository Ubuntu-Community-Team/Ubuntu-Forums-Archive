---
title: "is there a way to make Thunar's window size permanent?"
date: 2021-05-19
forum: General Help
---

### Post by ardouronerous on 2021-05-19
I'm running Xubuntu 20.04. I customized Thunar's window size like this:

I went to [FONT=courier new]/home/~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml[/FONT] and edited these values from  [FONT=courier new]640x480[/FONT]  to [FONT=courier new]798x547[/FONT] and restarted my system. 

  ```
<property name="last-window-width" type="int" value="798"/>
<property name="last-window-height" type="int" value="547"/>
```  

However, sometimes I would resize Thunar by accident  with my mouse. So, is there a way to make the window size permanent?

  The behavior that I'm looking for is like when I resize Thunar's  window size by accident, my customized window size would be brought back  after I close Thunar's window.

---

### Post by Holger_Gehrke on 2021-05-19
How about writing a a simple script that sets the properties and starts Thunar ?
```

#!/bin/bash
/usr/bin/xfce-conf --channel thunar --property /last-window-height --set 547
/usr/bin/xfce-conf --channel thunar --property /last-window-width --set 798
/usr/bin/thunar $*

```
Save that in a file in ~/.local/bin/ and make it executable. Copy the desktop file for thunar from /usr/share/applications/Thunar.desktop to ~/.local/share/applications/. Edit the local desktop file and change the 'Exec=' line to call the script instead of calling thunar directly.

Holger

---

### Post by ardouronerous on 2021-05-19
> **Holger_Gehrke said:**
> How about writing a a simple script that sets the properties and starts Thunar ?
```

#!/bin/bash
/usr/bin/xfce-conf --channel thunar --property /last-window-height --set 547
/usr/bin/xfce-conf --channel thunar --property /last-window-width --set 798
/usr/bin/thunar $*

```
Save that in a file in ~/.local/bin/ and make it executable. Copy the desktop file for thunar from /usr/share/applications/Thunar.desktop to ~/.local/share/applications/. Edit the local desktop file and change the 'Exec=' line to call the script instead of calling thunar directly.

Holger

Didn't work though.

---

### Post by ardouronerous on 2021-05-19
As a test, I edited the executable to see if it will change Thunar's window size:

```
#!/bin/bash
/usr/bin/xfce-conf --channel thunar --property /last-window-height --set  640
/usr/bin/xfce-conf --channel thunar --property /last-window-width --set 480
/usr/bin/thunar $*
```

It didn't work.

---

### Post by Holger_Gehrke on 2021-05-19
:oops:

please replace 'xfce-conf' with 'xfconf-query' ... for some reason I always misremember that particular command, even if I just had that error and corrected it.

Holger

---

### Post by ardouronerous on 2021-05-19
> **Holger_Gehrke said:**
> :oops:

please replace 'xfce-conf' with 'xfconf-query' ... for some reason I always misremember that particular command, even if I just had that error and corrected it.

Holger

```
#!/bin/bash
/usr/bin/xfconf-query --channel thunar --property /last-window-height --set 547
/usr/bin/xfconf-query --channel thunar --property /last-window-width --set 798
/usr/bin/thunar $*
```

Thank you that worked.

---

