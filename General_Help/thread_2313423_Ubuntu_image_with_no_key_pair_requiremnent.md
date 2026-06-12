---
title: "Ubuntu image with no key pair requiremnent"
date: 2016-02-12
forum: General Help
---

### Post by mark267 on 2016-02-12
Does anyone know where I can find an Ubuntu image that does not require ssh key pair for initial login? Will be deploying as KVM VM that will not initially not have network access, only console access.

Thanks

---

### Post by ian-weisser on 2016-02-12
Any flavor of desktop image, Ubuntu Server image, and the minimal image.
download.ubuntu.com

---

### Post by ajgreeny on 2016-02-12
What makes you think you need an SSH key pair to login; have you already had a problem with a key pair being asked for, or is this just a pre-emptive enquiry?

---

### Post by QIII on 2016-02-12
Perhaps the question is:  Will you (or someone else) have physical access to the physical machine on which the Ubuntu virtual machine will be created?  If that is the case, then there is no need to access it remotely and no need to connect to it over ssh to do initial configuration.

My servers run headless and I access them over ssh now, but I initially installed and configured them with a monitor, mouse and keyboard that were removed when I was done.

---

