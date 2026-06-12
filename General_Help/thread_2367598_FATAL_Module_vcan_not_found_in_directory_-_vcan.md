---
title: "FATAL: Module vcan not found in directory - vcan"
date: 2017-08-01
forum: General Help
---

### Post by cchaq on 2017-08-01
Hi all,

Apologies in advance if this is in the wrong sub section but need some help in fixing my missing module.

I'm trying to do the following:

    modprobe vcan

But it returns the following error:

    modprobe: FATAL: Module vcan not found in directory /lib/modules/4.4.0-1020-aws

I asked in the Github page for can-utils, as it's part of this application I'm trying to use and they said I'm missing:

    *"your 4.4.0-1020-aws Ubuntu Kernel has no CAN drivers configured at compile time - not even the virtual CAN driver.
    See: [https://packages.ubuntu.com/xenial-updates/amd64/linux-image-4.4.0-1020-aws/filelist](https://packages.ubuntu.com/xenial-updates/amd64/linux-image-4.4.0-1020-aws/filelist)
    There's no /lib/modules/4.4.0-1020-aws/kernel/drivers/net/can/ directory :-("*

Which makes sense, so I need to get the correct modules downloaded, but I don't know how to?

They said too:

    *"The usual way is to compile your own Kernel, which means to download the kernel sources from that 4.4.0-1020-aws Ubuntu Kernel and compile it on your own (with CONFIG_CAN_VCAN=m set in the kernel config)."*


Note - I am using AWS instance

Thank you

---

