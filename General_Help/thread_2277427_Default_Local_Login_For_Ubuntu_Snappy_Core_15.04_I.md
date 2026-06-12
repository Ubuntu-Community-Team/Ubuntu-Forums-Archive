---
title: "Default Local Login For Ubuntu Snappy Core 15.04 Image"
date: 2015-05-08
forum: General Help
---

### Post by digiPixel on 2015-05-08
Downloaded the [Ubuntu Snappy Core 15.04 image]("http://cloud-images.ubuntu.com/ubuntu-core/15.04/core/stable/current/core-stable-amd64-cloud.ova") (OVA file) for Virtual Box, and have imported it into Virtual Box successfully. Started up the Snappy Core virtual machine without any major issues apart from the systemd random seed holdup (delay of around 30 sec). Have a local login screen that is currently being displayed. Tried various login combinations but none of them work.

What is the default local login details for the Ubuntu Snappy Core 15.04 image? Been [looking]("http://askubuntu.com/questions/620996/how-to-install-snappy-ubuntu-15-04-core-images-on-a-pc") everywhere for a valid one but to no avail.

---

### Post by digiPixel on 2015-05-08
Had a look at the [Get Started]("http://developer.ubuntu.com/en/snappy/start/") page for Ubuntu Snappy Core and found out that some files have to be created first. Also the created ISO has to be attached to the virtual machine before startup. Unfortunately after doing all the steps on the page the Cloud-init system fails to detect the cdrom (ISO file), therefore the default account isn't created.

Without a default account there is no way to log into the virtual machine locally. Why hasn't Canonical setup a default user account for the Ubuntu Snappy Core 15.04 VM appliance?

---

### Post by grahammechanical on 2015-05-08
> After importing the OVA image using a VMware, Citrix or Virtualbox  platform, attach the VMDK or ISO image. Cloud-init will find the CDROM  and read the values. At that point you can login as "ubuntu" with the  password you have set.

Regards.

---

### Post by digiPixel on 2015-05-09
> After importing the OVA image using a VMware, Citrix or Virtualbox platform, attach the VMDK or ISO image

ISO image was attached before starting the Ubuntu Snappy Core virtual machine.

---

### Post by digiPixel on 2015-05-09
Does Cloud-init require an Internet connection in order to create a default user account?

---

### Post by digiPixel on 2015-05-09
Appears as though Cloud-init requires an Internet connection in order to work properly. Very disappointed that Canonical haven't designed the system to detect a malformed/non-existent ISO and display helpful error messages in the virtual machine, which would greatly help with quickly resolving issues around the default user account not being created as expected.
 
Seems as though some ports need to be opened in the Firewall in order for Cloud-init to function properly. There is nothing in the Ubuntu Snappy Core documentation about this. Also there is nothing in the documentation on resolving common Cloud-init issues. Have managed to finally get a default user account created for the virtual machine, however the system that Canonical have used requires a lot of work in order to make it very easy to use. As it stands the system can be very frustrating to deal with when it malfunctions.

Still don't understand why Canonical have imposed the Cloud-init system on the virtual machine method, yet the other methods already come with a default user account already created.

---

