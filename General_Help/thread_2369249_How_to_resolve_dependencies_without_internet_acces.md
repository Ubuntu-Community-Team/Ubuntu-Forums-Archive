---
title: "How to resolve dependencies without internet access"
date: 2017-08-20
forum: General Help
---

### Post by daryl9 on 2017-08-20
I'm trying to install print drivers on Edubuntu 14.0.3.   I don't have internet access to resolve dependencies, but I do have source media.  

The install fails with a dependency of "lsb".  I see a lsb-base and lsb-core installed, but apparently those are not what dpkg is looking for. 

Any suggestion on how to resolve the lsb dependency? 

Thanks.

Daryl

---

### Post by superiorsam on 2017-08-21
hi Daryl9

It is actually tough to solve the issue without internet.
But if you have the same setup running fine in other machine, you could connect/establish local network and download the repo and dependencies installed to other machine.
For that there are few configuration you need to do for the repo to update locally from other machine.

As I said it tough to do but achievable without internet.

Thanks
Sam

---

### Post by daryl9 on 2017-08-21
> **superiorsam said:**
> hi Daryl9

It is actually tough to solve the issue without internet.
But if you have the same setup running fine in other machine, you could connect/establish local network and download the repo and dependencies installed to other machine.
For that there are few configuration you need to do for the repo to update locally from other machine.

As I said it tough to do but achievable without internet.

Thanks
Sam

Hello Sam.

I'll take a look at doing that.

Thanks

Daryl

---

### Post by again? on 2017-08-21
From a machine with internet access you can search and download deb packages from [https://packages.ubuntu.com/](https://packages.ubuntu.com/) to a usbdrive.
lsb download for trusty-----> [https://packages.ubuntu.com/trusty/lsb](https://packages.ubuntu.com/trusty/lsb)
But you will most likely need to follow a trail of dependencies.
Do you have a live usb of Edubuntu/Ubuntu 14.0.3?

If so you can boot to that usb on a machine that has internet access and download the package and dependencies.
Enable universe repo.
```
sudo add-apt-repository universe
sudo apt update
```

Download package files only(-d)
```
sudo apt install -d lsb
```

Copy the downloaded files to another usb stick.
```
cp /var/cache/apt/archives/*deb /path/to/usbdrive
```

Connect the usbdrive to your offline machine and run.
(All you need here is the directory where downloaded debs are.
-R will recursively handle all regular files matching pattern *.deb found at specified directory)
```
sudo dpkg -iR /path/to/usbdrive
```

---

### Post by daryl9 on 2017-08-22
> **guber2 said:**
> From a machine with internet access you can search and download deb packages from [https://packages.ubuntu.com/](https://packages.ubuntu.com/) to a usbdrive.
lsb download for trusty-----> [https://packages.ubuntu.com/trusty/lsb](https://packages.ubuntu.com/trusty/lsb)
But you will most likely need to follow a trail of dependencies.
Do you have a live usb of Edubuntu/Ubuntu 14.0.3?

If so you can boot to that usb on a machine that has internet access and download the package and dependencies.
Enable universe repo.
```
sudo add-apt-repository universe
sudo apt update
```

Download package files only(-d)
```
sudo apt install -d lsb
```

Copy the downloaded files to another usb stick.
```
cp /var/cache/apt/archives/*deb /path/to/usbdrive
```

Connect the usbdrive to your offline machine and run.
(All you need here is the directory where downloaded debs are.
-R will recursively handle all regular files matching pattern *.deb found at specified directory)
```
sudo dpkg -iR /path/to/usbdrive
```

Thank you for these steps.  I think this will resolve my issue.

I've been thinking how to download all of the repository, put on an external usb drive that I can take with me.  This should do the trick.  That way, I have everything with me as needed.

Thank you for the suggestion.

Daryl

---

### Post by slickymaster on 2017-08-22
*Thread moved to **General Help**.*

---

