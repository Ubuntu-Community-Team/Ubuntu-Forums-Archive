---
title: "T495 - Ubuntu 19.10 - Backlight issue"
date: 2020-04-04
forum: General Help
---

### Post by yeleek on 2020-04-04
Hi,
Fresh install on a new Lenovo T495.  Noticed in  journalctl that I am getting the below error.  Any ideas how to resolve please?

```

ben@TP:~$ systemctl status systemd-backlight@backlight:acpi_video0.service
&#9679; systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0
   Loaded: loaded (/lib/systemd/system/systemd-backlight@.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2020-04-04 11:45:52 BST; 6min ago
     Docs: man:systemd-backlight@.service(8)
  Process: 993 ExecStart=/lib/systemd/systemd-backlight load backlight:acpi_video0 (code=exited, status=1/FAILURE)
 Main PID: 993 (code=exited, status=1/FAILURE)

Apr 04 11:45:52 TP systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:acpi_video0...
Apr 04 11:45:52 TP systemd-backlight[993]: Failed to get backlight or LED device 'backlight:acpi_video0': No such device
Apr 04 11:45:52 TP systemd[1]: systemd-backlight@backlight:acpi_video0.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 11:45:52 TP systemd[1]: systemd-backlight@backlight:acpi_video0.service: Failed with result 'exit-code'.
Apr 04 11:45:52 TP systemd[1]: Failed to start Load/Save Screen Backlight Brightness of backlight:acpi_video0.

```

Thanks

---

