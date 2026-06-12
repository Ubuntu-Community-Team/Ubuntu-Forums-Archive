---
title: "Nvidia Driver"
date: 2022-06-22
forum: General Help
---

### Post by outlaw67 on 2022-06-22
Using Ubuntu 22.04 server.Have Nvidia driver 510 installed but there is 515 avaialble.Don't see a 515 server driver version ? Thanks

---

### Post by mIk3_08 on 2022-06-22
> **outlaw67 said:**
> Using Ubuntu 22.04 server.Have Nvidia driver 510 installed but there is 515 avaialble.Don't see a 515 server driver version ? Thanks
Is that the only driver you see in the Additional Drivers under Software & Updates? Regards and cheers.

---

### Post by outlaw67 on 2022-06-22
Running Ubuntu 22.04 embedded server don't have [COLOR=#000000]Additional Drivers under Software & Updates.[/COLOR]

---

### Post by grahammechanical on 2022-06-22
Try running this command:

```
ubuntu-drivers list
```

On a desktop install with an Nvidia adapter that command will list available Nvidia drivers.

If the 515 driver is not available, then keep in mind that these are proprietary software and there is not much that Ubuntu developers can do about them. The driver may be too new for the developers to make available in Ubuntu. This would be especially true for Long Term Support versions.

If the 515 driver is listed then this command should install it.

```
ubuntu-drivers autoinstall
```

Regards

---

### Post by outlaw67 on 2022-06-22
Have done that but it only shows a 515 driver not 515 server driver.

---

### Post by ActionParsnip on 2022-06-22
Did you install a desktop environment on the server or is it command line only?

---

### Post by grahammechanical on 2022-06-22
> Have done that but it only shows a 515 driver not 515 server driver.

Now, I find myself having insufficient education. Why would there be a difference?

[https://askubuntu.com/questions/1262401/what-is-the-nvidia-server-driver](https://askubuntu.com/questions/1262401/what-is-the-nvidia-server-driver)

Learning every day.

> Using apt-file list on the two packages, the files are identical -

> They're both [metapackages]("https://help.ubuntu.com/community/MetaPackages"),  so presumably the important differences are in what packages they pull  in as dependencies, not what files they directly provide.

> The nvidia-driver-440 meta package includes i386 libraries whereas the nvidia-driver-440-server meta package does not. These are required for running Steam.

Regards

---

### Post by outlaw67 on 2022-06-22
Command line only

---

### Post by ActionParsnip on 2022-06-22
Then why are you installing the Nvidia driver if it is pure command line?

---

### Post by outlaw67 on 2022-06-22
This PC is used as a music server and uses Cuda off load.

---

### Post by mIk3_08 on 2022-06-23
> **outlaw67 said:**
> Running Ubuntu 22.04 embedded server don't have [COLOR=#000000]Additional Drivers under Software & Updates.[/COLOR]
Linux Ubuntu Server release is best for CLI and if you want to use GUI use the  Linux Ubuntu Desktop release. Regards and cheers

---

