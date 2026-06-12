---
title: "Updates don't work"
date: 2013-02-05
forum: General Help
---

### Post by Masz52 on 2013-02-05
I'm on Ubuntu 12.04.1 LTS, and when I try to update I get this error.

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing kde-window-manager-common (NewVersion2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
```

I'm not sure what to do.

---

### Post by plucky on 2013-02-06
> 'E:Problem parsing dependency Depends, E:Error occurred while processing kde-window-manager-common (NewVersion2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'


Open a terminal and run ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then run ```
sudo apt-get update
``` and see if you get any more errors.

The first command moves the **status** file to **status.broken** and the second command copies the backup status file to now become the new  **status** file.

Good Luck

---

### Post by Masz52 on 2013-02-07
Thank you, it updated successfully.

---

