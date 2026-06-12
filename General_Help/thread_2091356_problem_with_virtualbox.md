---
title: "problem with virtualbox"
date: 2012-12-04
forum: General Help
---

### Post by hunterkasy on 2012-12-04
what I am wanting to do is use a usb printer on a win 7 running on the virtualbox.

I am running ubuntu 12.10 and running virtualbox 4.2.4 r81684

Failed to access the usb subsystem

virtualbox is not currently allowed to access usb devices.  you can change this by adding your user to the 'vboxusers' group.  


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {30678943-32df-4830-b413-931b25ac86a0}
Callee: 
IMachine {22781af3-1c96-4126-9edf-67a020e0e858}

---

### Post by papibe on 2012-12-04
Hi hunterkasy.

Have you take a look at [this]("https://help.ubuntu.com/community/VirtualBox/USB")?

Let us know how it goes.
Regards.

---

### Post by hunterkasy on 2012-12-05
> **papibe said:**
> Hi hunterkasy.

Have you take a look at [this]("https://help.ubuntu.com/community/VirtualBox/USB")?

Let us know how it goes.
Regards.

it only goes up to 11.10

For Oneiric Ocelot 11.10

Add yourself to the user group vboxusers, then log out and back in, to make use of available USB devices. To do this via the graphical interface, click System Settings/Users and Groups/Manage Groups. 

12.10 don't have users and groups only user account

---

### Post by BertN45 on 2012-12-05
Yes they have a simplified version in 12.10, but you can download the "Users and Groups" version from the Software Center.

---

### Post by papibe on 2012-12-05
You can do it on the command line:
```
sudo usermod -aG vboxusers youruser
```
(replace 'youruser' for your actual user name).

Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2012-12-05
Another option is to share the printer in Windows then connect to it from the guest over the "network" set up between the guest and host.  In the Ubuntu guest, point a browser to [http://localhost:631/](http://localhost:631/) and follow the instructions for an SMB printer.  Use the internal IP address to which the guest connects.  If you don't know what that address is, enter the command "route -n" and see what the address of the gateway is that handles traffic for the 0.0.0.0 destination.  I think the default is 10.0.2.2.

---

### Post by hunterkasy on 2012-12-07
> **BertN45 said:**
> Yes they have a simplified version in 12.10, but you can download the "Users and Groups" version from the Software Center.

thanks it works now,

---

