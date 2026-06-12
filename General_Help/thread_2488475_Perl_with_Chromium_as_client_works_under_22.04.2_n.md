---
title: "Perl with Chromium as client works under 22.04.2 not like 20.04.3"
date: 2023-07-05
forum: General Help
---

### Post by Roland_Msl on 2023-07-05
My main software is written in perl as a server and uses Chromium as a client.

All worked fine in Ubuntu 16.04 and 20.04.3 but there is a problem in 22.04.2

When I enter in console
perl server.pl site=pege.org
perl starts normal and is writing messages to the console.
But at trying to open a new tab on Chromium, the following message appears on the console and nothing shows in Chromium



[7044:7044:0705/185945.214642:ERROR:chrome_browser_cloud_management_controller.cc(162)] Cloud management controller initialization aborted as CBCM is not enabled.
/usr/share/libdrm/amdgpu.ids: No such file or directory
amdgpu: os_same_file_description couldn't determine if two DRM fds reference the same file description.
If they do, bad things may happen!
[7044:7044:0705/185946.612899:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
[7044:7142:0705/185948.502553:ERROR:udev_watcher.cc(98)] Failed to begin udev enumeration.

In the attached error.txt are all the messages on console from 22.04.2 and from 20.04.3

---

