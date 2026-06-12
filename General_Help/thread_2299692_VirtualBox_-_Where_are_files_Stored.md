---
title: "VirtualBox - Where are files Stored"
date: 2015-10-20
forum: General Help
---

### Post by niceguy123 on 2015-10-20
Hi,

I am running windows vista on VirturalBox under Ubuntu 14.04 for a program that I need that does not work on linux. 

My question is: Is there a place in my file system in Ubuntu where I can see and manage documents or other files that have been saved on C: under windows. 

Or what would be the simplest procedure to transfer files from ubuntu to windows that is running on the same computer under virtualBox?

Thanks

---

### Post by v3.xx on 2015-10-20
shared folder?

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by JKyleOKC on 2015-10-20
> **niceguy123 said:**
> My question is: Is there a place in my file system in Ubuntu where I can see and manage documents or other files that have been saved on C: under windows. 

Or what would be the simplest procedure to transfer files from ubuntu to windows that is running on the same computer under virtualBox?

ThanksAs v3.xx suggests, using the "shared folders" capability of VBox is the simplest way to go. First, create the desired folder in your home directory under ubuntu. Then go to the Windows VM, be sure you have the Guest Additions installed in it, then select "shared folders" from the "Devices" pulldown of the VBox menu (not the Windows one). Using it, enable the shared folder. It should then appear in Windows as a new separate drive. This will allow you to read and write anything in the shared folder just as if it were a Windows drive.

Unfortunately it doesn't work both ways. Anything that you copy into the shared folder, from Windows, will be available to Ubuntu, but none of the other data on the C: drive will be accessible. While it's possible to use Samba to make it so, I've found that the simplest solution is to simply copy anything that I need to see in Ubuntu over into the shared folder using Windows, then do my work in Ubuntu.

---

### Post by SeijiSensei on 2015-10-20
You can define an entire Windows drive as a "shared folder" in VirtualBox.  I have a machine with a Kubuntu 14.04 guest and a Win7 host.  I shared my entire G:\ drive containing video and audio files and can navigate through all the folders from the VM.

Having a server at home, I often move files from one OS to the other by copying them from Windows to my Samba-exported home directory on the server and retrieving them from the same directory exported with NFS in Linux.  Or vice versa.  In general, I keep all my documents on the server making it easy to use either the virtual machine or the host system.

---

