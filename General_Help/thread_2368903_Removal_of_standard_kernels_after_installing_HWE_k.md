---
title: "Removal of standard kernels after installing HWE kernels?"
date: 2017-08-16
forum: General Help
---

### Post by blunden2 on 2017-08-16
A while back I installed the HWE kernels on a small home server running Ubuntu Server 16.04.3. The official guide said to install it using the following package.

```
sudo apt-get install --install-recommends linux-generic-hwe-16.04
```

Before rebooting I realized that it uses Secure Boot so I installed the package below too.

```
sudo apt-get install --install-recommends linux-signed-generic-hwe-16.04
```

As a result, I currently have the following kernels and headers etc. installed.

```
linux-image-4.8.0-58-generic          linux-image-extra-4.10.0-30-generic
linux-generic-hwe-16.04               linux-image-extra-4.10.0-32-generic
linux-headers-4.10.0-30               linux-image-extra-4.4.0-91-generic
linux-headers-4.10.0-30-generic       linux-image-extra-4.8.0-58-generic
linux-headers-4.10.0-32               linux-image-generic-hwe-16.04
linux-headers-4.10.0-32-generic
linux-headers-4.4.0-91                linux-signed-generic
linux-headers-4.4.0-91-generic        linux-signed-generic-hwe-16.04
linux-headers-4.8.0-58                linux-signed-image-4.10.0-30-generic
linux-headers-4.8.0-58-generic        linux-signed-image-4.10.0-32-generic
linux-headers-generic                 linux-signed-image-4.4.0-91-generic
linux-headers-generic-hwe-16.04       linux-signed-image-4.8.0-58-generic
linux-image-4.10.0-30-generic         linux-signed-image-generic
linux-image-4.10.0-32-generic         linux-signed-image-generic-hwe-16.04
linux-image-4.4.0-91-generic
```

I also get updates to the 4.4.x kernels which seems very unnecessary. Can I uninstall linux-signed-generic, linux-headers-generic and linux-generic-hwe-16.04 as well as any remaining 4.4.x kernels or will that cause issues?

---

### Post by deadflowr on 2017-08-16
> Can I uninstall linux-signed-generic, linux-headers-generic and linux-generic-hwe-16.04 as well as any remaining 4.4.x kernels or will that cause issues?
You can remove all but anything that says -hwe, as that should be obvious; it's the hwe kernel series and removing those will stop the kernel from getting updated.
Everything else is fair game to remove.
(and of course don't remove the running kernel)

---

### Post by blunden2 on 2017-08-16
> **deadflowr said:**
> You can remove all but anything that says -hwe, as that should be obvious; it's the hwe kernel series and removing those will stop the kernel from getting updated.
Everything else is fair game to remove.
(and of course don't remove the running kernel) Ok, thanks. That's what I hoped since the server has limited storage.

Do I still need the unsigned package linux-generic-hwe-16.04 when I have linux-signed-generic-hwe-16.04? The headers are naturally not signed. :)

---

### Post by deadflowr on 2017-08-16
> Do I still need the unsigned package linux-generic-hwe-16.04 when I have linux-signed-generic-hwe-16.04? The headers are naturally not signed. &#65532;
I don't think so.
The linux-generic and linux-signed-generic packages are independent of each other.
Meaning one is not dependent on the other.

---

### Post by blunden2 on 2017-08-16
> **deadflowr said:**
> I don't think so.
The linux-generic and linux-signed-generic packages are independent of each other.
Meaning one is not dependent on the other. Yes, that seems to be the case. I still have a few unsigned images but I'll leave those be and check if I get more unsigned updates the next time a new kernel drops. If not, I'll just remove them then. :)

---

