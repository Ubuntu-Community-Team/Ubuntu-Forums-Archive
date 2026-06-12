---
title: "Google chrome freezes after a download"
date: 2023-02-21
forum: General Help
---

### Post by satimis on 2023-02-21
Hi all,

Ubuntu 22.04

Google Chrome browser freezes after download an image.  I have to logout and re-login to start it.

Please advise where I have to check?  Thanks

Regards

---

### Post by #&amp;thj^% on 2023-02-21
This is just tips to check, is this installed:
```
apt policy xdg-desktop-portal-gnome
```
and, In the terminal, run Chrome with the flag:
```
--enable-logging --v=1
```
Press Enter.

---

### Post by satimis on 2023-02-21
> **1fallen said:**
> This is just tips to check, is this installed:
```
apt policy xdg-desktop-portal-gnome
```
and, In the terminal, run Chrome with the flag:
```
--enable-logging --v=1
```
Press Enter.
Hi,

Thanks for your advice.

$ apt policy xdg-desktop-portal-gnome```

xdg-desktop-portal-gnome:
  Installed: (none)
  Candidate: 42.1-0ubuntu1
  Version table:
     42.1-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     42.0.1-1ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
Do I need to install this application ?

$ google-chrome --enable-logging --v=1```

libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
[70126:70126:0222/064907.254998:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 1 times!
[70126:70126:0222/064910.071770:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 2 times!
[70126:70126:0222/064911.769839:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 3 times!
[70036:70036:0222/065304.638171:ERROR:interface_endpoint_client.cc(695)] Message 0 rejected by interface blink.mojom.WidgetHost
[libprotobuf ERROR ../../third_party/protobuf/src/google/protobuf/message_lite.cc:133] Can't parse message of type "safe_browsing.ClientDownloadRequest" because it is missing required fields: (cannot determine missing fields for lite message)

hanging here

```

Regards

---

### Post by #&amp;thj^% on 2023-02-21
Yes please try:
```
sudo apt install xdg-desktop-portal-gnome 
```
You will need to restart your session to load the change.

---

### Post by satimis on 2023-02-21
> **1fallen said:**
> Yes please try:
```
sudo apt install xdg-desktop-portal-gnome 
```
You will need to restart your session to load the change.
On Terminal
$ sudo apt install xdg-desktop-portal-gnome
$ reboot

Now Google-Chrome won't freeze after a download.

Thanks

Regards

---

