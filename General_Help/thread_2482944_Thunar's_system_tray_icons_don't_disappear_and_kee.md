---
title: "Thunar's system tray icons don't disappear and keep stacking"
date: 2023-01-14
forum: General Help
---

### Post by bladabuska on 2023-01-14
Hi, guys.

I notice some estrange behavior when using Thunar on Ubuntu 22.04.

I'm new on Linux, so maybe the user (read: me) just messed out the system configuration... Hehehe. I don't know the names of the GUI elements, so please excuse me if I got something wrong. (Bad English grammar included).

Steps to reproduce the issue:

Open Thunar.
Copy (ctrl+c) or cut (ctrl+x) one, or multiple, files and folders.
Paste (ctrl+v) in the same or in other location.
Important: the operation has to lengthy enough to trigger a "File operation progress".
Select some option.

What was expected to happen:

1. File transfer begins.
2. A "File operation progress" window is shown.
3. A Thunar icon of the "File operation progress" window is shown at the system tray (between clock and battery).
4. When a duplicate file or folder name is found, the operation is paused and a window dialog opens and prompts the user action.
5. When the user selects an option (all the options cause the issue), the operation is resumed according to the user option.
6. Files are correctly overwritten, renamed or skipped.
7. When the operation finishes, the "File operation progress" window closes.
8. The "File operation progress" on the tray bar disappears.

What actually happens:

OK 1. File transfer begins.
OK 2. A "File operation progress" window is shown.
OK 3. A Thunar icon of the "File operation progress" window is shown at the system tray (between clock and battery).
OK 4. When a duplicate file or folder name is found, the operation is paused and a window dialog opens and prompts the user action.
OK 5. When the user selects an option (all the options cause the issue), the operation is resumed according to the user option.
OK 6. Files are correctly overwritten, renamed or skipped.
OK 7. When the operation finishes, the "File operation progress" window closes.
==> 8. The icon stays on the bar.

If another file transfer is initialized, a second icon will appear, and so on.
Clicking on the icon will show a bugged window (empty with just the Title bar and the X button). Clicking on the X button will close the window, but the icon will remain on the tray bar.
The only way I found to make all icons disappear is to close Thunar. When opened again, none of the previous icons will show up.

I provided some pictures to illustrate the issue.

The system:
I have Ubuntu 22.04 installed, and I'm using it for 3 months. I always update the system using "apt update" and "apt upgrade", "snap refresh", and the Ubuntu Software Center.
I don't know if it's relevant, but I disabled the standard Ubuntu Dock, installed Cairo Dock, and changed from Wayland to X11, because Cairo Dock got some issues while using Wayland.

```
schwarz@peano:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
```

I don't know if I forgot some system information. If so, please ask (and tell me how to get it).

Any ideas?

Thanks in advance.

---

