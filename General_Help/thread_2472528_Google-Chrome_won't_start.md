---
title: "Google-Chrome won't start"
date: 2022-03-02
forum: General Help
---

### Post by Meneer Jansen on 2022-03-02
I did not install any updates or new software and today I cannot use Google-Chrome anymore. It starts up and closes after a second or so. Error message on command line:
```
$ google-chrome
libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed
[11621:11621:0302/115441.253060:ERROR:sandbox_linux.cc(377)] InitializeSandbox() called with multiple threads in process gpu-process.
Trace/breakpoint trap (core dumped)

```
Distro: Ubuntu 20.04 Focal Fossa.

Anybody else have this problem all of a sudden?

---

### Post by foxsquirrel on 2022-03-02
I have not personally experienced that issue.

It did look suspicious mentioning the "sandbox"

Did an internet search using this query : 
**sandbox_linux.cc**


It  appears in a few posts dating back to 2019, also looks like not much you can do on your end.

---

### Post by ActionParsnip on 2022-03-02
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy google-chrome

```

Thanks

---

### Post by Meneer Jansen on 2022-03-02
> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a; apt-cache policy google-chrome

```

Thanks
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
Linux Big-PC 5.8.0-63-generic #71~20.04.1-Ubuntu SMP Thu Jul 15 17:46:08 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
N: Unable to locate package google-chrome

```

---

### Post by deadflowr on 2022-03-02
Your linux kernel is out of date and unsupported.
Is there a reason for this?

Google Chrome's package is google-chrome-stable so look at
```
apt policy google-chrome-stable
```

---

### Post by Meneer Jansen on 2022-03-02
> **deadflowr said:**
> Your linux kernel is out of date and unsupported.
Is there a reason for this?

Google Chrome's package is google-chrome-stable so look at
```
apt policy google-chrome-stable
```
Output of the command:
```

$ apt policy google-chrome-stable
google-chrome-stable:
  Installed: 99.0.4844.51-1
  Candidate: 99.0.4844.51-1
  Version table:
 *** 99.0.4844.51-1 100
        100 /var/lib/dpkg/status
     98.0.4758.102-1 500
        500 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages


```

---

### Post by Meneer Jansen on 2022-03-03
1. Solution for the *libva* error:
The command *vainfo* echoed an error on a VA driver (iHD_drv_video.so) I don't need ([link]("https://forum.manjaro.org/t/va-api-driver-broken/30529")):
```
$ vainfo
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed
libva info: va_openDriver() returns 1
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_6
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Ivybridge Desktop - 2.4.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Simple            :    VAEntrypointEncSlice
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD

```
One needs to remove the package:
```
intel-media-driver
```
this also uninstalls the meta-package (i.e. does nothing) *va-driver-all*. The proper VA driver for my Intel video chip (GPU) is:
```
i965-va-driver
``` 
that is: the one does not give an error in *vainfo*. This still did not solve my problems w/ Chrome (had to backup Bookmarks delete profile). I uninstalled it by temporarily disabling the repo's for 'Proprietary Drivers' and 'Software restricted by copyright' in Synaptic. Else: forced installation of intel-media-driver-non-free.


2. The only way I could get rid of the errors and successfully use Google-chrome was to backup the *Bookmarks* file in- and then delete the folder */home/my_name/.config/google-chrome/*, restart Chrome make a new profile and copy my Bookmarks into the proper profile folder. Had to re-install my favourite Extensions. Done.

The VA error probably did **not** crash Chrome.

---

