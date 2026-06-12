---
title: "help with .NET snap. Can't run as normal user"
date: 2021-08-11
forum: General Help
---

### Post by yaminb on 2021-08-11
Hi,

I'm having some trouble getting the .NET snap to work. It installs, but following the instructions, it seems like I need to run as root/sudo to execute any .NET application.

Reference:
[https://docs.microsoft.com/en-us/dotnet/core/install/linux-snap](https://docs.microsoft.com/en-us/dotnet/core/install/linux-snap)

```

sudo snap install dotnet-runtime-50 --classic
sudo snap alias dotnet-runtime-50.dotnet dotnet 
export DOTNET_ROOT=/snap/dotnet-sdk/current

```

Here's the problem. I can only execute .net as root.

```

$ dotnet --info
cannot snap-exec: cannot exec "/snap/dotnet-sdk/137/snap/command-chain/snapcraft-runner": permission denied
$ sudo dotnet --info
.NET SDK (reflecting any global.json):
 Version:   5.0.400
 Commit:    d61950f9bf

Runtime Environment:
 OS Name:     ubuntu
 OS Version:  21.04
 OS Platform: Linux
 RID:         ubuntu.21.04-x64
 Base Path:   /snap/dotnet-sdk/137/sdk/5.0.400/

Host (useful for support):
  Version: 5.0.9
  Commit:  208e377a53

.NET SDKs installed:
  5.0.400 [/snap/dotnet-sdk/137/sdk]

.NET runtimes installed:
  Microsoft.AspNetCore.App 5.0.9 [/snap/dotnet-sdk/137/shared/Microsoft.AspNetCore.App]
  Microsoft.NETCore.App 5.0.9 [/snap/dotnet-sdk/137/shared/Microsoft.NETCore.App]

To install additional .NET runtimes or SDKs:
  https://aka.ms/dotnet-download



```


any ideas on how I can get dotnet to work as a regular user?

Thanks,

---

### Post by yaminb on 2021-08-11
Nevermind, think I got it.

Don't use aliases and link instead

```

sudo snap unalias dotnet
sudo ln -s /snap/dotnet-sdk/current/dotnet /usr/local/bin/dotnet



```

---

### Post by thiagocantero on 2021-11-07
Theres another simple way.

Code:

> sudo chown <user name> /snap/dotnet-sdk/current

---

### Post by QIII on 2021-11-07
It might be unwise to change ownership of that directory.  Changing directory ownership is not to be taken lightly.

The OP's solution was part of the instructions cited.  That should be enough.

Given that the thread was marked *Solved* by the user -- who will not likely be back to check -- further discussion is pointless in any case.

---

