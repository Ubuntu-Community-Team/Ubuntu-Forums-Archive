---
title: "KVM install - Terminal problem"
date: 2023-07-31
forum: General Help
---

### Post by grey1beard on 2023-07-31
[ATTACH=CONFIG]292532[/ATTACH]
I'm following instruction using Terminal to install KVM.
As shown in the attachment, I'm told to copy and paste a config file(?) into it.
[ATTACH=CONFIG]292533[/ATTACH]
1. The text that appears in the first picture is not the same content as in the original instruction(2nd picture), and
2. How do I 'save ', as per instruction ? I'm not familiar with the layout of the 1st terminal window, and see no 'save' button !

MTIA for any help.
John

---

### Post by #&amp;thj^% on 2023-07-31
Can you post the link you are following please.
I think you are making this much harder than needed.
```
sudo apt install virt-manager
```
is a good beginning.
```
apt policy virt-manager
virt-manager:
  Installed: 1:4.1.0-2
  Candidate: 1:4.1.0-2
  Version table:
 *** 1:4.1.0-2 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu lunar/universe i386 Packages
        100 /var/lib/dpkg/status

```
here will be a GUI for qemu-kvm

---

### Post by grey1beard on 2023-07-31
[https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/) is a link to the page.

---

### Post by #&amp;thj^% on 2023-07-31
> **grey1beard said:**
> [https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/) is a link to the page.

Thank you sir, How about virt-manager it's much easier to follow.
```
/etc/netplan/01-netcfg.yaml                        
network:
    ethernets:
       eth0:
          dhcp4: false
          dhcp6: false
     bridges:
        br0:
           interfaces: [eth0]
           dhcp4: false
           addresses: [10.254.152.27/24]
           macaddress: 01:26:3b:4b:1d:43
           routes:
              - to: default
                via: 10.254.152.1
                metric: 100
           nameservers:
                addresses: [8.8.8.8]
           parameters:
               stp: false
          dhcp6: false

```

---

### Post by grey1beard on 2023-07-31
> How about virt-manager it's much easier to follow.
Thanks.
Do I need to delete anything that I have already tried, or can I go ahead, as if from scratch ?
John

---

### Post by #&amp;thj^% on 2023-07-31
No sir you should be good if all you have done now is what is said from the link.
I do recommend to be sure after virt-manager is installed is:
```
sudo systemctl enable libvirtd
```
+
```
sudo systemctl start libvirtd
```
+
```
sudo usermod -aG kvm $USER
```
+
```
sudo usermod -aG libvirt $USER
```
Now i always recommend a restart for fresh new session.
Now try to install your Guest. (keep in mind there is a very small learning curve here)

---

### Post by grey1beard on 2023-07-31
Many thanks. I'll start in a couple of hours, after I've eaten !

---

### Post by grey1beard on 2023-07-31
I now have a virtual Windows 10 set up, so many thanks. Only a few minor hiccups along the way, but I've got there !
Now to try and set up  the preferred software and hardware.

I need to install a usb printer/cutter to the guest. Could you suggest a link to the simplest method, please ?
If I then need to add software, is importing it from a thumb drive (which I already have) the same process ? 
John
EDIT success with getting files into KVM  :D

---

### Post by grey1beard on 2023-07-31
I have tried to connect my Gazelle cutter via usb to the virtual machine, but can't make any progress. 
I've got the cutter plugged into the same port that I used previously to get files onto the Windows desktop, and with the vm running, clicked on 'Add Hardware', then usb host device, but the cutter isn't showing.
I've tried both with the cutter powered up and off, but no sign of it.
What am I doing wrong ?

---

### Post by aljames2 on 2023-07-31
It sounds like you need to pass the USB device through to your VM by selecting it from within the vm.  While in your VM, do you see a USB icon when you hover over the top-middle edge of the screen.  Or, you may find it in a menu option.

---

### Post by grey1beard on 2023-07-31
Just found 'file' sharing in advanced network settings, so I may have stumbled onto some progress !
Fingers crossed.

---

### Post by MAFoElffen on 2023-08-01
No. Take a breath. LOL. Let me spin up a VM to take a screen shot...

In Settings > Select Add Hardware > Select USB Host Device > Select the specific device... Select Finish... See attached.

---

### Post by #&amp;thj^% on 2023-08-01
> **MAFoElffen said:**
> No. Take a breath. LOL. Let me spin up a VM to take a screen shot...

In Settings > Select Add Hardware > Select USB Host Device > Select the specific device... Select Finish... See attached.

Sorry late for the party, but MAFoElffen spells it out nicely.

---

### Post by grey1beard on 2023-08-01
Thanks both. It is now becoming a habit through repetition.
Just hope I can remember it tomorrow !

---

